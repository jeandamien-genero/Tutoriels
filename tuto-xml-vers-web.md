# Tutoriel pour lxml & Flask

Contributeurs : [@Lucaterre](https://github.com/Lucaterre), [@jeandamien-genero](https://github.com/jeandamien-genero).

Ce tutoriel a pour but d'expliquer comment afficher le contenu d'un document XML dans une application Flask via la librairie lxml.

---

## Pré-requis

* Python 3.x

* Framework Flask (*from Flask import flask*)

* Package lxml (*from lxml import etree*)

---

## Étape 1 : XML

* Structurer un texte en un document XML ;

* La version XML doit être 1.0 ;

* Ne pas mettre de namespace dans l'élément racine XML.

---

## Étape 2 : XSL

* Les versions de l'XML et de l'XSL doivent être 1.0 ;

* Si le contenu final affiché dans le navigateur web doit varier (par ex. : afficher une seule section de l'XML) :

  1. Dans la feuille de transformation XSL, définir une variable via l'élément ```<xsl:param name="nom_paramètre"/>``` ;

  2. Cette variable peut ensuite être appelée sous la forme de son ```@name``` précédé par un ```$``` dans le XPath d'une template XSLT.

* Écrire les règles de transformation XSL.

*Exemple :*

```XSLT
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
    <xsl:output method="html" indent="yes"/>
    <xsl:param name="nom_variable_xslt"/>
    <xsl:template match="/" >
                <xsl:apply-templates select="//text/body/div[@n=$nom_variable_xslt]"/>
    </xsl:template>
    <!-- 
    	Templates XSL de votre transformation.
    -->
</xsl:stylesheet>
```

---

## Étape 3 : Python

*Modèle :*

```Python
@app.route("chemin_route/<int:paramètre_fonction>")
def nom_fonction(paramètre_fonction):
	source_doc = etree.parse("doc_xml")
	xslt_doc = etree.parse("doc_xslt")
	xslt_transformer = etree.XSLT(xslt_doc)
	output_doc = xslt_transformer(source_doc, nom_variable_xslt=str(paramètre_fonction))
	return render_template("document_html", template_flask1=output_doc, template_flask2=paramètre_fonction) # Le nombre de template n'est pas limité.
```

1. Définir un décorateur et une fonction ;

2. Parser le document XML et stocker ce parsage dans une variable ```source_doc``` ;

3. Parser le document XSL et stocker ce parsage dans une variable ```xslt_doc``` ;

4. Utiliser la méthode ```.XSLT()``` sur ```xslt_doc``` pour indiquer à lxml qu'il s'agit d'une feuille de transformation XSL. Le résultat est stocké dans la variable ```xslt_transformer```;

5. Appliquer la feuille de transformation ```xslt_transformer``` à ```source_doc```.

  - La variable définie dans le document XSLT doit être indiquée comme un paramètre de la variable ```xslt_transformer``` et correspondre au paramètre de la fonction Python. 

  - Le paramètre de la fonction Python doit obligatoirement être casté en ```str``` s'il s'agit d'un autre type.

6. Retourner la template via l'objet Flask ```render_template()```.

  - Définir le chemin vers le document html où le retour de la fonction Python sera affiché ;

  - Définir une template Flask qui contient le résultat de la transformation XSL, i. e. ```output_doc```.

  - D'autres templates peuvent être définies, suivant les besoins du rendu.

---

## Étape 4 : HTML

```HTML
{% extends "conteneur.html" %}
{% block corps %}
	<div>
		<h1>Texte n°{{template_flask2}}</h1>
		<div>
			{{template_flask1|safe}} <!-- Le mode "|safe" est obligatoire -->
		</div>
	</div>
	<!-- Code HTML -->
{% endblock %}
```

* Dans le fichier HTML, le résultat de la transformation XSL est affichée au sein d'une template entre deux accolades ```{{}}```

  * Il faut impérativement ajouter le mode ```|safe``` à la template pour que les éléments HTML soit interprétés par le navigateur.

---

## Documentation

* lxml : https://lxml.de/

* Flask : https://palletsprojects.com/p/flask/

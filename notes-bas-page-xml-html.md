# XSLT. Faire des notes de bas de page.

Rédaction : [@jeandamien-genero](https://github.com/jeandamien-genero).

Ce tutoriel a pour but d'expliquer comment intégrer les notes d'un document XML dans le contenu HTML d'une page web via une feuille de transformation XSL.

---

## I. Structure du XML

* Les exemples se basent sur un document XML où les notes se trouvent dans le ```<text>```.

* Une note se trouve toujours dans un élément ```<note>``` (possédant l'attribut ```@type``` s'il y a plusieurs niveaux de note) puis dans un élément ```<p>```. 

	Exemple : ```<note type="n1"><p>La note.</p></note>```

* À la fin, le but est d'avoir un document HTML où des chiffres ou lettres en exposant se trouvent dans le texte à l'emplacement de la note, et renvoient en-dessous le texte où se trouvent les notes elles-mêmes.

---

## II. Structure

* J'ai commencé par faire la structure de ma template : 

```HTML
<xsl:template match="/" > <!-- Je matche la racine -->
                <xsl:apply-templates select="//text/div"/> 
                <!--
                	Je fais un apply-templates pour mon texte (ci-dessus).
                	Je fais une div spéciale pour mes notes (ci-dessous).
                	NB : j'ai deux niveaux de notes (na et n1).
                	Pour chaque niveau, je fais un apply-templates.
                -->
                <div>
                    <div class="note-global">
                        <xsl:apply-templates select="///text/div//note[@type='na']/p"/>
                    </div>
                    <div class="note-global">
                        <xsl:apply-templates select="//text/div//note[@type='n1']/p"/>
                    </div>
                </div>
    </xsl:template>
```

---

## III. Faire le renvoi au sein du texte

```HTML
	<xsl:template match="note[@type='n1']">
        <xsl:element name="sup">
            <xsl:element name="a">
                <xsl:attribute name="href">
                    <xsl:text>#</xsl:text>
                    <xsl:number count="//text/div//note[@type='n1']" level="any" format="1"/>
                </xsl:attribute>
                <xsl:number count="//text/div//note[@type='n1']" level="any" format="1"/>
            </xsl:element>
        </xsl:element>
    </xsl:template>
```

1. Je matche mes notes n1 ;

2. Je crée un élément HTML ```<sup>``` pour faire l'exposant ;

3. À l'intérieur, je crée l'élément ```<a>``` et son attribut ```@href``` pour faire le lien. L'attribut doit contenir deux informations :

	* ```#``` afin de créer une référence à un ```@id``` (à mettre dans ```<xsl:text>```) ;

	* La fonction ```xsl:number``` pour que la note soit automatiquement numérotée et faire l'id.

---

## IV. Faire la note de bas de page

```HTML
    <xsl:template match="note[@type='n1']/p">
        <xsl:element name="p">
            <xsl:attribute name="id">
                <xsl:number count="//text/div//note[@type='n1']" level="any" format="1"/>
            </xsl:attribute>
            <xsl:number count="//text/div//note[@type='n1']" level="any" format="1"/>
            <xsl:text>. </xsl:text>
            <xsl:apply-templates/>
        </xsl:element>
    </xsl:template>
```

1. Je matche l'élément XML ```<p>```.

2. Je crée un élément HTML ```<p>``` et son attribut ```@id```.

3. L'attribut ```@id``` contient une fonction ```<xsl:number>``` afin de numéroter automatiquement la note ; l'attribut ```@count``` matche sur l'élément ```<note>``` et non pas sur le ```<p>``` pour que le numéro corresponde à celui du renvoi dans le texte.

4. Dans l'élément HTML ```<p>``` se trouve la même fonction ```<xsl:number>```, ainsi qu'un point et un ```<xsl:apply-templates/>``` afin que l'XSLT récupère le contenu de l'élément XML ```<p>```.

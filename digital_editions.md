---
title: "Introduction to </br> Digital Humanities"
subtitle: "(Digital Editions & TEI)"
author: Maciej Eder
date: 2025/10/23
format: 
  revealjs:
    katex: true
    theme: files/pp.scss
    logo: files/DigiTS-RGB-short-SMALL.svg
    css: files/big_logo_DigiTS.css
    self_contained: false
---


---

## from printed to digital editing

1. **Paleography & transcription**
2. **Critical edition** – collate variants, produce apparatus
3. **Digital transition** – scan → OCR → manual correction
4. **Encoding** – represent structure, content, and editorial data
5. **Publication** – web, API, data sets

---

## why TEI‑XML?

- **Standardised**: Widely used by the DH community.
- **Extensible**: Customisable with ODDs (Object Definition Documents).
- **Rich**: Supports full editorial apparatus, metadata, annotations.
- **Interoperable**: Converters to HTML, RDF, TEI Lite, etc.
- **Community**: Large network of editors, tools, and resources.



# markup


## data & formatting in the same file

```
.title
Example
.endtitle
Johann Sebastian
.bold
Bach
.endbold
was a
.italic
great
.enditalic
composer.
```

👇

What we expect to get:

👇

#### Example

Johann Sebastian **Bach** was a _great_ composer.



## html


``` 
<h1>Example</h1>
<p>Johann Sebastian <b>Bach</b> was a <i>great</i> composer.</p>
```

👇

``` html
<h1>Example</h1>
<p>Johann Sebastian <b>Bach</b> was a <i>great</i> composer.</p>
```


👇

#### Example

Johann Sebastian **Bach** was a _great_ composer.



## LaTeX

``` tex
\section{Example}

Johann Sebastian {\bf Bach} was a {\it great} composer.\par
```

👇

#### Example

Johann Sebastian **Bach** was a _great_ composer.


## Markdown

``` md
## Example

Johann Sebastian **Bach** was a _great_ composer.
```

👇

#### Example

Johann Sebastian **Bach** was a _great_ composer.



## rtf format

```
{\rtf1\ansi\deff3\adeflang1025
{\fonttbl{\f0\froman\fprq2\fcharset0 Times New Roman;}{\f1\froman\fprq2\fcharset2 Symbol;}{\f2\fswiss\fprq2\fcharset0 Arial;}{\f3\froman\fprq2\fcharset0 Liberation Serif{\*\falt Times New Roman};}{\f4\fswiss\fprq2\fcharset0 Liberation Sans{\*\falt Arial};}{\f5\fnil\fprq2\fcharset0 PingFang SC;}{\f6\fnil\fprq2\fcharset0 Arial Unicode MS;}{\f7\fswiss\fprq0\fcharset128 Arial Unicode MS;}}
{\colortbl;\red0\green0\blue0;\red0\green0\blue255;\red0\green255\blue255;\red0\green255\blue0;\red255\green0\blue255;\red255\green0\blue0;\red255\green255\blue0;\red255\green255\blue255;\red0\green0\blue128;\red0\green128\blue128;\red0\green128\blue0;\red128\green0\blue128;\red128\green0\blue0;\red128\green128\blue0;\red128\green128\blue128;\red192\green192\blue192;}
{\stylesheet{\s0\snext0\rtlch\af6\afs24\alang1081 \ltrch\lang1033\langfe2052\hich\af3\loch\widctlpar\hyphpar0\ltrpar\cf0\f3\fs24\lang1033\kerning1\dbch\af8\langfe2052 Normal;}
{\s15\sbasedon0\snext16\rtlch\af6\afs28 \ltrch\hich\af4\loch\sb240\sa120\keepn\f4\fs28\dbch\af5 Heading;}
{\s16\sbasedon0\snext16\loch\sl276\slmult1\sb0\sa140 Body Text;}
{\s17\sbasedon16\snext17\rtlch\af7 \ltrch List;}
{\s18\sbasedon0\snext18\rtlch\af7\afs24\ai \ltrch\loch\sb120\sa120\noline\fs24\i caption;}
{\s19\sbasedon0\snext19\rtlch\af7 \ltrch\loch\noline Index;}
}{\*\generator LibreOffice/25.2.5.2$MacOSX_AARCH64 LibreOffice_project/03d19516eb2e1dd5d4ccd751a0d6f35f35e08022}{\info{\creatim\yr2025\mo10\dy23\hr16\min56}{\revtim\yr2025\mo10\dy23\hr16\min56}{\printim\yr0\mo0\dy0\hr0\min0}}{\*\userprops}\deftab709
\hyphauto1\viewscale100\formshade\nobrkwrptbl\paperh16838\paperw11906\margl1134\margr1134\margt1134\margb1134\sectd\sbknone\sftnnar\saftnnrlc\sectunlocked1\pgwsxn11906\pghsxn16838\marglsxn1134\margrsxn1134\margtsxn1134\margbsxn1134\ftnbj\ftnstart1\ftnrstcont\ftnnar\fet\aftnrstcont\aftnstart1\aftnnrlc
{\*\ftnsep\chftnsep}\pgndec\pard\plain \s0\rtlch\af6\afs24\alang1081 \ltrch\lang1033\langfe2052\hich\af3\loch\widctlpar\hyphpar0\ltrpar\cf0\f3\fs24\lang1033\kerning1\dbch\af8\langfe2052\ql\ltrpar{\loch
Johann Sebastian }{\rtlch\ab \ltrch\loch\b\loch
Bach}{\loch
 was a }{\rtlch\ai \ltrch\loch\i\loch
great}{\loch
 composer.}
\par }
```


# from troff to xml



## troff -- the 1970s vibes

```
.SH "Example"
Johann Sebastian \fBBach\fP was a \fIgreat\fP composer.
.PP
```

then you would compile your source file:

```bash
# Compile to PDF
groff -mandoc -Tpdf example.troff > example.pdf
```


---



## TeX/LaTeX -- the 1980s vibes


``` tex
\section{Euclidean distance}

The Euclidean distance between any two texts represented by two points $A$ and $B$ 
in an $n$-dimensional space can be defined as:

$$ \delta_{AB} = \sqrt{ \sum_{i = 1}^{n} (A_i - B_i)^2 } $$

where $A$ and $B$ are the two documents to be compared, and $A_i$, $B_i$ are 
the scaled (z-scored) frequencies of the $i$-th word in the range of $n$ 
most frequent words.
```

#### Euclidean distance 

The Euclidean distance between any two texts represented by two points _A_ and _B_ in an _n_-dimensional space can be defined as:

$$ \delta_{AB} = \sqrt{ \sum_{i = 1}^{n} (A_i - B_i)^2 } $$

where _A_ and _B_ are the two documents to be compared, and $A_i,\, B_i$ are the scaled (z-scored) frequencies of the _i_-th word in the range of _n_ most frequent words.

---





## early Web -- the 1990s vibes

- **HTML** (HTML 2.0, 1995) – HyperText Markup Language.
- Purpose: *Presentational* – describe **how** content looks.
- Features: *tag soup* – browsers tolerated malformed markup.

an example, correctly marked-up:

``` html
<H1>Example</H1>
<P>Johann Sebastian <B>Bach</B> was a <I>great</I> composer.</P>
```
but this would work too:

``` html
<H1>Example</H2>
<P>Johann Sebastian <B>Bach was a <I>great</I> composer.</P>
```

> meant to be *browser‑friendly*, not *schema‑strict*.



---

## the XML revolution

- **XML (eXtensible Markup Language, 1998)** – designed for **data
interchange**.
- Goal: *self‑describing*, *machine‑readable* data.
- Rules:
  - **Well‑formed**: tags must be closed, nested properly.
  - **Validated**: must conform to an external **schema**.

> XML brought *structure* and *semantics* to markup.

---


## html vs. XML

What is the difference between the following _html_ code:

``` html
<h1>Example</h1>
<p>Johann Sebastian <b>Bach</b> was a <i>great</i> composer.</p>
```

and the _xml_ code here:

``` xml
<head>Example</head>
<sentence>Johann Sebastian <name>Bach</name> was a <emph>great</emph> composer.</sentence>
```
with an additional file in the _css_ language:

``` css
.reveal name {
  font-weight: bold;
}
.reveal emph {
  font-style: italic;
}
.reveal head {
  display: block;
  font-weight: bold;
  text-align: left;
  text-transform: uppercase;
  font-size: 0.4em;
}
```


# XML



## a simple XML file

``` txt
<?xml version="1.0" encoding="UTF-8"?><story title="The Old Willow" author="Jane Doe">
<chapter number="1" title="A Quiet Morning"><paragraph>The sun rose over the quiet 
valley, casting golden light on the ancient willow by the stream.</paragraph><paragraph>
The leaves rustled softly, as if whispering secrets to the wandering 
breeze.</paragraph></chapter><chapter number="2" title="The Mysterious Visitor"><paragraph>
Suddenly, a stranger appeared at the edge of the forest, his cloak billowing 
in the wind.</paragraph></chapter></story>
```


## indents help read the code

``` txt
<?xml version="1.0" encoding="UTF-8"?>
<story title="The Old Willow" author="Jane Doe">
  <!-- Narrative content -->
  <chapter number="1" title="A Quiet Morning">
    <paragraph>
      The sun rose over the quiet valley, casting golden light on the ancient willow by the stream.
    </paragraph>
    <paragraph>
      The leaves rustled softly, as if whispering secrets to the wandering breeze.
    </paragraph>
  </chapter>
  <chapter number="2" title="The Mysterious Visitor">
    <paragraph>
      Suddenly, a stranger appeared at the edge of the forest, his cloak billowing in the wind.
    </paragraph>
  </chapter>
</story>
```



## syntax highlighting is useful

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<story title="The Old Willow" author="Jane Doe">
  <!-- Narrative content -->
  <chapter number="1" title="A Quiet Morning">
    <paragraph>
      The sun rose over the quiet valley, casting golden light on the ancient willow by the stream.
    </paragraph>
    <paragraph>
      The leaves rustled softly, as if whispering secrets to the wandering breeze.
    </paragraph>
  </chapter>
  <chapter number="2" title="The Mysterious Visitor">
    <paragraph>
      Suddenly, a stranger appeared at the edge of the forest, his cloak billowing in the wind.
    </paragraph>
  </chapter>
</story>
```



## XML in a nutshel

- it is a formal description of a dataset
- ... which also means, it's a model
- essentially, it follows a tree-like structure
- or, a structure of recursive containers
  - the elements can contain other elements
  - the elements cannot overlap
- the file has to be **well-formed**
- the file has to pass **validation** (well, not really...)


##

![](https://tei-c.org/release/doc/tei-p5-doc/en/html/Images/xmlFlowChart.png)


## validation (optional yet useful)

If you want to validate against a schema, you could attach a DTD like this:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE story [
  <!ELEMENT story (chapter+)>
  <!ATTLIST story title CDATA #REQUIRED
                     author CDATA #REQUIRED>
  <!ELEMENT chapter (paragraph+)>
  <!ATTLIST chapter number CDATA #REQUIRED
                     title CDATA #REQUIRED>
  <!ELEMENT paragraph (#PCDATA)>
]>
<story title="The Old Willow" author="Jane Doe">
  ...
</story>
```

Now, a validator will check that:

- A `<story>` must contain one or more `<chapter>` elements.
- Each `<chapter>` must contain one or more `<paragraph>` elements.
- The required attributes are present.

---




## well‑formed vs. validated

| | **Well‑Formed** | **Valid** |
|---|---|---|
| **Definition** | Syntax rules of XML are met (e.g., `<tag></tag>`). | Document conforms to a *schema* (DTD, XSD, RNG). |
| **Requirement** | Mandatory for any XML processor. | Optional; adds confidence in data structure. |
| **Purpose** | Enables parsing. | Ensures data integrity, consistency. |
| **Common Errors** | Unclosed tags, wrong nesting. | Missing required elements, wrong data types. |



---

## validation schemas

| Schema Type | Purpose | Strengths | Limitations |
|-------------|---------|-----------|-------------|
| **DTD (Document Type Definition)** | Original XML schema language. | Simple; widely supported. | Limited data types; no namespaces. |
| **XSD (XML Schema Definition)** | Formal, XML‑based schema language. | Rich types, namespaces, constraints. | Verbose; learning curve. |
| **RelaxNG** | Alternative to XSD (compact or XML form). | Simpler syntax; expressive. | Less tooling in some environments. |


---

## Example: DTD

```dtd
<!-- book.dtd -->
<!ELEMENT book (title, author+, chapter+)>
<!ELEMENT title (#PCDATA)>
<!ELEMENT author (#PCDATA)>
<!ELEMENT chapter (title, p+)>
<!ELEMENT p (#PCDATA)>
```

## Example: XML Schema Definition


```xsd
<!-- book.xsd -->
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="book">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="title" type="xs:string"/>
        <xs:element name="author" type="xs:string" maxOccurs="unbounded"/>
        <xs:element name="chapter" maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="title" type="xs:string"/>
              <xs:element name="p" type="xs:string" maxOccurs="unbounded"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```


# Text Encoding Initiative (TEI)



## Text Encoding Initiative

- nonprofit organization of academic institutions, research projects, and individual scholars.
- develops the Guidelines -- an XML language specifically for Digital Humanities.
- infrastructure for developing machine-actionable cultural heritage texts.
- widely used by libraries, museums, publishers, and individual scholars to present texts for online research, teaching, and preservation.

> TEI is a subset of XML.

> TEI defines which XML tags should be used.




---

## TEI overview

``` xml
<TEI>
  <teiHeader> … </teiHeader>
  <text> … </text>
</TEI>
```

- **Header** – metadata about the text.
- **Body** – the encoded content.
- **Namespaces** – `<TEI>`, `<teiHeader>`, `<text>`.

---

## TEI structural elements

| Element | Purpose | Example |
|---------|---------|---------|
| `<text>` | Root of the body | `<text> … </text>` |
| `<body>` | Main content | `<body> … </body>` |
| `<div>` | Structural divisions (chapter, section) | `<div type="chapter" n="1"> … </div>` |
| `<head>` | Heading for a `<div>` | `<head>Chapter One</head>` |
| `<p>` | Paragraph | `<p> … </p>` |
| `<lg>` | Verse line group | `<lg> … </lg>` |
| `<sp>` | Speech | `<sp who="#speaker1"> … </sp>` |



---

## TEI editorial apparatus

| Element | Purpose | Example |
|---------|---------|-------------|
| `<app>` | Apparatus (list of variants) | `<app> … </app>` |
| `<lem>` | Lemma (preferred reading) | `<lem>…</lem>` |
| `<rdg>` | Variant reading | `<rdg wit="#w1">…</rdg>` |
| `<wit>` | Witness (edition source) | `<wit n="w1"/>` |
| `<supplied>` | Text supplied by editor | `<supplied reason="unknown"/>` |
| `<corr>` / `<sic>` | Correction / original error | `<corr>…</corr>` |



---

## a minimal TEI skeleton

```xml
<?xml version="1.0" encoding="UTF-8"?>
<TEI xmlns="http://www.tei-c.org/ns/1.0">
  <teiHeader>
    <fileDesc>
      <titleStmt>
        <title>Sample Text</title>
        <author>Anonymous</author>
      </titleStmt>
      <publicationStmt>
        <p>Produced for DH course</p>
      </publicationStmt>
      <sourceDesc>
        <p>Handwritten manuscript, 18th c.</p>
      </sourceDesc>
    </fileDesc>
  </teiHeader>
  <text>
    <body>
      <div type="chapter" n="1">
        <head>Chapter One</head>
        <p>First paragraph of the text.</p>
      </div>
    </body>
  </text>
</TEI>
```


---

## adding annotations

```xml
<p>In <hi rend="bold">Rome</hi> we found <supplied reason="missing"/>.</p>
```

- **`<hi rend="bold">`** – Highlighting (formatting).
- **`<supplied>`** – Editor supplied missing content.

> Annotations can be nested and may reference external resources.


---

## TEI metadata (teiHeader)

- **`<fileDesc>`** – Title, author, publication details.
- **`<encodingDesc>`** – Encoding practices, DTD/ODD.
- **`<profileDesc>`** – Text type, language, genre.
- **`<revisionDesc>`** – Version history.



---

## representing multiple witnesses

```xml
<app>
  <lem>Example</lem>
  <rdg wit="#w1">Exemple</rdg>
  <rdg wit="#w2">Exemple</rdg>
</app>
```

- Use **`<wit>`** elements in `<teiHeader>` to list witnesses.
- In `<app>` link variants via the `wit` attribute.


---

## typical encoding workflow

1. **Source acquisition** – Scan, photograph, OCR.
2. **Transcription** – Manual correction, proof‑reading.
3. **Encoding** – Apply TEI structure, annotate.
4. **Quality‑control** – XML validation (DTD/Schema).
5. **Version control** – Git, Subversion.
6. **Publication** – HTML, PDF, API.
7. **Archiving** – Deposit in institutional repository.



---

## common tools

| Tool | Purpose | Notes |
|------|---------|-------|
| **Oxygen XML Editor** | Full‑featured editor, schema support |
Commercial but free for students |
| **TEI Editor (XML-Editor)** | Lightweight TEI editor | Open source |
| **Emacs + RefTeX** | Advanced editing, macros | Requires learning curve
|
| **Brat** | Inline annotation viewer | Good for collaborative annotation
|
| **TAME (Text Annotation and Manipulation Engine)** | Batch processing |
Useful for large corpora |
| **TEI Lite** | Simplified profile for beginners | Focus on core elements
|


---


## Publishing Options

| Format | Tool | Pros | Cons |
|--------|------|------|------|
| **HTML** | `tei2html` (XSLT) | Interactive, browsable | Requires web
hosting |
| **PDF** | `tei2pdf` (XSLT) | Print‑ready, offline | Static, large |
| **EPUB** | `tei2epub` | E‑reader friendly | Limited interactivity |
| **API** | Custom Python/JavaScript | Programmatic access | Development
effort |
| **Data set** | CSV/JSON | Analysis ready | Loss of markup depth |





---

## Exercise 1 – Encode a Short Passage

1. Choose a 5‑sentence excerpt from a public‑domain text.
2. Create a TEI skeleton.
3. Mark up:
   - `<body>` → `<div>` → `<head>` → `<p>`
   - Add a **<hi>** for a proper noun.
4. Save as `ex1.xml` and validate.

---

## Exercise 2 – Add an Editorial Apparatus

Using the same passage:

1. Assume you have two witnesses: `w1` (original) and `w2` (variant).
2. Encode an `<app>` with `<lem>` (the base) and two `<rdg wit="…">`
elements.
3. Document the witness list in `<teiHeader>`.

> Submit your XML file for peer review.

---

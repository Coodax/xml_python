# XML_PYTHON

### Enlaces de interés a w3schools: 
- https://www.w3schools.com/xml/xml_tree.asp
- https://www.w3schools.com/xml/xml_parser.asp
- https://www.w3schools.com/xml/dom_intro.asp
- https://www.w3schools.com/xml/xpath_intro.asp
- https://www.w3schools.com/xml/xsl_intro.asp
  
![how-to-encode-strings-for-xml-with-python-heading-image--large](https://github.com/Coodax/xml_python/assets/160049365/8c256577-d83c-45fa-a8ab-ceefe0fa8e56)

El procesamiento de XML es una tarea común, ya sea para leer, escribir o manipular datos.
Pequeño resumen de lo aprendido hasta ahora:

## 1. Librerías para el manejo de XML en Python

Python ofrece varias bibliotecas para trabajar con XML:

- ***xml.etree.ElementTree:*** Esta es una biblioteca integrada en Python que proporciona una forma simple y eficiente de analizar y manipular XML.
  
- ***xml.dom:*** Proporciona una interfaz para el modelo de objetos de documento XML estándar (DOM).

- ***lxml:*** Esta es una biblioteca externa de Python que se basa en libxml2/libxslt.

## 2. Lectura de XML en Python

Para leer un documento XML en Python, se necesita cargar el archivo XML en una estructura de árbol. Se puede hacer usando *`xml.etree.ElementTree`*:

```ejemplo en python
import xml.etree.ElementTree as ET

tree = ET.parse('archivo.xml')
root = tree.getroot()
```

## 3. Escritura de XML en Python
Para escribir datos en un archivo XML desde Python, hay que crear una estructura de árbol utilizando las mismas clases y métodos que se ha utilizado para leer XML:

```ejemplo en python
import xml.etree.ElementTree as ET

root = ET.Element("raiz")
doc = ET.SubElement(root, "documento")
ET.SubElement(doc, "elemento", atributo="valor")
tree = ET.ElementTree(root)
tree.write("archivo.xml")
```
## 4. Manipulación de XML en Python
Una vez leído un documento XML en una estructura de árbol, se puede añadir, eliminar o modificar elementos y atributos:

```ejemplo en python
import xml.etree.ElementTree as ET

tree = ET.parse('archivo.xml')
root = tree.getroot()

# Añadir un nuevo elemento
nuevo_elemento = ET.Element("nuevo_elemento")
root.append(nuevo_elemento)

# Modificar un atributo
root.attrib["nuevo_atributo"] = "valor"

# Eliminar un elemento
for child in root.findall("elemento"):
    root.remove(child)

# Escribir el árbol modificado de nuevo en un archivo
tree.write("archivo_modificado.xml")
```

## 5. XPath en Python
Se puede utilizar XPath en Python para buscar elementos específicos en un árbol XML.

```ejemplo en python
from lxml import etree

tree = etree.parse('archivo.xml')
elementos = tree.xpath('//elemento[@atributo="valor"]')
for elemento in elementos:
    print(etree.tostring(elemento))
```

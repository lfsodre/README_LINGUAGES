<h3 style="font-size:50px; color: #EF5A6F" align="center"><b>XML TOOLS</h3>


Biblioteca Element.Tree
------------------------------------------------
```Python
import xml.etree.ElementTree as ET
```

O XML é formado por TAGs e Atributos:
------------------------------------------------
```Python
<TAG> ATRIBUTO </TAG>
```

Arquivo XML utilizado:
------------------------------------------------
```XML
<?xml version="1.0"?>
<data>
    <country name="Liechtenstein">
        <rank>1</rank>
        <year>2008</year>
        <gdppc>141100</gdppc>
        <neighbor name="Austria" direction="E"/>
        <neighbor name="Switzerland" direction="W"/>
    </country>
    <country name="Singapore">
        <rank>4</rank>
        <year>2011</year>
        <gdppc>59900</gdppc>
        <neighbor name="Malaysia" direction="N"/>
    </country>
    <country name="Panama">
        <rank>68</rank>
        <year>2011</year>
        <gdppc>13600</gdppc>
        <neighbor name="Costa Rica" direction="W"/>
        <neighbor name="Colombia" direction="E"/>
    </country>
</data>
```

Importar arquivo XML
------------------------------------------------
```Python
tree = ET.parse('caminho.xml')
root = tree.getroot()
```

Respectivos comandos do ROOT:
------------------------------------------------
```Python
>>> root.tag
... 'data'   
>>> root.attrib 
... { }
```
Para interagir com os FILHOS do ROOT:
------------------------------------------------
```Python
>>> for child in root:
...    print(child.tag, child.attrib)
country {'name': 'Liechtenstein'}
country {'name': 'Singapore'}
country {'name': 'Panama'}
```

Podemos acessar FILHOS ESPECÍFICOS:
------------------------------------------------
```Python
>>> root[0][1].text
'2008'
```

Juntando DADOS
------------------------------------------------
```Python
```

!
------------------------------------------------
```Python
```

!
------------------------------------------------
```Python
```
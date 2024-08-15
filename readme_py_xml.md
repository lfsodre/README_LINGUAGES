<h3 style="font-size:50px; color: #EF5A6F; margin:0px" align="center"><b>XML TOOLS</h3>
<h3 style="font-size:20px; color: #FFFFF; margin-bottom: 8px; margin-top:0px" align="center">ELEMENT TREE</h3>


```Python
import xml.etree.ElementTree as ET
```

<h3 style="font-size:20px; color: #FFFFF; margin:0px">O XML é formado por TAGs e Atributos:</h3>
<hr>

```Python
<TAG> ATRIBUTO </TAG>
```

<h3 style="font-size:20px; color: #FFFFF; margin:0px">Arquivo XML utilizado:</h3>
<hr>

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

<h3 style="font-size:20px; color: #FFFFF; margin:0px">Importar arquivo XML</h3>
<hr>

```Python
tree = ET.parse('caminho.xml')
root = tree.getroot()
```

<h3 style="font-size:20px; color: #FFFFF; margin:0px">Respectivos comandos do ROOT:</h3>
<hr>

```Python
>>> root.tag
'data'   
>>> root.attrib 
'{ }'
```

<h3 style="font-size:20px; color: #FFFFF; margin:0px">Para interagir com os filhos do ROOT:</h3>
<hr>

```Python
>>> for child in root:
        print(child.tag, child.attrib)
'country {name: Liechtenstein}'
'country {name: Singapore}'
'country {nam: Panama}'
```

<h3 style="font-size:20px; color: #FFFFF; margin:0px">Podemos acessar filhos específicos:</h3>
<hr>

```Python
>>> root[0][1].text
'2008'
```

<h3 style="font-size:20px; color: #FFFFF; margin:0px">Juntando dados</h3>
<hr>

```Python
>>> parser = ET.XMLPullParser(['start', 'end'])
        parser.feed('<mytag>sometext')
        list(parser.read_events())
        parser.feed(' more text</mytag>')
        for event, elem in parser.read_events():
            print(event)
            print('<',elem.tag,'>', elem.text)
'end'
'<mytag> sometext more text'
```

<h3 style="font-size:20px; color: #FFFFF; margin:0px">Interagindo com Sub-árvores</h3>
<hr>

```Python
for neighbor in root.iter('neighbor'):
        print(neighbor.attrib)
{'name': 'Austria'    , 'direction': 'E'}
{'name': 'Switzerland', 'direction': 'W'}
{'name': 'Malaysia'   , 'direction': 'N'}
{'name': 'Costa Rica' , 'direction': 'W'}
{'name': 'Colombia'   , 'direction': 'E'}
```

<h3 style="font-size:20px; color: #FFFFF; margin:0px">Encontrando Elementos Interessantes</h3>
<hr>

```Python
# Element.findall()-> Encontra elementos que são filhos do elemento atual.
# Element.find()   -> Encontra o primeiro filho com uma tag específica
# Element.text()   -> Acessa o conteúdo de texto do elemento.
# Element.get()    -> Acessa os atributos do elemento:
```

```Python
>>> for country in root.findall('country'):
        rank = country.find('rank').text
        year = country.find('year').text
        name = country.get('name')
        print(name, rank, year)
'Liechtenstein 1 2008'
'Singapore 4 2011'
'Panama 68 2011'
```

<h3 style="font-size:20px; color: #FFFFF; margin:0px">!!!</h3>
<hr>

```Python
```

<h3 style="font-size:20px; color: #FFFFF; margin:0px">!!!</h3>
<hr>

```Python
```
## XML
Wykorzystywanym przez nas standardem wymiany danych będzie XML (Extensible Markup Language) - język znaczników do reprezentowania różnych danych w ustrukturyzowany sposób. XML to format, który jest łatwy do odczytu zarówno przez maszyny jak i przez ludzi.
Przykładowy dokument XML:
```
<?xml version="1.0" encoding="UTF-8"?>
<gazeta>
    <artykul data=”2020-03-29”>
        <tytul>Koronawirus w Polsce</tytul>
        <tresc>Wicepremier Piotr Gliński zapowiada nowe   obostrzenia w walce z SARS-CoV-2</tresc>
        <autor>Jakub Zimny</autor> 
    </artykul> 
</gazeta>
```

Standard XML jest powszechnie używany, a swoje zastosowanie znajduje w wielu elementach systemów informatycznych - do komunikacji między serwisami, zapisywania plików konfiguracyjnych, generowania dokumentów do druku czy opisu widoków aplikacji.

## XML Schema
Do definiowania struktury dokumentów XML służy XML Schema Definition (skrót: XSD). Definiuje on elementy, atrybuty oraz typy danych. Przykładowy dokument XML Schema:
```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs = "http://www.w3.org/2001/XMLSchema">
    <xs:element name = "gazeta">
        <xs:complexType name=”artykul”>
            <xs:attribute name="data" type="xs:date"/>
            <xs:sequence>   
                <xs:element name="tytul" type="xs:string"/>
                <xs:element name="tresc" type="xs:string"/>
                <xs:element name="autor" type="xs:string"/>
            </xs:sequence>  
        </xs:complexType>
    </xs:element>
</xs:schema>
```

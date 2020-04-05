## XML
Wykorzystywanym przez nas standardem wymiany danych będzie XML (Extensible Markup Language) - język znaczników do reprezentowania różnych danych w ustrukturyzowany sposób. XML to format, który jest łatwy do odczytu zarówno przez maszyny jak i przez ludzi.
Przykładowy dokument XML, przesyłany podczas procesu logowania:
```
<?xml version="1.0" encoding="UTF-8"?>
<login>
  <email>azor@piesmail.com</email>
  <password>H@$lo1234</password>
</login>
```

Standard XML jest powszechnie używany, a swoje zastosowanie znajduje w wielu elementach systemów informatycznych - do komunikacji między serwisami, zapisywania plików konfiguracyjnych, generowania dokumentów do druku czy opisu widoków aplikacji.

## XML Schema
Do definiowania struktury dokumentów XML służy XML Schema Definition (skrót: XSD). Definiuje on elementy, atrybuty oraz typy danych. Przykładowy dokument XML Schema, który opisuje/waliduje powyższy XML używany podczas logowania:
```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
  <xs:element name="login">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="email"/>
        <xs:element ref="password"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="email" type="xs:string"/>
  <xs:element name="password" type="xs:string"/>
</xs:schema>
```

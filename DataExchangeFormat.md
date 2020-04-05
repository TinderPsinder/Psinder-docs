## Register
Endpoint reprezentujący realizacje procesu biznesowego "process-create-account". Proces wykonywany jest przez Gościa, którego celem jest założenie konta użytkownika oraz przejście do klasy aktora AKT_JAM.
### Request
Communication: **Client -> API Gateway -> Users service**
```
POST /api/register
```
Example:
```
<?xml version="1.0" encoding="UTF-8"?>
<register>
  <name>Azor</name>
  <email>azor@piesmail.com</email>
  <password>H@$lo1234</password>
</register>
```
XML Schema:
```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
  <xs:element name="register">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="name"/>
        <xs:element ref="email"/>
        <xs:element ref="password"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="name" type="xs:NCName"/>
  <xs:element name="email" type="xs:string"/>
  <xs:element name="password" type="xs:string"/>
</xs:schema>
```
### Response
```
200 OK
```
Example:
```
<?xml version="1.0" encoding="UTF-8"?>
<user>
  <id>5ABDED2B-F27B-4C5F-AE9A-C864D3E703CD</id>
  <name>Azor</name>
  <email>azor@piesmail.com</email>
  <photos>
    <photo><id>DED644F2-F20B-4938-994B-5AADD596CD90</id></photo>
    <photo><id>8367784C-503E-4D87-9A4D-6AE35C59AF25</id></photo>
  </photos>
  <chat_id>23722755-67BA-4FC5-A579-9425F03B0F67</chat_id>
  <bio>Goracy jamnik</bio>
</user>
```
XML Schema:
```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
  <xs:element name="user">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="id">
          <xs:sequence>
            <xs:element ref="name"/>
            <xs:element ref="email"/>
            <xs:element ref="photos"/>
            <xs:element ref="chat_id"/>
            <xs:element ref="bio"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>
  <xs:element name="name" type="xs:NCName"/>
  <xs:element name="email" type="xs:string"/>
  <xs:element name="photos">
    <xs:complexType>
      <xs:sequence>
        <xs:element maxOccurs="unbounded" ref="photo"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="photo" type="id"/>
  <xs:element name="chat_id" type="xs:string"/>
  <xs:element name="bio" type="xs:string"/>
  <xs:complexType name="id">
    <xs:sequence>
      <xs:element ref="id"/>
    </xs:sequence>
  </xs:complexType>
  <xs:element name="id" type="xs:string"/>
</xs:schema>

```

## Login
Endpoint reprezentujący realizacje drugiej części procesu biznesowego "process-create-account". Proces wykonywany jest przez Gościa, którego celem jest zalogowanie się oraz przejście do klasy aktora AKT_JAM.
### Request
Communication: **Client -> API Gateway -> Users service**
```
POST /api/login
```
Example:
```
<?xml version="1.0" encoding="UTF-8"?>
<login>
  <email>azor@piesmail.com</email>
  <password>H@$lo1234</password>
</login>
```
XML Schema:
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
### Response
```
200 OK
```
Example:
```
<?xml version="1.0" encoding="UTF-8"?>
<user>
  <id>5ABDED2B-F27B-4C5F-AE9A-C864D3E703CD</id>
  <name>Azor</name>
  <email>azor@piesmail.com</email>
  <photos>
    <photo><id>DED644F2-F20B-4938-994B-5AADD596CD90</id></photo>
    <photo><id>8367784C-503E-4D87-9A4D-6AE35C59AF25</id></photo>
  </photos>
  <chat_id>23722755-67BA-4FC5-A579-9425F03B0F67</chat_id>
  <bio>Goracy jamnik</bio>
</user>
```
XML Schema:
```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
  <xs:element name="user">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="id">
          <xs:sequence>
            <xs:element ref="name"/>
            <xs:element ref="email"/>
            <xs:element ref="photos"/>
            <xs:element ref="chat_id"/>
            <xs:element ref="bio"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>
  <xs:element name="name" type="xs:NCName"/>
  <xs:element name="email" type="xs:string"/>
  <xs:element name="photos">
    <xs:complexType>
      <xs:sequence>
        <xs:element maxOccurs="unbounded" ref="photo"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="photo" type="id"/>
  <xs:element name="chat_id" type="xs:string"/>
  <xs:element name="bio" type="xs:string"/>
  <xs:complexType name="id">
    <xs:sequence>
      <xs:element ref="id"/>
    </xs:sequence>
  </xs:complexType>
  <xs:element name="id" type="xs:string"/>
</xs:schema>
```

## Report user
Endpoint reprezentujący realizacje procesu biznesowego "process-report". Proces wykonywany jest przez aktora AKT_JAM, którego celem jest zgłoszenie konta użytkownika łamiącego regulamin serwisu.
### Request
Communication: **Client -> API Gateway -> Users service**
```
POST /api/report
```
Example:
```
<?xml version="1.0" encoding="UTF-8"?>
<report>
  <user><id>5ABDED2B-F27B-4C5F-AE9A-C864D3E703CD</id></user>
</report>
```
XML Schema:
```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
  <xs:element name="report">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="user"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="user">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="id"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="id" type="xs:string"/>
</xs:schema>
```
### Response
```
200 OK
```

## Dogs nearby
Endpoint reprezentujący część realizacji procesu biznesowego "process-match". Proces wykonywany jest przez aktora AKT_JAM, którego celem jest pobranie pobliskich użytkowników.
### Request
Communication: **(Client -> Geolocation service) -> API Gateway -> Cards service**
```
GET /api/dogs
```
### Response
```
200 OK
```
Example:
```
<?xml version="1.0" encoding="UTF-8"?>
<dogs>
  <user>
    <id>5ABDED2B-F27B-4C5F-AE9A-C864D3E703CD</id>
    <name>Azor</name>
    <photos>
      <photo><id>DED644F2-F20B-4938-994B-5AADD596CD90</id></photo>
      <photo><id>8367784C-503E-4D87-9A4D-6AE35C59AF25</id></photo>
    </photos>
    <chat_id>23722755-67BA-4FC5-A579-9425F03B0F67</chat_id>
    <bio>Goracy jamnik</bio>
  </user>
  <user>
    <id>5ABDED2B-F27B-4C5F-AE9A-C864D3E703CD</id>
    <name>Azor</name>
    <photos>
      <photo><id>DED644F2-F20B-4938-994B-5AADD596CD90</id></photo>
      <photo><id>8367784C-503E-4D87-9A4D-6AE35C59AF25</id></photo>
    </photos>
    <chat_id>23722755-67BA-4FC5-A579-9425F03B0F67</chat_id>
    <bio>Goracy jamnik</bio>
  </user>
</dogs>
```
XML Schema:
```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
  <xs:element name="dogs">
    <xs:complexType>
      <xs:sequence>
        <xs:element maxOccurs="unbounded" ref="user"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="user">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="id">
          <xs:sequence>
            <xs:element ref="name"/>
            <xs:element ref="photos"/>
            <xs:element ref="chat_id"/>
            <xs:element ref="bio"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>
  <xs:element name="name" type="xs:NCName"/>
  <xs:element name="photos">
    <xs:complexType>
      <xs:sequence>
        <xs:element maxOccurs="unbounded" ref="photo"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="photo" type="id"/>
  <xs:element name="chat_id" type="xs:string"/>
  <xs:element name="bio" type="xs:string"/>
  <xs:complexType name="id">
    <xs:sequence>
      <xs:element ref="id"/>
    </xs:sequence>
  </xs:complexType>
  <xs:element name="id" type="xs:string"/>
</xs:schema>
```

## Like/dislike dog
Endpoint reprezentujący część realizacji procesu biznesowego "process-match". Proces wykonywany jest przez aktora AKT_JAM, którego celem jest zmiana statusu polubienia innego użytkownika.
### Request
Communication: **Client -> API Gateway -> Cards service**
```
PATCH /api/dogs
```
Example:
```
<?xml version="1.0" encoding="UTF-8"?>
<dogs>
  <dog>
    <id>5ABDED2B-F27B-4C5F-AE9A-C864D3E703CD</id>
    <like>true</like>
  </dog>
</dogs>
```
XML Schema:
```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
  <xs:element name="dogs">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="dog"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="dog">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="id"/>
        <xs:element ref="like"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="id" type="xs:string"/>
  <xs:element name="like" type="xs:boolean"/>
</xs:schema>
```
### Response
```
200 OK
```

## Matches
Endpoint reprezentujący część realizacji procesu biznesowego "process-match". Proces wykonywany jest przez aktora AKT_JAM, którego celem jest sprawdzenie dopasowanych użytkowników.
### Request
Communication: **Client -> API Gateway -> Cards service**
```
GET /api/matches
```
### Response
```
200 OK
```
Example:
```
<?xml version="1.0" encoding="UTF-8"?>
<matches>
  <user>
    <id>5ABDED2B-F27B-4C5F-AE9A-C864D3E703CD</id>
    <name>Azor</name>
    <photos>
      <photo><id>DED644F2-F20B-4938-994B-5AADD596CD90</id></photo>
      <photo><id>8367784C-503E-4D87-9A4D-6AE35C59AF25</id></photo>
    </photos>
    <chat_id>23722755-67BA-4FC5-A579-9425F03B0F67</chat_id>
    <bio>Goracy jamnik</bio>
  </user>
</matches>
```
XML Schema:
```
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
  <xs:element name="matches">
    <xs:complexType>
      <xs:sequence>
        <xs:element ref="user"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="user">
    <xs:complexType>
      <xs:complexContent>
        <xs:extension base="id">
          <xs:sequence>
            <xs:element ref="name"/>
            <xs:element ref="photos"/>
            <xs:element ref="chat_id"/>
            <xs:element ref="bio"/>
          </xs:sequence>
        </xs:extension>
      </xs:complexContent>
    </xs:complexType>
  </xs:element>
  <xs:element name="name" type="xs:NCName"/>
  <xs:element name="photos">
    <xs:complexType>
      <xs:sequence>
        <xs:element maxOccurs="unbounded" ref="photo"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:element name="photo" type="id"/>
  <xs:element name="chat_id" type="xs:string"/>
  <xs:element name="bio" type="xs:string"/>
  <xs:complexType name="id">
    <xs:sequence>
      <xs:element ref="id"/>
    </xs:sequence>
  </xs:complexType>
  <xs:element name="id" type="xs:string"/>
</xs:schema>
```

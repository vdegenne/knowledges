# Jersey

Jersey est une librairie Java (plus sp�cifiquement une librairie Java EE) qui permet de construire des applications de type RESTful.


## @XmlRootElement

Les objets impliqu�s dans les transactions Jersey, et particuli�rement dans les manipulations d'objets Json, doivent avoir l'annotation @XmlRootElement. Cette annotation permet de traduire l'objet en structure XML interpr�table par les processus sous-jacents.

```java
import javax.xml.bind.annotation.XmlRootElement;

@XmlRootElement
class MyObject {
   ...
}
```
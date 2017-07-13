# Jersey

Jersey est une librairie Java (plus spécifiquement une librairie Java EE) qui permet de construire des applications de type RESTful.


## @XmlRootElement

Les objets impliqués dans les transactions Jersey, et particulièrement dans les manipulations d'objets Json, doivent avoir l'annotation @XmlRootElement. Cette annotation permet de traduire l'objet en structure XML interprétable par les processus sous-jacents.

```java
import javax.xml.bind.annotation.XmlRootElement;

@XmlRootElement
class MyObject {
   ...
}
```
# Dienstag 220531


## Spring Framework
- Java Framework oft in Verbindung mit Web-Anwendungen
- dient zur Vereinfachung und Strukturierung vieler Aufgaben im Bereich Web
- besonders dafür vorgesehen ist Spring-Web
- Spring bietet einen Initializer in welchem alle Teile des Frameworks definiert werden -> [hier](https://start.spring.io/)
- durch erstellen des Projektes über die Website kann ein bereits vollwertiges Mavenprojekt heruntergeladen werden
- dieses Projekt enthält ein spring package mit einer vordefinierten main Methode
- durch starten dieser Methode wird ein lokaler Server gestartet welcher in der Standarddefinition den Port 8080 verwendet
- zu errreichen also unter http://localhost:8080
```Java
@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }

}
```
- in diesem Package sollten auch alle anderen Spring relevanten Klassen erstellt werden
- Spring basiert auf Annotationen
- Spring Web bietet die Möglichkeit REST Prinzipien direkt einzubauen
- Die Annotation @RestController eröffnet hier einen Anwendungsbereich im Rahmen der REST Architektur
- @RequestMapping verweist auf den URL Zusatz unter welchem die folgende Klasse ausgeführt wird
- @GetMapping verweist auf Methoden des Typs GET
- wird also per Browser ein GET Request an den Server geschickt werden die @GetMapping Methoden ausgeführt
```Java
@RestController
@RequestMapping("students")
public class StudentController {

    @GetMapping
    public Student getStudent(){
        return new Student("Name");
    }
}
```
- die @Service Annotation bietet die Möglichkeit eine "Businesslogik" zu implementieren und später im RestController aufzurufen
- es ist auch möglich der @GetMapping Annotation eine path variable hinzuzufügen
- diese kann mit der Annotation @PathVariable in der Methode verwendet werden
```Java
@RestController
@RequestMapping("students")
public class StudentController {
    @GetMapping(path = "{id}")
    public Student getStudent(@PathVariable String id) {
        return service.getStudent(id);
    }
}
```
- ein GET request mit der URL http://localhost:8080/students/1234 wird also die getStudent Methode aufrufen und die id 1234 einfügen
- die Annotation @RequestParam kann in die Methode integiert werden
- in der URL wird der RequestParam nach einem ? angegeben
```Java
@RestController
@RequestMapping("students")
public class StudentController {
    @GetMapping
    public Student getStudent(@PathVariable String id) {
        return service.getStudent(id);
    }
}
```
- für die gleiche Funktionalität wie im Code darüber muss also ein GET request an folgende URL erfolgen
- http://localhost:8080/students?id=1234
- @PostMapping erstellt einen POST Endpunkt
- durch senden eines POST requests wird diese Methode ausgeführt (oft um Objekte oder Einträge hinzuzufügen)
- @RequestBody ermöglich in dem POST request ein Objekt im JSON Format mitzugeben, welche ausgelesen und in der Methode verwendet wird
```Java
@RestController
@RequestMapping("students")
public class StudentController {
    @PostMapping
    public Student addStudent(@RequestBody Student student) {
        return service.addStudent(student);
    }
}
```
- dem POST request kann hier ein Body mitgegeben werden 
- erwartet wird ein Objekt Student
- der Konstruktor des Objektes nimmt Beispielsweise einen Vor- und einen Nachnamen
- im Body kann nun ein JSON Objekt übergeben werden, welches die Parameter des Konstruktors aufgreift
- z.B.
    {
        "firstName": "Max",
        "lastName": "Mustermann"
    }
- @RequestBody erkennt diese Parameter und erstellt eine Objekt Student


## REST (Representational State Transfer)
- Paradigma der Softwareentwicklung insbesondere im Bereich Webservices
- Ziel von REST ist es einen Architekturstil zu schaffen, der den modernen Anforderungen des Web genügt
- gliedert sich in die Bereiche:
    - GET (Informationen abrufen) 
    - POST (Informationen hinzufügen)
    - PUT (Informationen verändern) 
    - DELETE (Informationen löschen)


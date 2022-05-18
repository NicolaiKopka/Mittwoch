# Mittwoch


## JUnit

- Framework für Unit Testing
- ermöglicht einfache Tests von Code
- integriert mit Maven
- dafür muss zunächst JUnit den Maven dependencies zugefügt werden (s. POM.xml)
- der src/Java Ordner im Projekt enthält nun den gesamten Code
- um für eine Klasse Unit Tests zu implementieren, zunächst mit dem Cursor in die Klasse gehen
- der Command Shift + command + T öffnet das Test hinzufügen Fenster in IntelliJ
- im folgenden Popup noch auf richtige JUnit Version prüfen, dann Ok
- im src/Test Ordner wird nun eine Test Klasse angelegt
- hier werden die Test Methoden implementiert
- eine Test Methode wird [auf diese Weise](https://fictional-eureka-49f222de.pages.github.io/week-1.html#72) angelegt
- übliche Vorgehnsweise für Tests:
    - ein Test wird implementiert
    - auf dieser Grundlage wird die Methode definiert
    - danach wird der Code refactored
    - dann beginnt mit dem nächsten Test der nächst Durchlauf
- Tests bilden vor allem auch die Funktionalität eines Programms ab
- so ist für andere auch ersichtlich wie genau eine Methode funktionieren soll

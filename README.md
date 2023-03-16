# scala-best-pratices
A collection of best pratices

Version: 0.1

Updated at: 2023-03-16

## Table of Contents
  - 1 . Scalafmt
    - 1.1 Definition
    - 1.2 Configuration
    - 1.3 Implementation on IntelliJ
  - 2 . Scalastyle
    - 2.1 Definition
    - 2.2 Configuration
    - 2.3 Implementation on Intellij
  - 4 . How to enabled or disabled rules
  - 5 . Languages Rules
    - 5.1. MUST NOT use "return"
    - 5.2. SHOULD use immutable data structures
    - 5.3. SHOULD NOT update a "var" using loops or conditions
    - 5.4. SHOULD NOT define useless traits
    - 5.5. MUST NOT use "var" inside a case class
    - 5.6. SHOULD NOT declare abstract "var" members
    - 5.7. MUST NOT throw exceptions for validations of user input or flow control
    - 5.8. MUST NOT catch Throwable
    - 5.9. MUST NOT use "null"
    - 5.10. MUST NOT use "Option.get"
    - 5.11. MUST NOT use Java's Date or Calendar, instead use java.time (JSR-310)
    - 5.12. SHOULD NOT use Any or AnyRef or isInstanceOf / asInstanceOf
    - 5.13. MUST serialize dates as either Unix Timestamp or ISO 8601
    - 5.14. MUST NOT use magic values
    - 5.15. SHOULD NOT use "var" as shared state
    - 5.16. Public functions SHOULD have an explicit return type
    - 5.17. SHOULD NOT define case classes nested in other classes
    - 5.18. MUST NOT include classes, traits and objects inside package objects
    - 5.19. SHOULD use head/tail and init/last decomposition only if they can be done in constant time and memory
    - 5.20. MUST NOT use Seq.head
    - 5.21. Case classes SHOULD be final
    - 5.22. SHOULD NOT use scala.App


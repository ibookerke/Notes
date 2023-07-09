There are 5 requirements that should be satisfied by any architecture:
1. Independent of Frameworks. The architecture does not depend on the existence of some library of feature laden software. This allows you to use such frameworks as tools, rather than having to cram your system into their limited constraints.
2. Testable. The business rules can be tested without the UI, Database, Web Server, or any other external element.
3. Independent of UI. The UI can change easily, without changing the rest of the system. A Web UI could be replaced with a console UI, for example, without changing the business rules.
4. Independent of Database. You can swap out Oracle or SQL Server, for Mongo, BigTable, CouchDB, or something else. Your business rules are not bound to the database.
5. Independent of any external agency. In fact your business rules simply don’t know anything at all about the outside world.

![[Pasted image 20230622120947.png]]

## Dependency Rule
The concentric circles represent different areas of software. In general, the further in you go, the higher level the software becomes. The outer circles are mechanisms. The inner circles are policies.

The overriding rule that makes this architecture work is _The Dependency Rule_. This rule says that _source code dependencies_ can only point _inwards_. Nothing in an inner circle can know anything at all about something in an outer circle. In particular, the name of something declared in an outer circle must not be mentioned by the code in the an inner circle. That includes, functions, classes. variables, or any other named software entity.

By the same token, data formats used in an outer circle should not be used by an inner circle, especially if those formats are generate by a framework in an outer circle. We don’t want anything in an outer circle to impact the inner circles.



- Насчет покупки фиатом надо уточнить, чтобы пользователь не ебался, с покупкой юсдт и толькьо потом покупка токена
- Сделать возможность сделать рефанд части своего стейка другим пользукам
- Возможность сделать так, чтобы деньги передавались какому-то сервису и крутились
- Уведомить юристов насчетных валютных рисков
- Сделать лимиты по срокам выкупки
- В случае окончания срока - устраивать голосовалку с предложением продления
- 17 июля 15:00-16:00 - презентация изменений


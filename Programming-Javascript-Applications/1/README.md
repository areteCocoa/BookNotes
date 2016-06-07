# Chapter 1: The JavaScript Revolution
Pages 1-

- Once thought of as a toy, it is now a full top-to-bottom language

## Advantages of JavaScript
### Performance
- Just-in-time compiling
- Most modern browsers compile JS down to the low level

### Objects
- Rich OO features
- Prototypal Inheritance Model
  - No classes, only objects that inherit from parent objects
    - Prototype Chain

### Syntax
- Familiar to most other languages
- JSON replaces XML

### First-Class Functions
- Everything (including functions) are objects

### Events
- All event driven programming

### Reusability
- Runs on both client and the server

### The Net Result
- Some of the greatest applications ever created

## Anatomy of a Typical Modern JavaScript App
### Infrastructure
- Back to front, infrastructure usually consists of
  - A data store
  - A VPN or firewall to protect the data from unauthorized access
  - A black box JSON RESTFul Web Service Layer
  - Various 3rd party APIs
  - An app server/content management system (CMS) to route requests and deliver
    pages to the client
  - A static content deliver network (CDN) for cached files (like images, JavaScript,
    CSS and client-side templates)
  - The client (browser)
- Data store is often Relational DBMS with a SQL API
  - NoSQL is on the rise
### JSON: Data Storage and Communication
- Names and string values must be enclosed in double quotes. Others appear as literals
- JSON records cannot contain circular references
- JSON cannot contain function

### NoSQL Data Stores
- Although SQL still popular, some NoSQL is rising

### RESTful JSON Web Services
- Representational State Transfer (REST): client-server communication architecture
  that separates concern between data resources and UI
- Implementations of REST are called RESTful
- Server manages data but does not implement the UI
  - Client implements UI
- Uses HTTP verbs
  - PUT if client can generate own safe ID
  - POST if it cannot, and it gets returned

[END CHAPTER]
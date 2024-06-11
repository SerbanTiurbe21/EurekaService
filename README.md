# Eureka Service

Eureka Server este un serviciu de descoperire a serviciilor dezvoltat și menținut de Netflix, fiind parte a proiectului Spring Cloud Netflix. Este utilizat în arhitecturile de microservicii pentru a facilita descoperirea și înregistrarea serviciilor.

## Descriere

În cadrul acestui sistem, Eureka Server este configurat să ruleze ca o aplicație Spring Boot, după cum indică adnotarea `@EnableEurekaServer` în clasa principală `EurekaApplication`. Aceasta înseamnă că aplicația va funcționa ca un server Eureka, permițând altor servicii să se înregistreze la acesta.

Fișierul `pom.xml` relevă utilizarea Spring Boot și Spring Cloud în proiect, cu dependența specifică `spring-cloud-starter-netflix-eureka-server` pentru activarea funcționalității serverului Eureka.

Configurația pentru serverul Eureka este definită în fișierul `application.yaml`. Aici, serverul este configurat să nu se înregistreze pe sine (register-with-eureka: false) și să nu încerce să preia registrul de la sine (fetch-registry: false). Aceste setări sunt tipice pentru un server Eureka care funcționează independent.

## Dockerfile

Proiectul include un Dockerfile pentru containerizarea și desfășurarea ușoară a serverului Eureka.

## Rularea Serverului Eureka cu Docker

Pentru a rula serverul Eureka într-un container Docker, trebuie să urmezi câțiva pași simpli care implică construirea unei imagini Docker și rularea acesteia.

### Construirea Imaginii Docker
 - Deschide un terminal și navighează în directorul sursă al proiectului Eureka Server unde se află `Dockerfile`.
 - Rulează următoarea comandă pentru a construi imaginea Docker pentru serviciul Eureka. Acest pas presupune crearea unei imagini Docker local, etichetată ca `eureka-service`:

   `docker build -t eureka-service .`

   Această comandă va căuta Dockerfile în directorul curent și va folosi instrucțiunile specificate pentru a construi o imagine Docker.

### Rularea Containerului Docker

După construirea imaginii, poți rula containerul folosind imaginea creată:
`docker run -p 8761:8761 eureka-service`

Această comandă va porni un container din imaginea eureka-service, mapând portul 8761 al containerului pe portul 8761 al mașinii tale locale. Asta înseamnă că poți accesa serverul Eureka navigând la http://localhost:8761 în browserul tău.

!Însă acest pas nu este necesar pentru că există un `Dockerfile` de unde se vor porni toate containerele.!

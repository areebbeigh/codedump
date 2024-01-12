# codedump

## Java

- [Tuning the Size of Your Thread Pool
](https://www.infoq.com/articles/Java-Thread-Pool-Performance-Tuning/)

## Spring Microservices

- [Spring Transactional Guide](https://www.marcobehler.com/guides/spring-transaction-management-transactional-in-depth)
- [A Use Case for Transactions: Outbox Pattern Strategies in Spring Cloud Stream Kafka Binder
](https://spring.io/blog/2023/10/24/a-use-case-for-transactions-adapting-to-transactional-outbox-pattern/) - 6 Articles


## Distributed Systems

- [Raft vs MongoDB Consensus](https://medium.com/geekculture/raft-consensus-algorithm-and-leader-election-in-mongodb-vs-coachroachdb-19b767c87f95)
- [Please stop calling databases CP or AP
](https://martin.kleppmann.com/2015/05/11/please-stop-calling-databases-cp-or-ap.html)

## Blockchain
- [Merkle Proofs](https://bitcoin.stackexchange.com/questions/69018/merkle-root-and-merkle-proofs)

## Software Architecture
- [Source Making](https://sourcemaking.com/)
- [Refactoring Guru](https://refactoring.guru/)
- [An easy way to learn design patterns in SWE](http://scientificprogrammer.net/2020/01/30/an-easy-way-to-learn-design-patterns-in-software-development/)

## DBMS
- [Things every developer absolutely, positively needs to know about database indexing - Kai Sassnowski
](https://youtu.be/HubezKbFL7E)
- [MySQL Cheatsheet](https://www.mysqltutorial.org/mysql-cheat-sheet.aspx)
- [Understand Group by in Django with SQL](https://hakibenita.com/django-group-by-sql#how-to-group-by)
- [Cardinality, range queries and indexing](https://stackoverflow.com/questions/50239658/higher-cardinality-column-first-in-an-index-when-involving-a-range)

## Concurrency
- [(Thesis) Events vs Threads](https://berb.github.io/diploma-thesis/original/043_threadsevents.html)
- [(Thesis) Web Technologies - concurrency, scalability...](https://berb.github.io/diploma-thesis/original/index.html#chapter/5)
- [How does non-blocking IO work under the hood?](https://medium.com/ing-blog/how-does-non-blocking-io-work-under-the-hood-6299d2953c74)
- [AsyncIO in Python: A complete walkthrough](https://realpython.com/async-io-python/#setting-up-your-environment)
- [Should you be using Web Workers? (hint: probably not)](https://medium.com/@david.gilbertson/should-you-should-be-using-web-workers-hint-probably-not-9b6d26dc8c6a)

## Networks
- [Erle Robotics: Python Networking Programming](https://erlerobotics.gitbooks.io/erle-robotics-python-gitbook-free/content/)

## REST
- [REST: I don't Think it Means What You Think it Does • Stefan Tilkov • GOTO 2014
](https://www.youtube.com/watch?v=pspy1H6A3FM)

## Unorganized
- [Devhints Cheatsheets - Bash, MySQL, Go, etc. ](https://devhints.io/)
- [Profiling React Components (Chrome)](https://calibreapp.com/blog/react-performance-profiling-optimization)
- [How to Fix Your Git Branches After a Rebase](https://www.viget.com/articles/how-to-fix-your-git-branches-after-a-rebase/)
- [How To Serve Django Applications with uWSGI and Nginx on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-serve-django-applications-with-uwsgi-and-nginx-on-ubuntu-16-04#install-and-configure-virtualenv-and-virtualenvwrapper)
- Testing SMTP servers with `swaks` example
  ```
  swaks --to areebbeigh@gmail.com \
    --from noreply@example.com \
    --server email-smtp.ap-east-1.amazonaws.com:587 \
    --auth LOGIN \
    --auth-password <password> \
    --auth-user <user> \
    -tls
  ```
- Rabbit MQ quick start
    ```
    docker run -p 15672:15672 -p 5672:5672 -d --hostname my-rabbit rabbitmq:3-management
    ```
- Postman pre-request django csrf scipt
  ```javascript
  pm.cookies.jar().get("localhost", "csrftoken", (error, val) => {
      console.log("upsert", val)
      console.log(pm.request.headers.upsert({
          key: "X-CSRFToken",
          value: val,
      }))
  })
  ```

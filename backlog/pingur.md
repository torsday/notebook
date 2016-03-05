# Pingur

---

## UML

<!--lint disable no-literal-urls-->

![Alt text](http://g.gravizo.com/g?
@startuml;
actor User;
participant "RedditUser" as RU;
participant "RedditPost" as RP;
participant "PostDownloader" as PD;
participant "LinkPurifier" as LP;
participant "WebScraper" as WS;
participant "NokoGiriDoc" as NGD;
participant "FileDownloader" as FD;
User -> RU: updateUserPosts;
activate RU;
PD -> LP: cleanLinks;
activate LP;
LP -> PD: arrOfCleanLinks;
deactivate LP;
PD -> WS: getFileUrls;
@enduml
)

<!--lint enable no-literal-urls-->

---

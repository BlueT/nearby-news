# nearby-news
Keyword Cloud for your current location. A simple API service telling you what's hot near you.

A prototype system. NCNU BigData lecture project.

## Data collecting:

1. Parse article from news site. Extract data.
2. Lookup it's location (x, y)
3. Import to DB (RethinkDB)
4. Build geospatial index (RethinkDB or Redis)

## User Stream:

1. Locate user (GPS, map center)
2. Get radius (map size)
3. Send location to server, get unsorted array of Entries { [Keywords], timestamp, source, etc}
4. Build and show Keyword Cloud on map.
5. Repeat.

## 權重計算
- 先生成一個middle object，它包含每個keyword的timestamp
- 再透過midlle object，把每個keyword的score算出來
- 演算法是原本討論好的 sum(1/timeDiff)
- 測資timestamp從2007/1/1 到 2017/1/1隨機抓
- 共有10000筆測資，每筆測資有20個keywords，執行時間約5秒(AMD X4 965 3.4G)

## Docs:
- Diags https://cacoo.com/diagrams/zFHADLJOpHNowcYL#65F5B
- Wireframe https://invis.io/VT9M4KO7R
- Slide https://docs.google.com/presentation/d/1Il1CRVJDEXHyQfRYY71MkgUOekWvhwQLN_WfsOYOKOk/edit?usp=sharing
- Sample data https://docs.google.com/spreadsheets/d/1xcu-0PaMgywk60JRi_6ES6v6BCxXzDrWxwyNP05OKIw/edit?usp=sharing


# Nearby News API Server

## Overview
Server template was generated by the [swagger-codegen](https://github.com/swagger-api/swagger-codegen) project.  By using the [OpenAPI-Spec](https://github.com/OAI/OpenAPI-Specification) from a remote server.

This server uses the [Connect](https://github.com/senchalabs/connect) middleware layer for Node.js.
This service uses [RethinkDB](https://www.rethinkdb.com/) Database.

### Running the server
To run the server, run:

```
npm start
```

To view the Swagger UI interface:

```
open http://localhost:8080/docs
```

This project leverages the mega-awesome [swagger-tools](https://github.com/apigee-127/swagger-tools) middleware which does most all the work.

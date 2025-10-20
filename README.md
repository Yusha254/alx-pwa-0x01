# alx-project-0x14 – MoviesDatabase API

This project uses the **MoviesDatabase API** to get data about movies, TV shows, and actors. It includes info like ratings, genres, cast, and release dates.

---

## 🧭 API Overview

The API gives access to over **9 million titles** and **11 million actors**.  
You can search, filter, and sort data by name, year, genre, popularity, or rating.

Main features:
- Search movies, series, and actors.
- Get full details for any IMDb ID.
- View top-rated or popular titles.
- Check ratings, awards, and related media.

---

## 🔢 Version
**1.0**

---

## 🔗 Main Endpoints

| Endpoint | Description |
|-----------|--------------|
| `/titles` | Get a list of movies or shows. |
| `/titles/{id}` | Get details for one movie. |
| `/titles/{id}/ratings` | Get rating and vote count. |
| `/titles/search/title/{title}` | Search by title name. |
| `/titles/x/upcoming` | Get upcoming releases. |
| `/actors/{id}` | Get actor details. |

---

## 🧠 Request and Response

### Example Request
```bash
GET https://moviesdatabase.p.rapidapi.com/titles?genre=Action&limit=3
```

### Example Response
```json
{
  "results": [
    {
      "id": "tt1234567",
      "titleText": { "text": "Action Movie" },
      "releaseDate": { "year": 2023 },
      "genres": { "genres": [{ "text": "Action" }] },
      "ratingsSummary": { "aggregateRating": 8.0 }
    }
  ]
}
```

## 🔐 Authentication
Use your RapidAPI key in request headers:

```http
X-RapidAPI-Key: YOUR_API_KEY
X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
```

## ⚠️ Error Handling

| Code | Meaning           | Fix                      |
| ---- | ----------------- | ------------------------ |
| 400  | Bad Request       | Check your parameters.   |
| 401  | Unauthorized      | Add or fix your API key. |
| 404  | Not Found         | Wrong ID or endpoint.    |
| 429  | Too Many Requests | Wait and retry later.    |

## 🚦 Limits & Best Practices
- Don’t exceed RapidAPI request limits.

- Use pagination (page, limit).

- Cache static data like genres.

- Only request what you need using info to save time.

## 🧩 Quick Example

```ts
const url = "https://moviesdatabase.p.rapidapi.com/titles?list=top_rated_250&limit=5";

fetch(url, {
  headers: {
    "X-RapidAPI-Key": process.env.RAPIDAPI_KEY!,
    "X-RapidAPI-Host": "moviesdatabase.p.rapidapi.com"
  }
})
  .then(res => res.json())
  .then(data => console.log(data.results))
  .catch(err => console.error(err));
```

## 📎 Docs
[MoviesDatabase on RapidAPI](https://rapidapi.com/SAdrian13/api/moviesdatabase)
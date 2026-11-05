# 🎬 One Movie (Vanilla JS Version)

**Live demo:** https://mamalgamerrtx.github.io/One-Movie-No-React/

One Movie is a simple movie browser where you can search for movies and TV series and sort the results. This is the **original version of the project**, built with plain HTML, CSS, and JavaScript — no frameworks, no build step, just one `index.js` file doing all the work.

> This version was later rebuilt as a React app, which also adds a details page for every movie.

---

## Features

- **Search movies and series** by title using the [OMDb API](https://www.omdbapi.com/)
- **Sort results** four ways:
  - Alphabetical: A to Z
  - Alphabetical: Z to A
  - Newest to Oldest
  - Oldest to Newest
- **Featured list on first load** — the home page shows a hand-picked list of titles stored in the code, so opening the site uses **zero API calls**
- **Loading spinner** while search results are being fetched
- **Fallback poster** when a movie has no image (or the image fails to load)
- **Friendly messages** for "No movies found" and network/API errors
- **Responsive layout** with a navigation bar and footer

---

## Built With

- HTML5
- CSS3
- JavaScript (ES6+) — `fetch`, `async/await`, template literals, array methods
- [OMDb API](https://www.omdbapi.com/) for movie data
- GitHub Pages for hosting

---

## How It Works

Everything lives in `index.js`:

| Part | What it does |
|---|---|
| `mockMovies` | An array of featured movie/series objects shown when the page first loads |
| `searchMovies(query)` | Calls the OMDb search endpoint (`?s=`) when the search form is submitted, shows a spinner, handles errors, then renders (and sorts, if a sort option is selected) the results |
| `renderMovies(movies)` | Builds a card for each movie (poster, title, year) and injects it into `#movieContainer` |
| `sortMovies(order)` | Copies the current list and sorts it by title or year, then re-renders |
| Event listeners | Search form `submit` → search; sort dropdown `change` → sort |

The app keeps the list currently on screen in a `currentMovies` variable, so sorting works the same on both the featured list and search results.

---

## Running Locally

No installs or build tools needed.

1. Clone the repo:
   ```bash
   git clone https://github.com/mamalgamerrtx/One-Movie-No-React.git
   cd One-Movie-No-React
   ```
2. Open `index.html` in your browser (or use the VS Code **Live Server** extension).

### API key

The app uses an OMDb API key stored at the top of `index.js`:

```js
const apiKey = "YOUR_OMDB_API_KEY";
```

You can get a free key at [omdbapi.com/apikey.aspx](https://www.omdbapi.com/apikey.aspx). Since this is a front-end-only project, the key is visible in the browser — fine for a free learning project, but don't use a paid or private key this way.

---

## Project Structure

```
One-Movie-No-React/
├── index.html     # Page layout: nav, search form, sort dropdown, movie grid, footer
├── style.css      # Styles
├── index.js       # All app logic
└── assets/        # Images (e.g. search.jpg)
```

---

## Known Limitations

- OMDb's search endpoint returns only basic info (title, year, poster), so **ratings aren't shown** on search results — that would need a separate lookup per movie by IMDb ID.
- Search results are limited to the **first page** (up to 10 results) from OMDb.
- No individual movie details page — this was added in the React version.

---

## What I Learned

- Fetching data from a REST API with `async/await` and handling loading and error states
- Rendering lists dynamically with `map()` and template literals
- Sorting arrays without mutating the original (`[...array].sort()`)
- Saving API quota by using local data for the initial page load
- Why a component-based framework like React becomes useful as a single JS file grows

---

## Author

**mamalgamerrtx** — [GitHub](https://github.com/mamalgamerrtx)

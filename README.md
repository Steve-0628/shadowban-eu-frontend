# Twitter Shadowban Tests

#### One-page web app, testing Twitter users for various shadowbans.

## NOTE

Shadowban.eu Frontend Forked. For [hmpf.club/shadowban](https://hmpf.club/shadowban) and [hisubway.online/shadowban](https://hisubway.online/shadowban).

Frontend (former TwitterShadowBanV2; history preserved):  
[shadowban-eu/shadowban-eu-frontend](https://github.com/shadowban-eu/shadowban-eu-frontend.git)

Backend:  
[shadowban-eu/shadowban-eu-backend](https://github.com/shadowban-eu/shadowban-eu-backend.git)

---

## Setup
Requires Volta installed; The version of node and npm are very old. It uses npm@5 and node@10. 

```bash
# Clone
git clone https://github.com/shadowban-eu/shadowban-eu-frontend.git && cd shadowban-eu-frontend

# Install
npm i

#Start development
npm start
# or npm run dev

# Build (to ./dist/)
npm run build
```

Some values, like the HTML base href, are hard-coded in `webpack.config.js`.

## Notes
#### Base href
The `<base href>` is set on build, depending on the `NODE_ENV`:

  - production: https://shadowban.eu/
  - development: http://127.0.0.1:9000/

The development value is taken from the `devServerConfig` object in `webpack.config.js`, including `basePath`.  
Be aware that setting `<base href>` to `http://127.0.0.1:9000/`, but then visiting the site via `http://localhost:9000/` will work at first, but the browser will deny setting the URL to http://localhost:9000/testedName, when running a test.
 
#### .api mocks
During development, /src/.api/ is included to have the webpack-dev-server serve API responses.

```
./src/.api/
├── deboost
├── ghost
├── invalid
├── notweets
├── protected
└── typeahead
```

All these files hold one response object in JSON notation.
These files are served, whenever you test their respective name.

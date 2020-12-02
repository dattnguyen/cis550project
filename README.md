# cis550project
Jeopardy!

- Install the "Basic package" and the "SDK package" here: https://www.oracle.com/database/technologies/instant-client/winx64-64-downloads.html

Backend:
- Under routes.js (server side), update the "oracledb.initOracleClient({ libDir: '/Users/datnguyen/Project550/instantclient_19_8'});" with the path to where the instant client package was saved
- npm install oracledb

Frontend:
- npm run serve -- --port 3000

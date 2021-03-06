# Install

```
npm i express-cron
```

# Use

```js
import express from 'express';
import expressCron from 'express-cron';

const app = express();
expressCron(app);

app.cron('* * * * *', () => {
    console.log('running every minute');
});
```

Only run cron jobs after app has started

```js
import express from 'express';
import expressCron from 'express-cron';

const app = express();
expressCron(app, 'runCronJobs');

app.cron('* * * * *', () => {
    console.log('running every minute');
});

app.listen(8080, () => {
    app.emit('runCronJobs');
});
```

# ToDo

automatically insert into dist/index.d.ts:

```
declare module 'express-serve-static-core' {
    export interface Application {
        cron: (schedule: string, fn: () => void) => void;
    }
}
```

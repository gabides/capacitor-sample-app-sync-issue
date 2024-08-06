## Created with Capacitor Create App

This app was created using [`@capacitor/create-app`](https://github.com/ionic-team/create-capacitor-app),
and comes with a very minimal shell for building an app.

### Running this example

To run the provided example, you can use `npm start` command.

```bash
npm start
```


### Reproducing the sync hook issue

```
npm i
npx cap sync
```

You will see in the logs that the `capacitor:sync:after` hook (`"echo 'capacitor:sync:after' && pwd"`) is executed several times, at the root of each capacitor plugin:
- `capacitor-sample-app-sync-issue/node_modules/@capacitor/camera/`
- `capacitor-sample-app-sync-issue/node_modules/@capacitor/splash-screen/`


then remove the nx.json file and run the sync again:

```
rm nx.json
npx cap sync
```

you will see in the logs that the sync is executed at the root of the repo (`capacitor-sample-app-sync-issue/`)

this behaviour seems related to the nx.json config, and is not reproducible with `@capacitor/cli` version 6.0.1
# mixcoffee

Dahsboard and API for our friendly neighborhood coffee fund.

## Install

```
npm Install
```

## Usage

- the app expects the environment variable **GOOGLE_SPREADSHEET_ID**, which should be the ID of publishd Spreadsheet
  - generate this id by going to **File** > **Publish to the web...**
  - the ID will be part of the URL shown:
  - https://docs.google.com/spreadsheets/d/**id-will-be-here**/pubhtml

```bash
# specify the env var at startup
GOOGLE_SPREADSHEEET_ID=my-spreadsheet-id npm start
```

## Google Spreadsheet format
The app expects these columns:

| Day       |	Contributor |	Amount  | Comment                                       | image                                    | Balance |
| --------- | ----------- | ------- | --------------------------------------------- | ---------------------------------------- | ------- |
| 1/4/2016  | Dan	        | $10.00  |					                                      |                                          |  $10.00 |
| 1/5/2016  | Steve	      | $10.00  |					                                      |                                          |  $20.00 |
| 1/5/2016	| COFFEE	    | -$17.50 |	Greenway Gedeb Chelbessa Yirgacheffe Ethiopia	|                                          |   $3.50 |
| 1/8/2016	| COFFEE	    | -$17.50	| Crema - Finca Dragon Red Honey Costa Rica   	|	http://example.com/some-coffee-image.jpg | -$14.00 |
| 1/8/2016  | Flet        | $10.00  |                                               |                                          |  -$4.00 |

- entries should be in chronological order with the most recent at the bottom
- Contributor names should be consistent so they can be rolled up
- to record new coffee, contributor should be COFFEE and amount should be a negative value
- the Balance value should be the total of all previous fields so the bottom row's balance reflects the current balance


## Deploying
We're using `now.sh` for deployment. The deploy script assumes there is a `now secret` called `@coffee-spreadsheet-url`.

Run these commands one time to setup the secret:
```bash
now secrets add coffee-spreadsheet-id "my-coffee-spreadsheet-id"
```

Now that the secret is set, we can run the `package.json` script to redeploy
```bash
npm run deploy
```

Once the deploy is done and looks good, update the `now alias` to update production:

```bash
now alias set https://mixcoffee-qwertyuiop.now.sh custom-url.com
```

## License

[ISC](LICENSE)

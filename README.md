# API BTCpool.kz
BTCpool.kz offers developers to use API (Application Programming Interface) - a web service for receiving data.
Developers can use the API in applications and send HTTP requests to the BTCpool server in accordance with the proposed description.
The response from the web request will contain data in JSON format.

****
## Methods API
* General statistics of the pool - without authorization
* Summary account data
* Income history
* Payment history
* List of workers
****

### Authorization
Each account or child account has its own `api key`, which can be found in your account, in the `Settings Center` section

Just send a request with the title `X-API-KEY: <your_api_key>`:
```
curl 'https://btcpool.kz/ru/api?v=1&currency=BTC&method=profit_history' \
-H 'X-API-KEY: 5f42fd-1119a9-011313-c043cd-bd6d52'
```
****
### `main_stat` General pool statistics
**GET**

`https://btcpool.kz/ru/api?v=1&method=main_stat`

**RESPONSE**
```
{"status":"OK","data":{"BTC":{"miners":"1853","fee":1,"poolHs":"109444141315644889","networkHs":"4.4014015804097E+20","networkDiff":"52391178981379","poolHs_string":"109.44 PH\/s","networkHs_string":"440.14 EH\/s","networkDiff_string":"52.39T"},"BCH":{"miners":"5","fee":1,"poolHs":"293906788182043","networkHs":"2.89E+18","networkDiff":"404189587524.26","poolHs_string":"293.91 TH\/s","networkHs_string":"2.89 EH\/s","networkDiff_string":"404.19G"},"LTC":{"miners":"5","fee":1,"poolHs":"2419498243","networkHs":"700700000000000","networkDiff":"26922009.073457","poolHs_string":"2.42 GH\/s","networkHs_string":"700.7 TH\/s","networkDiff_string":"26.92M"}}}
```
****
### `summary_data` Account summary information
**GET**

`https://btcpool.kz/ru/api?v=1&method=summary_data&currency=BTC`

**Required parameters:**

`currency=string` BTC, BCH, LTC

**RESPONSE**
```
{"status":"OK","data":{"active_workers":"0","unactive_workers":"0","hashrate_10min":"0","hashrate_1hour":"0","hashrate_24hour":"0","balance":"0.00015744"}}
```

****
### `profit_history` Income History
**GET**

`https://btcpool.kz/ru/api?v=1&method=profit_history&currency=BTC&from=2023-04-21&to=2023-05-02&limit=10&offset=5`

**Required parameters:**

`currency=string` BTC, BCH, LTC

**Optional parameters:** 

`from=date`

`to=date`

`offset=int`

`limit=int` 

**RESPONSE**
```
{"status":"OK","data":[{"hashrate":"293286989405200.68","pplns_profit":"0.00003050","pps_profit":"0.00073035","total_profit":"0.00076085","date":"2023-04-26"},{"hashrate":"291413747372693.43","pplns_profit":"0.00003200","pps_profit":"0.00072572","total_profit":"0.00075772","date":"2023-04-27"},{"hashrate":"241351761280465.71","pplns_profit":"0.00001091","pps_profit":"0.00060104","total_profit":"0.00061195","date":"2023-04-28"},{"hashrate":"291197102859368.68","pplns_profit":"0.00003456","pps_profit":"0.00072518","total_profit":"0.00075974","date":"2023-04-29"},{"hashrate":"291037470060076.75","pplns_profit":"0.00003347","pps_profit":"0.00072479","total_profit":"0.00075826","date":"2023-04-30"},{"hashrate":"290051167407308.81","pplns_profit":"0.00002535","pps_profit":"0.00072229","total_profit":"0.00074764","date":"2023-05-01"},{"hashrate":"168986792658595.09","pplns_profit":"0.00003837","pps_profit":"0.00042082","total_profit":"0.00045919","date":"2023-05-02"}],"count":7,"offset":5,"limit":10,"total":12}
```

****
### `payment_history` Withdrawal history
**GET**

`https://btcpool.kz/ru/api?v=1&method=payment_history&currency=BTC&from=2023-04-21&to=2023-05-02&limit=10&offset=5`

**Required parameters:**

`currency=string` BTC, BCH, LTC

**Optional parameters:** 

`from=date`

`to=date`

`offset=int`

`limit=int` 

**RESPONSE**
```
{"status":"OK","data":[{"amount":"0.00149377","address":"bc1qllf33yhp7m80sfm35fce0tagcckey7dljauwd5","tx":"7f37726aca676a11ae30277d1a12bfec761f3523dc64c151abe2ec7d410c36fb","created_time":"1683017935","payment_id":"38518124"},{"amount":"0.00137954","address":"bc1qllf33yhp7m80sfm35fce0tagcckey7dljauwd5","tx":"398e02bff83a6e71df32516ac584314fd234e00e479274df8d6b46265c93286d","created_time":"1682845283","payment_id":"38409239"}],"count":2,"offset":0,"limit":2,"total":11}
```
`created_time` возвращается в Unix Time Stamp

****

### `workers` List of workers
**GET**

`https://btcpool.kz/ru/api?v=1&method=workers&currency=BTC&limit=100`

**Required parameters:**

`currency=string` BTC, BCH, LTC

**Optional parameters:** 

`offset=int`

`limit=int` 

**RESPONSE**
```
{"status":"OK","data":[{"hashrate_10min":"0","hashrate_1hour":"0","hashrate_24hour":"0","last_active":"1681255059","reject_rate":"0.00000000","worker_id":"24032703","worker_name":"worker1","worker_status":"0"},{"hashrate_10min":"0","hashrate_1hour":"0","hashrate_24hour":"0","last_active":"1683024000","reject_rate":"0.00000000","worker_id":"23890575","worker_name":"6094","worker_status":"0"},{"hashrate_10min":"0","hashrate_1hour":"0","hashrate_24hour":"0","last_active":"1683024000","reject_rate":"0.00000000","worker_id":"23890172","worker_name":"897","worker_status":"0"},{"hashrate_10min":"0","hashrate_1hour":"0","hashrate_24hour":"0","last_active":"1683024000","reject_rate":"0.00000000","worker_id":"23890171","worker_name":"8d77","worker_status":"0"},{"hashrate_10min":"0","hashrate_1hour":"0","hashrate_24hour":"0","last_active":"1683024000","reject_rate":"0.00000000","worker_id":"23890170","worker_name":"1x5","worker_status":"0"},{"hashrate_10min":"0","hashrate_1hour":"0","hashrate_24hour":"0","last_active":"1683024000","reject_rate":"0.00000000","worker_id":"23890169","worker_name":"9be6","worker_status":"0"}],"count":6,"offset":0,"limit":100,"total":6}
```

`last_active` returns in Unix Time Stamp

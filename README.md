# Actor - Ryanair Scraper

## Ryanair scraper

Since Ryanair doesn't provide an good API, this actor should help you to retrieve data from it.

The Ryanair data scraper supports the following features:

-   Scrape round trip - you can scrape a complete round trip with departure and return dates.
-   Scrape one way trip - you can scrape an one way trip with just providing the departure date
-   Scrape with multiple people options - You can scrape Ryanair with Adults, Teens, Children and Infants options

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/ryanair-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing. Possible fields are:

- `mode`: (Required) (String) Mode for the actor. It can be either `ROUND` for Round trip or `ONEWAY` for One way trips.

- `origin`: (Required) (String) 3-letter destination airport code. Ex: VIE.

- `destination`: (Required) (String) Mode for the actor. It can be either `ROUND` for Round trip or `ONEWAY` for One way trips.

- `departureDate`: (Required) (String) Date for departure. Should be in the format of `YYYY-MM-DD`. Ex: 2021-02-21.

- `returnDate`: (Optional) (String) Date for return. It is required for Round trips. Should be in the format of `YYYY-MM-DD`. Ex: 2021-02-21.

- `adults`: (Required) (Number) Number of adults that will be included on the flight. Minimum number is 1.

- `teens`: (Optional) (Number) Number of teens (12-15 years old) that will be included on the flight.

- `children`: (Optional) (Number) Number of children (2-11 years old) that will be included on the flight.

- `infants`: (Optional) (Number) Number of teens (Under 2 years old) that will be included on the flight.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use <a href="https://www.apify.com/docs/proxy">Apify Proxy</a>.

### Compute Unit Consumption

The actor optimized to run in a very fast manner and scrape the flights in the most performant way. Therefore, it forefronts all flight result requests. If actor doesn't block very often it'll scrape 10 flights in 3 seconds with ~0.005-0.01 compute units.

### Ryanair Scraper Input example

```json
{
    "type": "ROUND",
    "origin": "VIE",
    "destination": "BCN",
    "departureTime": "2021-11-02",
    "returnTime": "2021-11-09",
    "adults": 4,
    "children": 3,
    "infants": 2,
    "teens": 1,
    "requestExtension": {
        "timeoutSecs": 100
    }
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on.
When items are loaded from the page, you should see a message about this event with a loaded item count.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Ryanair Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Ryanair actor.

## Scraped Ryanair Flights

The structure of each item in Ryanair flights looks like this:

```json
[
    {
        "Origin": "VIE",
        "Destination": "BCN",
        "Flight duration": "02:20",
        "Flight number": "FR 7350",
        "Price": 19.79,
        "Time departure": "2021-05-02T16:55:00.000",
        "Time arrival": "2021-05-02T19:15:00.000",
        "key": "FR~7350~ ~~VIE~05/02/2021 16:55~BCN~05/02/2021 19:15~~",
        "scrapedAt": "2021-03-16T14:56:12.589Z",
        "regularFare": {
            "fareKey": "M4QWIFT5CMI6W554NIEL57IV6W6IKYDXA4HYK5TOZ3XDXKE5ZIEA2SAQMZI2ZHAVJRZE6PNUMMZ7KMWOLDIQQQ2HHNXOWJLJHJDQHLHLCGLC7XXCR37MU4LSLJKSBC3IISWCP5UWXAKWP2URYKOW6SL6RD5PP5C6G2LVCIRMU52U5OPUZ566RWCNU6MZGWKZO3STLR4N5MEEY",
            "fareClass": "W",
            "fares": [
                {
                    "type": "ADT",
                    "amount": 19.79,
                    "count": 1,
                    "hasDiscount": true,
                    "publishedFare": 19.92,
                    "discountInPercent": 10,
                    "hasPromoDiscount": false,
                    "discountAmount": 0.13,
                    "hasBogof": false
                }
            ]
        },
        "operatedBy": "Buzz"
    },
    {
        "Origin": "BCN",
        "Destination": "VIE",
        "Flight duration": "02:20",
        "Flight number": "FR 7351",
        "Price": 14.44,
        "Time departure": "2021-05-07T19:25:00.000",
        "Time arrival": "2021-05-07T21:45:00.000",
        "key": "FR~7351~ ~~BCN~05/07/2021 19:25~VIE~05/07/2021 21:45~~",
        "scrapedAt": "2021-03-16T14:56:12.589Z",
        "regularFare": {
            "fareKey": "PAZI5RTI7Q6XPJWZ7NWTM2L6ST4EGT5VMEUFJ6XELKMBYO6E32W5J5N7O4Q5CLXR5CGRECNSKTZTI4RKRXUINENX2PFLTWHHXJLAH7T6GXNF4TXMHSLS4XQPUMFFXA2R4HAIMVIEEALOODFNPIWICPXWWWM4NH3WFFECKOB6BG3EM5EO2FZRAG5I74AY26PWUQSTRWRZSY3TS",
            "fareClass": "T",
            "fares": [
                {
                    "type": "ADT",
                    "amount": 14.44,
                    "count": 1,
                    "hasDiscount": true,
                    "publishedFare": 14.63,
                    "discountInPercent": 15,
                    "hasPromoDiscount": false,
                    "discountAmount": 0.19,
                    "hasBogof": false
                }
            ]
        },
        "operatedBy": "Lauda Europe"
    },
    {
        "Origin": "BCN",
        "Destination": "VIE",
        "Flight duration": "02:20",
        "Flight number": "FR 7351",
        "Price": 25.19,
        "Time departure": "2021-05-09T19:50:00.000",
        "Time arrival": "2021-05-09T22:10:00.000",
        "key": "FR~7351~ ~~BCN~05/09/2021 19:50~VIE~05/09/2021 22:10~~",
        "scrapedAt": "2021-03-16T14:56:12.589Z",
        "regularFare": {
            "fareKey": "5DK4JGBZGI3LGJEY7PIPEHFS6AQV5IRPZTGV23N5AMBWJS4ZR22QAPTVTCGN24WMRSPLJGWCHJGIFLZQRXINUUEMCZX4Z5UPWN3RSKZ3R24BNFBGZIKWCFZWXI7IFPO3QDXJPS65E5E4I73IQHMLKGVT7PQ76AJUUPEK33SNLF5NNIMK3M5QCPFUJN3XP6KYFPJX3SC5IYATO",
            "fareClass": "A",
            "fares": [
                {
                    "type": "ADT",
                    "amount": 25.19,
                    "count": 1,
                    "hasDiscount": true,
                    "publishedFare": 25.32,
                    "discountInPercent": 10,
                    "hasPromoDiscount": false,
                    "discountAmount": 0.13,
                    "hasBogof": false
                }
            ]
        },
        "operatedBy": "Buzz"
    }
]
```

## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that is available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.

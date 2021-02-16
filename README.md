# avlcy (aV's Local CurrencY)

![Language Badge](https://img.shields.io/badge/Language-Go-blue.svg) ![Go Report](https://img.shields.io/badge/go_report-A_+-green)

avlcy is a Go program made on the top of Kund Nu Currency Converter API to convert between local currencies.

## Demo

[![asciicast](https://asciinema.org/a/107878.svg)](https://asciinema.org/a/107878)

## Available Currencies

- ATS Austria, shilling
- AUD Australian, dollar
- BEF Belgien, franc
- BRL Brazilien, real
- CAD Canada, dollar
- CHF Switzerland, francs
- CNY China, yuan renminbi
- CYP Cyprus, pound
- CZK Czech Republic, koruna
- DEM Germany, mark
- DKK Denmark, krone
- EEK Estonian, kroon
- ESP Spain, pesetas
- EUR Euroland, euro
- FIM Finland, marka
- FRF France, franc
- GBP Great Britain, pound
- GRD Greece, drachmer
- HKD Hong Kong, dollar
- HUF Hungary, forint
- IDR Indonesia, rupiah
- IEP Ireland, pund
- INR India, rupee
- ISK Iceland, kronor
- ITL Italy, lire
- JPY Japan, yen
- KRW South Korea, won
- KWD Kuwait, dinar
- LTL Lithuania, litas
- LVL Latvia, lat
- MAD Morocko, dirham
- MXN Mexico, nuevo peso
- MYR Malaysia, ringgit
- NLG Dutchland, guilder
- NOK Norway, krone
- NZD New Zealand, dollar
- PLN Poland, zloty
- PTE Portugal, escudo
- RUB Russia, rouble
- SAR Saudi Arabia, riyal
- SEK Sweden, kronor
- SGD Singapore, dollar
- SIT Slovenia, tolar
- SKK Slovakia, koruna
- THB Thailand, baht
- TRL Turkey, lira
- TRY Turkey, new lira
- USD US, dollar
- ZAR South Africa, rand

## Usage

### Go Get

```bash
$ go get github.com/a0v0/avlcy
```

### Get all available currencies

```golang
package main

import (
	"fmt"

	"github.com/a0v0/avlcy"
)

func main() {
	curList, _ := avlcy.AvailableCurrencies()

	for _, currency := range curList {
		fmt.Println(currency.Description)
	}
}
```

Output:

```
SEK Sweden, kronor
ATS Austria, shilling
AUD Australian, dollar
BEF Belgien, franc
BRL Brazilien, real
CAD Canada, dollar
CHF Switzerland, francs
CNY China, yuan renminbi
CYP Cyprus, pound
CZK Czech Republic, koruna
DEM Germany, mark
DKK Denmark, krone
EEK Estonian, kroon
ESP Spain, pesetas
EUR Euroland, euro
FIM Finland, marka
FRF France, franc
GBP Great Britain, pound
GRD Greece, drachmer
HKD Hong Kong, dollar
HUF Hungary, forint
IDR Indonesia, rupiah
IEP Ireland, pund
INR India, rupee
ISK Iceland, kronor
ITL Italy, lire
JPY Japan, yen
KRW South Korea, won
KWD Kuwait, dinar
LTL Lithuania,  litas
LVL Latvia, lat
MAD Morocko, dirham
MXN Mexico, nuevo peso
MYR Malaysia, ringgit
NLG Dutchland, guilder
NOK Norway, krone
NZD New Zealand, dollar
PLN Poland, zloty
PTE Portugal, escudo
RUB Russia, rouble
SAR Saudi Arabia, riyal
SGD Singapore, dollar
SIT Slovenia, tolar
SKK Slovakia, koruna
THB Thailand, baht
TRL Turkey, lira
TRY Turkey, new lira
USD US, dollar
ZAR South Africa, rand
```

### Convert 100 USD to all currencies

```golang
package main

import (
	"fmt"
        "strconv"

	"github.com/a0v0/avlcy"
	"github.com/shopspring/decimal"
)

func main() {
	curList, _ := avlcy.AvailableCurrencies()

	dollar := avlcy.NewCurrency("USD")
        amount := decimal.NewFromFloat(100.00)

	for _, currency := range curList {
		conv, _ := avlcy.ConvertCurrency(dollar, currency, amount)

		fmt.Printf("%-3s %-8s --> %-3s %s\n", dollar.ID, amount, currency.ID, conv)
	}
}
```

Output:

```
USD 100.00 --> SEK 881.12
USD 100.00 --> ATS 1334.36
USD 100.00 --> AUD 130.28
USD 100.00 --> BEF 3911.85
USD 100.00 --> BRL 312.07
USD 100.00 --> CAD 133.35
USD 100.00 --> CHF 99.59
USD 100.00 --> CNY 690.75
USD 100.00 --> CYP 54.42
USD 100.00 --> CZK 2509.74
USD 100.00 --> DEM 189.66
USD 100.00 --> DKK 690.54
USD 100.00 --> EEK 1531.05
USD 100.00 --> ESP 16134.77
USD 100.00 --> EUR 92.88
USD 100.00 --> FIM 576.57
USD 100.00 --> FRF 636.10
USD 100.00 --> GBP 80.95
USD 100.00 --> GRD 33042.83
USD 100.00 --> HKD 776.45
USD 100.00 --> HUF 28765.63
USD 100.00 --> IDR 1333010.59
USD 100.00 --> IEP 76.37
USD 100.00 --> INR 6553.27
USD 100.00 --> ISK 10876.95
USD 100.00 --> ITL 187751.97
USD 100.00 --> JPY 11334.92
USD 100.00 --> KRW 113239.94
USD 100.00 --> KWD 37.74
USD 100.00 --> LTL 319.77
USD 100.00 --> LVL 69.22
USD 100.00 --> MAD 999.46
USD 100.00 --> MXN 1924.26
USD 100.00 --> MYR 489.51
USD 100.00 --> NLG 213.70
USD 100.00 --> NOK 848.16
USD 100.00 --> NZD 143.12
USD 100.00 --> PLN 399.87
USD 100.00 --> PTE 19441.33
USD 100.00 --> RUB 5790.71
USD 100.00 --> SAR 375.02
USD 100.00 --> SGD 140.29
USD 100.00 --> SIT 23310.05
USD 100.00 --> SKK 0.00
USD 100.00 --> THB 3490.97
USD 100.00 --> TRL 176224000.00
USD 100.00 --> TRY 360.64
USD 100.00 --> USD 100.00
USD 100.00 --> ZAR 1277.17
```

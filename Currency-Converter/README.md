# Currency Converter

With this script you can freely convert between 36 different currencies from around the world. The script uses exchange rates downloaded from the European Central Bank via an xml file located at www.ecb.europa.eu/stats/eurofxref/eurofxref-daily.xml. The rates are then stored in your own MySQL database for use and then updated daily.

Example: £2.50 = $4.03

Update (August 2013): The European Central bank have updated the url of their feed. The URL in the script should be updated from www.ecb.int/stats/eurofxref/eurofxref-daily.xml to www.ecb.europa.eu/stats/eurofxref/eurofxref-daily.xml

## Usage

Copy the above code into a new file and save it as CurrencyConverter.php. Whenever you need to make a conversion just include the class file and call the ‘convert’ function. You will need to enter your own mysql database variables such as the login details. The example below will convert £2.50 GBP into US Dollars ($).

```
<?php
   include('CurrencyConverter.php');
   $x = new CurrencyConverter('your_host','your_username','your_password','your_database_name','your_table_name');
   echo $x->convert(2.50,'GBP','USD');
?>
```

If the table doesn’t already exist then it will be created by the script.

## Currency Codes

British Pounds = GBP, US Dollars = USD, Euros = EUR, Australian Dollars = AUD, Bulgarian Leva = BGN, Canadian Dollars = CAD, Swiss Francs = CHF, Chinese Yuan Renminbi = CNY, Cyprian Pounds = CYP, Czech Koruny = CZK, Danish Kroner = DKK, Estonian Krooni = EEK, Hong Kong, Dollars = HKD, Croatian Kuna = HRK, Hungarian Forint = HUF, Indonesian Rupiahs = IDR, Icelandic Kronur = ISK, Japanese Yen = JPY, South Korean Won = KRW, Lithuanian Litai = LTL, Latvian Lati = LVL, Malta Liri = MTL, Malaysian Ringgits = MYR, Norwegian Krone = NOK, New Zealand Dollars = NZD, Philippine Pesos = PHP, Polish Zlotych = PLN, Romanian New Lei = RON, Russian Rubles = RUB, Swedish Kronor = SEK, Singapore Dollars = SGD, Slovenian Tolars = SIT, Slovakian Koruny = SKK, Thai Baht = THB, Turkish New Lira = TRY, South African Rand = ZAR


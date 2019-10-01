CySCA 2018 | Keep it Hidden writeup

Looking at the webpage we are provided we can see an under construction page, which appears to be a sql table.

If we have our user agent set to *BOBDev/1.4* the webpage shows us the paramter *formatted=true*

Changing that to false we see a webpage that has the same table witht he value for flags changed to 1 (this means we are on the right track)

After a while of throwing everything at this webpage another parameter was discovered *debug=*

Looking around on the internet for vulnerabilities in php we found **PHP TEMPLATE INJECTION** where special characters, such as { are used to make the webpage execute arbitrary code or disclose information

making *debug={{self}}* threw an error that said *Template reference not found*

making *debug={{flag}}* caused the page to print the flag
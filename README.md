# Hópverkefni 1

## Hópmeðlimir
Nemendur og notendanöfn verkefnis: 
* Björgvin Hall
    * bjh45@hi.is
* Emma Líf Jónsdóttir
    * elj44@hi.is
* Friðrik Árni Halldórsson
    * fah13@hi.is
* Melkorka Mjöll Jóhönnudóttir
    * mmj8@hi.is

## Setja upp verkefnið

```bash
> git clone https://github.com/bjorgvinhall/vef2-hop1
> cd vef2-hop1 # opna skjalið þar sem verkefni er í
> npm install 
> node setup.js # setja upp gagnagrunninn
> node faker.js # búa til gögn og sett í gagnagrunninn
> nodemon app.js # keyrt verkefnið
```

## Dæmi um notkun

Til að sjá lista yfir allar mögulegar aðgerðir skal velja `GET` á `/` 

* Til að búa til nýjan notanda skal fara á 
    *  `POST` á `/users/register` og stimpla inn notendanafn, lykilorð og email. 
    * Hér er dæmi
    ```bash
    {
    "username": "broskall",
    "password": "smiley123",
    "email": "smile@org.com"
    }
    ```
* Til að skoða síðu með öllum vörum er hægt að fara á `GET` á `/products`. 
* Hægt er að leita að öllum vörum í ákveðnum flokki með því að gera `GET` á `/products?category={category}`, þar sem `{category}` er heiti á viðkomandi flokki. Leitin skilar upplýsingum um allar þær vörur sem viðkomandi flokkur inniheldur.
* Hægt að leita að vörum með ákveðnu leitarorði með því að gera `GET` á `/products?search={query}`, þar sem `{query}` er viðkomandi leitarstrengur. Leitin skilar öllum þeim vörum sem innihalda viðkomandi leitarorð, annaðhvort í titli eða texta.
* Ef notandi vill skoða einhvern sérstakan flokk þá getur hann leitað að honum á `GET` á `/categories`.
* Ef notandi vill setja vöru í körfuna sína þá skal hann fara `POST` á `/cart` og bætir við vöru með að skrifa titil hennar eins og t.d.

     ``` bash
    {
        "title": "Incredible Fresh Soap"
    }
    ```
* Síðan getur notandi skoðað allar vörurnar sínar með reiknuðu heildarverði með því að gera `GET` á `/cart`

## Skrá sig inn sem admin

Til að skrá sig inn sem admin þarf að gera `POST` á `users/login` og stimpla inn netfang og lykilorð

```bash
{
    "email": "admin@example.com"
    "password": "12341234"
}
```

## Bæta við mynd og breyta mynd

Til þess að bæta við myndum á vöru þarf að gera `POST` á `/products/{id}/image`, þar sem `{id}` er númer þeirrar vöru sem bæta á mynd við. Setja þarf inn slóð á mynd í gegnum `form-data`, en notast þarf við `key: imgurl`.

Ef að breyta á mynd á vöru sem nú þegar hefur mynd, er ferlið svipað og fyrir ofan nema það þarf að gera `PATCH` á `/products/{id}/image`.
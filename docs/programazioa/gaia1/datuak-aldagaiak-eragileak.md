# Javaren Eraikuntza-Blokeak: Datuak, Aldagaiak eta Eragileak

!!! abstract "Zer ikasiko duzu gai honetan?"
    Gai honetan Java programen oinarrizko osagaiak ikasiko ditugu: aldagaiak nola deklaratu eta erabiltzen diren, zein datu mota dauden, konstanteak zer diren, eta eragileak nola funtzionatzen duten. Hauek dira edozein programa idazteko ezinbesteko eraikuntza-blokeak.

📄 [Teoria PDF formatuan deskargatu](recursos/G.1.2-Datuak.pdf)

---

## 1. Datuak Memoria-Kaxetan

Programa guztiek datuak erabiltzen dituzte. Datu horiek **aldagaietan** gordetzen dira — memoria-sistemako edukiontzi izendatuetan.

```java
int adina = 20;
```

```
  int        adina       =        20        ;
   │           │          │        │         │
   │           │          │        │         └── Sententziaren amaiera
   │           │          │        └── Balioa (kaxaren edukia)
   │           │          └── Esleipena (sartu ekintza)
   │           └── Identifikatzailea (kaxaren izena)
   └── Mota (zer sartu daiteke kaxan?)
```

!!! tip "Analogia"
    Aldagai bat etiketa duen kaxa bat da. `int` kaxak zenbaki osoak bakarrik onartzen ditu. `String` kaxak testu kateak gordetzen ditu.

---

## 2. Aldagaien Bizitza-Zikloa eta Arauak

### Bizitza-zikloa

Aldagai bat erabiltzeko bi urrats jarraitu behar dira:

```java
// 1. Deklarazioa: kaxaren mota eta izena adierazi
int adina;

// 2. Hasieratzea: balioa sartu
adina = 20;

// Edo biak batera:
double altuera = 1.65;
```

### Izendatzeko Arauak

| | Araua | Adibidea |
|---|---|---|
| ✅ | Hizki txikiz hasi beti | `adina`, `pisua` |
| ✅ | Deskribatzailea izan | `erabiltzaileIzena` ez `ei` |
| ✅ | camelCase hitz anitzetan | `batezBestekoNota` |
| ❌ | Hitz erreserbatuak ez erabili | `class`, `public`, `int`... |
| ❌ | Zenbakiz hasi ezin | `1adina` ❌ |

!!! warning "Java case-sensitive da"
    `adina`, `Adina` eta `ADINA` hiru aldagai **desberdin** dira Java-n.

---

## 3. Zenbakizko Jatorrizko Motak (Primitive Types)

Jatorrizko motek balioa zuzenean memorian gordetzen dute. Datu-mota bakoitzak edukiera zehatz bat dauka.

### Zenbaki Osoak

| Mota | Tamaina | Balioen tartea | Adibidea |
|---|---|---|---|
| `byte` | 8 bit | -128 → 127 | `byte txikia = 120;` |
| `short` | 16 bit | -32.768 → 32.767 | `short motza = 32000;` |
| `int` | 32 bit | -2.147M → 2.147M | `int zenbakia = 25000;` |
| `long` | 64 bit | Oso handia | `long handi = 1000000000L;` |

!!! tip "Zein erabili?"
    Gehienetan **`int`** nahikoa da. `long` erabili zenbaki oso handietarako — eta `L` letra gehitu behar zaio: `1000000000L`

### Zenbaki Hamartarrak

| Mota | Tamaina | Zehaztasuna | Adibidea |
|---|---|---|---|
| `float` | 32 bit | 6-7 digitu | `float altuera = 1.75f;` |
| `double` | 64 bit | 15-16 digitu (**lehenetsia**) | `double pisua = 72.5;` |

!!! warning "float-ek `f` behar du"
    `float altuera = 1.75f;` — `f` letra ahazten bada konpilazio-errorea jasoko duzu.

---

## 4. Karaktereak eta Boolearrak

=== "Karaktereak (char)"
    Karaktere **bakarra** gordetzen du. Komatxo **sinpleak** erabili behar dira:

    ```java
    char letra = 'A';
    char zenbakia = '5';   // '5' karakterea da, ez 5 zenbakia
    char zuriunea = ' ';
    ```

    !!! danger "Komatxo sinpleak vs bikoitzak"
        - `char letra = 'A';`  ✅ Karaktere bat — komatxo sinpleak
        - `String hitza = "Ane";`  ✅ Testu katea — komatxo bikoitzak
        - `char letra = "A";`  ❌ Errorea — char-ak komatxo sinpleak behar ditu

=== "Boolearrak (boolean)"
    Bi balio posible bakarrik ditu: `true` (egia) edo `false` (faltsua).

    ```java
    boolean ikasleaDa = true;
    boolean gainditua = false;
    boolean adultua = (adina >= 18);  // konparaketa baten emaitza
    ```

    Baldintzetarako eta begiztetarako ezinbestekoa da.

---

## 5. Erreferentzia Motak: Objektuak eta Metodoak

Erreferentzia motek ez dute balioa zuzenean gordetzen — **memoriako helbidea** gordetzen dute.

```
Primitiboa:                    Erreferentzia:
┌─────────────┐                ┌─────────────┐
│  int adina  │                │String izena │
│     18      │                │   ────────►  │──► [ "Ane" ]
└─────────────┘                └─────────────┘
  Balioa zuzenean                Helbidea → objektua
```

### String: Erreferentzia Motarik Ohikoena

`String` karaktere-katea da, eta barnean **metodoak** dakartzana:

```java
String izena = "Ane";

// String-en metodo erabilienak
System.out.println(izena.length());        // 3 → luzera
System.out.println(izena.toUpperCase());   // ANE → maiuskulak
System.out.println(izena.toLowerCase());   // ane → minuskulak
System.out.println(izena.charAt(0));       // A → lehen karakterea
System.out.println(izena.contains("ne")); // true → azpikatea
```

| Metodoa | Zer egiten du | Adibidea |
|---|---|---|
| `.length()` | Luzeraren zenbakia itzultzen du | `"Ane".length()` → `3` |
| `.toUpperCase()` | Maiuskuletara bihurtzen du | `"ane".toUpperCase()` → `"ANE"` |
| `.toLowerCase()` | Minuskuletara bihurtzen du | `"ANE".toLowerCase()` → `"ane"` |
| `.charAt(i)` | i. posizioko karakterea itzultzen du | `"Ane".charAt(0)` → `'A'` |
| `.contains(s)` | Azpikatea badagoen egiaztatzen du | `"Ane".contains("ne")` → `true` |

---

## 6. Irismena (Scope): Blokeen Mugak

Aldagai bat deklaratzen den `{ }` giltzen barruan bakarrik da erabilgarria. Blokea amaitzean, **aldagai lokalak suntsitu egiten dira**.

```java
class Batu {

    static int n1 = 50;          // Klasearen aldagaia — denentzat eskuragarri

    public static void main(String[] args) {

        int n2 = 30;             // Aldagai lokala — main barruan bakarrik

        System.out.println(n1);  // ✅ n1 eskuragarri dago
        System.out.println(n2);  // ✅ n2 eskuragarri dago
    }

    // System.out.println(n2);   // ❌ Errorea! n2 hemen ez dago
}
```

!!! note "Arau praktikoa"
    Aldagaia ahalik eta **txikieneko irismenekin** deklaratu. Metodo barruan behar bada, bertan deklaratu.

---

## 7. Konstanteak: Balio Aldaezinak

Konstanteak **behin deklaratuta ezin dira aldatu**. `final` hitza erabiltzen da, eta maiuskulaz idazten dira beti.

```java
final double PI = 3.141592;
final int BEZ = 21;
```

**Erabilera adibidea:**
```java
double erradioa = 5.0;
double azalera = PI * erradioa * erradioa;   // ✅
PI = 3.14;                                    // ❌ Error: cannot assign a value to final variable PI
```

!!! tip "Zergatik erabili konstanteak?"
    - Balio garrantzitsu bat aldatzen bada, leku bakarrean aldatu behar da
    - Kodea irakurterrazagoa egiten du (`PI` `3.141592` baino argiagoa da)
    - Akatsak ekiditen laguntzen du

---

## 8. Eragile Aritmetikoak eta Esleipenak

### Eragile Aritmetikoak

```java
int a = 10, b = 3;

System.out.println(a + b);   // 13 → Batuketa
System.out.println(a - b);   // 7  → Kenketa
System.out.println(a * b);   // 30 → Biderketa
System.out.println(a / b);   // 3  → Zatiketa (osoa!)
System.out.println(a % b);   // 1  → Hondarra / Modulua
```

!!! warning "Osoko zatiketa"
    `10 / 3 = 3` Java-n, ez `3.33`. Dezimala nahi baduzu:
    ```java
    double emaitza = (double) 10 / 3;   // 3.333...
    ```

### Eragile Unarioak: ++ eta --

```java
int m = 2;

m++;           // m = 3 (ondoren handitu)
System.out.println(m++);   // 3 erakutsi, gero m=4 bihurtu
System.out.println(++m);   // lehenik m=5, gero 5 erakutsi
```

### Esleipen Eragileak

```java
int num = 10;

num += 5;    // num = num + 5  → 15
num -= 3;    // num = num - 3  → 12
num *= 2;    // num = num * 2  → 24
num /= 4;    // num = num / 4  → 6
num %= 4;    // num = num % 4  → 2
```

`num += 5` idaztea `num = num + 5` idaztea bezalakoa da — laburpena besterik ez.

---

## 9. Eragile Erlazionalak eta Logikoak

### Erlazionalak — Balioak Alderatzeko

Beti `boolean` balio bat itzultzen dute (`true` edo `false`):

```java
int a = 5, b = 3;

System.out.println(a > b);    // true  → handiagoa
System.out.println(a < b);    // false → txikiagoa
System.out.println(a >= b);   // true  → handiagoa edo berdina
System.out.println(a <= b);   // false → txikiagoa edo berdina
System.out.println(a == b);   // false → berdinak dira?
System.out.println(a != b);   // true  → ezberdinak dira?
```

!!! danger "= eta == ez nahastu"
    - `=` → esleipena: `adina = 20;`
    - `==` → konparaketa: `adina == 20`
    - `adina = 20` idazteak balioa **aldatzen** du. `adina == 20` idazteak **egiaztatzen** du.

### Logikoak — Kondizio Anitzak Elkartzeko

```java
int adina = 20;
boolean ikaslea = true;

System.out.println(adina >= 18 && ikaslea);   // true  → AND: biak true
System.out.println(adina < 18 || ikaslea);    // true  → OR: bat true nahikoa
System.out.println(!ikaslea);                  // false → NOT: alderantzizkoa
```

**Egia-taula:**

| A | B | A && B | A \|\| B | !A |
|---|---|---|---|---|
| true | true | true | true | false |
| true | false | false | true | false |
| false | true | false | true | true |
| false | false | false | false | true |

---

## 10. Lehentasunen Piramidea

Eragile anitz daudenean, Java-k lehentasun-ordenaren arabera exekutatzen ditu:

```
        ┌─────────────────────────┐
    1   │     Parentesiak  ( )    │  ← Lehentasun gorena
        ├─────────────────────────┤
    2   │   Unarioak  ++, --, !   │
        ├─────────────────────────┤
    3   │   Biderketa / Zatiketa  │
        │        *, /, %          │
        ├─────────────────────────┤
    4   │   Batuketa / Kenketa    │
        │          +, -           │
        ├─────────────────────────┤
    5   │  Erlazionalak/Logikoak  │
        │  <, >, <=, >=, ==, !=   │
        │      &&, ||, !          │
        ├─────────────────────────┤
    6   │      Esleipenak  =      │  ← Lehentasun baxuena
        └─────────────────────────┘
```

**Adibidea:**
```java
int emaitza = 2 + 3 * 4;    // 14, ez 20 — * lehenik exekutatzen da
int emaitza = (2 + 3) * 4;  // 20 — parentesiak lehentasuna aldatzen dute
```

!!! tip "Arau praktikoa"
    Zalantzarik bada, **parentesiak erabili** — kodea argiagoa eta seguruagoa egingo du.

---

## 11. Adibide Osoa: Piezak Ahokatzen

```java
public class Datuak {
    public static void main(String[] args) {

        // Datu mota jatorrizkoak
        int adina = 19;
        double altuera = 1.72;
        boolean ikasleaDa = true;

        // Erreferentzia mota
        String izena = "Jon";

        // Pantailaratzea katea elkartzea (+) erabiliz
        System.out.println("Izena: " + izena);
        System.out.println("Adina: " + adina);
        System.out.println("Altuera: " + altuera);
        System.out.println("Ikaslea da? " + ikasleaDa);
    }
}
```

**Emaitza:**
```
Izena: Jon
Adina: 19
Altuera: 1.72
Ikaslea da? true
```

---

## 12. Ariketak

!!! question "1. Ariketa — Sorkuntza"
    Sortu programa bat zure izena (`String`), adina (`int`) eta altuera (`double`) aldagaietan gordeko dituena eta pantailaratuko dituena.

??? success "Irtenbidea"
    ```java
    public class NireDatuak {
        public static void main(String[] args) {
            String izena = "ZureIzena";
            int adina = 25;
            double altuera = 1.80;
            System.out.println(izena + ", " + adina + ", " + altuera);
        }
    }
    ```

!!! question "2. Ariketa — Kalkulua"
    Kalkulatu zirkunferentziaren luzera `r=3` izanik. Formula: `luzera = 2 * PI * r`. Erabili `final` konstante bat PI-rentzat.

??? success "Irtenbidea"
    ```java
    public class Zirkunferentzia {
        public static void main(String[] args) {
            final double PI = 3.141592;
            double r = 3;
            double luzera = 2 * PI * r;
            System.out.println("Luzera: " + luzera);
        }
    }
    ```

!!! question "3. Ariketa — Konstanteen Legea"
    Deklaratu `final double PI = 3.14159` konstante bat eta saiatu berari beste balio bat esleitzen. Zer errorea ematen du konpiladoreak?

??? success "Irtenbidea"
    ```java
    final double PI = 3.14159;
    PI = 3.14;  // ❌ Error: cannot assign a value to final variable PI
    ```
    `final` aldagaiak behin bakarrik esleitu daitezke. Gero ezin dira aldatu.

!!! question "4. Ariketa — Logika: Trukatze Erronka"
    Trukatu bi aldagairen (`a = 5` eta `b = 10`) balioak **hirugarren aldagairik gabe**. Pista: eragile aritmetikoak erabili.

??? success "Irtenbidea"
    ```java
    public class Trukatzea {
        public static void main(String[] args) {
            int a = 5;
            int b = 10;

            a = a + b;   // a = 15
            b = a - b;   // b = 5  (lehengo a)
            a = a - b;   // a = 10 (lehengo b)

            System.out.println("a = " + a);  // 10
            System.out.println("b = " + b);  // 5
        }
    }
    ```

---

## Kontzeptuen Laburpen-Taula

| Kontzeptua | Sintaxia | Adibidea |
|---|---|---|
| Aldagaia | `<mota> <izena> = <balioa>;` | `int adina = 20;` |
| Konstante | `final <mota> <IZENA> = <balioa>;` | `final double PI = 3.14;` |
| Zenbaki osoa | `int`, `long`, `byte`, `short` | `int n = 42;` |
| Dezimala | `double`, `float` | `double d = 3.14;` |
| Karakterea | `char` (komatxo sinpleak) | `char c = 'A';` |
| Logikoa | `boolean` | `boolean b = true;` |
| Testu katea | `String` (komatxo bikoitzak) | `String s = "Kaixo";` |
| Hondarra | `%` | `10 % 3` → `1` |
| Berdintasuna | `==` | `a == b` |
| Esleipena | `=` | `a = 5` |

---

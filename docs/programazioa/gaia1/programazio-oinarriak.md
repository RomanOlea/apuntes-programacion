
# Oinarrizko Programazioa Javan

!!! abstract "Zer ikasiko duzu gai honetan?"
    Gai honetan Java programazio-lengoaiaren oinarriak ikasiko ditugu: programa bat zer den, nola antolatzen den, zein datu mota dauden eta nola idazten den lehen programa. Hau 1. DAMeko programazioaren abiapuntua da.

📄 [Teoria PDF formatuan deskargatu](recursos/G_1_0_-_Programazio_Oinarriak.pdf)

---

## 1. Aplikazioen Antolaketa: Egitura Logikoa

Java aplikazio bat hainbat elementuz osatuta dago, hierarkikoki antolatuta:

```
Proiektua
└── Paketeak
    └── Azpi-paketeak
        ├── Kalkulagailua.java   (Klasea)
        └── Ikaslea.java         (Klasea)
```

| Elementua | Azalpena |
|---|---|
| **Proiektua** | Aplikazioaren oinarri nagusia. Klasez osatuta dago. |
| **Paketeak** | Klaseak antolatzeko modu logikoa. Proiektu handietan antolaketa errazten dute. |
| **Azpi-paketeak** | Egitura hierarkikoa sortzeko — pakete baten barruan beste batzuk egon daitezke. |
| **Klaseak** | Benetako kodea gordetzen duten fitxategiak (adib. `Kalkulagailua.java`). |

!!! tip "Analogia"
    Pentsatu proiektua liburutegi bat dela, paketeak sailak direla eta klaseak liburuak direla. Dena ordenatuta egoteak bilaketa errazten du.

---

## 2. Programa Baten Egitura Generikoa

Java programa batek beti egitura bera du:

```java
package nire_paketea;

import kanpoko_liburutegiak;

public class ProgramaAdibidea {

    // Aldagaien adierazpena
    int zenbakia;
    String testua;

    // main metodoa (Exekutatzen dena)
    public static void main(String[] args) {
        // Sententziak
    }
}
```

| Zatia | Azalpena |
|---|---|
| `package nire_paketea` | Fitxategia zein paketetakoa den adierazten du |
| `import kanpoko_liburutegiak` | Kanpoko klaseak edo liburutegiak ekartzeko |
| `public class ProgramaAdibidea` | Objektuaren egitura. Klase publiko bakarra egon daiteke fitxategiko |
| `public static void main(String[] args)` | Programaren exekuzio-fluxuaren hasiera puntua |

### `main` metodoaren hitzen esanahia

```
public   static   void   main   (String[] args)
  │        │        │      │           │
  │        │        │      │           └── String-en array bat. Parametro gisa
  │        │        │      │               testu kateak jasotzeko prestatua.
  │        │        │      └── Programa hastean gauzatutako metodo-mota berezia.
  │        │        │          Javan kode guztia klase baten barruan egon behar da.
  │        │        └── Metodo honek ez du ezer itzultzen.
  │        └── Klasea instantziatu gabe deitu dakioke.
  └── Edozein lekutatik deitu daiteke.
```

---

## 3. Fitxategien Izenen Urrezko Araua

!!! danger "Arau garrantzitsua"
    Java-n **klase publikoaren izena eta fitxategiaren izena berdinak izan behar dira** (maiuskulak/minuskulak barne). Hau ez betetzeak konpilazio-errorea sortuko du.

=== "✅ Zuzena"
    ```java
    // Fitxategia: Kaixo.java
    public class Kaixo {
        public static void main(String[] args) {
            System.out.println("Kaixo Mundua!");
        }
    }
    ```

=== "❌ Okerra"
    ```java
    // Fitxategia: Kaixo.java
    public class Agur {   // Errorea: fitxategiaren izenarekin ez dator bat
        public static void main(String[] args) {
            System.out.println("Agur!");
        }
    }
    ```

!!! tip "Konbentzioa"
    Klase izenak **letra larriz** hasten dira beti: `KaixoMundua`, `Kalkulagailua`, `IkasleZerrenda`.

---

## 4. Kanpoko Liburutegiak: JAR Fitxategiak

**JAR** (Java ARchive) fitxategi bat ZIP fitxategi moduko bat da, baina barruan konpilatutako `.class` fitxategiak eta manifest fitxategi bat ditu.

**Zertarako balio du?**
Aplikazioek beste proiektu batzuen laguntza behar dutenean erabiltzen da funtzionalitateak zabaltzeko.

**Adibidea:**
```
commons-math3-3.6.1.jar   ← Apache Commons Math liburutegia
```

```java
import org.apache.commons.math3.stat.StatUtils;

public class Estatistikak {
    public static void main(String[] args) {
        double[] datuak = {1.0, 2.0, 3.0, 4.0};
        double batezbestekoa = StatUtils.mean(datuak);
        System.out.println("Batez bestekoa: " + batezbestekoa);
    }
}
```

!!! note "Maven eta Gradle"
    Geroago ikasiko duzun bezala, Maven eta Gradle tresnek JAR fitxategiak automatikoki kudeatzen dituzte. Ez da eskuz deskargatu behar.

---

## 5. Lehenengo Programa: 'Kaixo Mundua'

Tradizionalki, programazio-lengoaia berri bat ikastean idazten den lehen programa "Kaixo Mundua" da:

```java
package ejemplos;

/*
 * Ejemplo HolaMundo
 * Imprime el mensaje "Hola, Mundo!" con salto de línea
 */
public class HolaMundo {
    public static void main(String[] args) {
        // Imprime el mensaje "Hola, Mundo!"
        System.out.println("Hola, Mundo!");
    }
}
```

**Programa honek erakusten duena:**

- `package` adierazpena nola idazten den
- `/* ... */` iruzkina nola erabiltzen den
- `// ...` lerroko iruzkina nola erabiltzen den
- `System.out.println()` pantailaratzeko nola erabiltzen den

---

## 6. Kodea Dokumentatzen: Iruzkinak

Iruzkinak programatzaileentzat idatzitako oharrak dira. **Konpiladoreak ez ditu kontuan hartzen.**

=== "Lerroko Iruzkina"
    ```java
    // Testua
    ```
    Hasi `//`-rekin eta lerroaren amaieraraino zabaltzen da.

=== "Paragrafo Iruzkina"
    ```java
    /* Testua */
    ```
    Lerro batean edo gehiagotan egon daiteke. Ez dio exekuzio-fluxuari eragiten.

=== "Javadoc Iruzkina"
    ```java
    /** Testua */
    ```
    HTML-n dokumentazio ofiziala sortzeko (Oracle APIlaren estilora). Etiketak onartzen ditu.

**Javadoc etiketak:**

| Etiketa | Erabilera |
|---|---|
| `@param` | Metodo baten parametroa azaltzeko |
| `@return` | Metodoaren itzulera balioa azaltzeko |
| `@author` | Egilea adierazteko |
| `@version` | Bertsioa adierazteko |

```java
/**
 * Bi zenbaki batzen dituen metodoa.
 * @param a Lehen zenbakia
 * @param b Bigarren zenbakia
 * @return Batura emaitza
 */
public int batu(int a, int b) {
    return a + b;
}
```

---

## 7. Aldagaiak: Datuen Biltegiak

Aldagai bat **balio bat gordetzen den memoria-posizio bat da**. Izen bat du (identifikatzailea) bertara sarbidea emateko.

### Adierazpen sintaxia

```java
<mota> <izena> = [balioa];
```

```java
int adina = 25;           // osoko zenbakia
double altura = 1.75;     // dezimal zenbakia
boolean aktiboa = true;   // balio logikoa
char letra = 'A';         // karaktere bakarra
String izena = "Ane";     // testu katea
```

### Aldagaien arauak

- Izen **deskribatzaileak** erabiltzea komeni da: `adina` ez `a`, `erabiltzaileIzena` ez `ei`
- Beti **letra xehe** batetik hasi: `adina`, `erabiltzaileIzena`
- Hitz anitzeko izenak **camelCase** formatuan: `batezBestekooBalioa`
- **Ezin dira** erabili: `class`, `int`, `public`... (Java hitz erreserbatuak)

!!! warning "Kontuz maiuskulak/minuskulakekin"
    Java **case-sensitive** da. `adina`, `Adina` eta `ADINA` hiru aldagai desberdin dira.

---

## 8. Datu Motak

Javak bi aldagai mota ditu: **Jatorrizko motak** eta **Erreferentzia motak**.

### Jatorrizko Motak (Primitive Types)

Memorian balioa zuzenean gordetzen dute.

| Mota | Tamaina | Balioen tartea | Adibidea |
|---|---|---|---|
| `byte` | 1 byte | -128 → 127 | `byte b = 100;` |
| `short` | 2 byte | -32.768 → 32.767 | `short s = 1000;` |
| `int` | 4 byte | -2.147M → 2.147M | `int i = 42;` |
| `long` | 8 byte | Oso handia | `long l = 123456789L;` |
| `float` | 4 byte | 6-7 dezimal digitu | `float f = 3.14f;` |
| `double` | 8 byte | 15-16 dezimal digitu | `double d = 3.14159;` |
| `boolean` | 1 bit | `true` / `false` | `boolean b = true;` |
| `char` | 2 byte | Karaktere bakarra | `char c = 'A';` |

!!! tip "Zein erabili?"
    - Zenbaki osoetarako → `int` (gehienetan nahikoa)
    - Dezimaletarako → `double` (zehaztasun handiagoa `float` baino)
    - Egia/Gezurra → `boolean`
    - Karaktere bakarrerako → `char` (komatxo **sinpleak**: `'A'`)

### Erreferentzia Motak (Reference Types)

Objektu bati egiten diote erreferentzia — daturik ez, memoria-helbidea gordetzen dute.

| Mota | Adibidea |
|---|---|
| `String` | `String izena = "Ane";` |
| Array-ak | `int[] zenbakiak = {1, 2, 3};` |
| Klaseak | `Scanner sarrera = new Scanner(System.in);` |

**Defektuzko balioa:** `null` (inora apuntatzen ez duenean)

---

## 9. Erreferentzia Motak eta Heap Memoria

```
Jatorrizko aldagaia:          Erreferentzia aldagaia:
┌─────────────────┐           ┌─────────────────┐
│aPrimitiveVariable│           │aReferenceVariable│
│      value      │           │    reference  ●──┼──→  [ Heap memoria ]
└─────────────────┘           └─────────────────┘      [ An instance  ]

                               ┌─────────────────┐
                               │aReferenceVariable│
                               │      null    ●──┼──→  ✗ (inora ez)
                               └─────────────────┘
```

- **Zuzenbidea**: Datuak dauden memoriaren helbidea gordetzen dute, ez datua bera.
- **Heap eremua**: Objektu konplexuak (instantziak) `Heap` izeneko memoria gunean sortzen dira.
- **Null balioa**: Erreferentzia batek inora apuntatzen ez duenean, bere balioa `null` da.

!!! warning "NullPointerException"
    `null` balioko erreferentzia bati metodo bat deitzen badiozu, **NullPointerException** errorea jasoko duzu. Java-ko errore ohikoenetako bat da.

---

## 10. Emaitzak Pantailaratzea

```java
System.out.println("Testua");   // Inprimatu eta lerro-jauzia egin
System.out.print("Testua");     // Inprimatu baina lerro berean jarraitu
```

### Konkatenazioa (`+` ikurra)

`+` ikurra erabiliz testu kateak eta aldagaiak elkar daitezke pantailaratzeko:

```java
int balioa = 10;
String izena = "Ane";

System.out.println("Balioa hau da: " + balioa);
System.out.println("Erabiltzailea: " + izena + ", adina: " + balioa);
```

**Irteera:**
```
Balioa hau da: 10
Erabiltzailea: Ane, adina: 10
```

!!! tip "printf erabiltzea"
    Formatu kontrolatuagoa nahi baduzu:
    ```java
    System.out.printf("Izena: %s, Adina: %d%n", izena, adina);
    ```
    - `%s` → String batentzat
    - `%d` → Osoko zenbaki batentzat
    - `%f` → Dezimal zenbaki batentzat
    - `%n` → Lerro-jauzia

---

## 11. Operadoreak: Datuak Eraldatzeko Tresnak

### Aritmetikoak

```java
int a = 10, b = 3;

System.out.println(a + b);   // 13 → Batuketa
System.out.println(a - b);   // 7  → Kenketa
System.out.println(a * b);   // 30 → Biderketa
System.out.println(a / b);   // 3  → Zatiketa (osoa!)
System.out.println(a % b);   // 1  → Hondarra (modulo)
System.out.println(a++);     // 10 → Lehenik erabili, gero handitu
System.out.println(++a);     // 12 → Lehenik handitu, gero erabili
```

!!! warning "Osoko zatiketa"
    `10 / 3 = 3` Java-n, ez `3.33`. Dezimala nahi baduzu: `(double) 10 / 3`

### Erlazionalak

```java
int a = 5, b = 3;

System.out.println(a > b);    // true
System.out.println(a < b);    // false
System.out.println(a >= b);   // true
System.out.println(a <= b);   // false
System.out.println(a == b);   // false  → Berdintasuna
System.out.println(a != b);   // true   → Desberdintasuna
```

### Logikoak / Booleanoak

```java
boolean a = true, b = false;

System.out.println(a && b);   // false → AND: biak true izan behar
System.out.println(a || b);   // true  → OR: bat true nahikoa
System.out.println(!a);       // false → NOT: alderantzizkoa
```

### Esleipenezkoak

```java
int x = 10;

x += 5;    // x = x + 5  → 15
x -= 3;    // x = x - 3  → 12
x *= 2;    // x = x * 2  → 24
x /= 4;    // x = x / 4  → 6
x %= 4;    // x = x % 4  → 2
```

---

## 12. Laburpena: Dena Elkarlanean

Hona hemen ikasitako kontzeptu guztiak programa txiki batean:

```java
package estatistikak;                                        // 1. Paketea

import org.apache.commons.math3.stat.StatUtils;             // 2. JAR/Liburutegia

public class Estatistikak {                                  // 3. Klasearen egitura

    public static void main(String[] args) {

        double[] datuak = {1.0, 2.0, 3.0, 4.0};            // 4. Erreferentzia mota (Array-a)

        double batezbestekoa = StatUtils.mean(datuak);       // 5. Jatorrizko mota + Esleipen operadorea

        System.out.println("Batez bestekoa: " + batezbestekoa); // 6. Pantailaratzea konkatenazioarekin
    }
}
```

**Programa txiki honek bateratzen duena:**

1. Paketeak → aplikazioaren antolaketa
2. JAR liburutegia → kanpoko funtzionalitateak
3. Klasearen egitura → Java programaren oinarria
4. Erreferentzia mota → array bat sortu
5. Jatorrizko mota → emaitza `double` batean gorde
6. Pantailaratzea → emaitza erakutsi

---

## Kontzeptuen Laburpen-Taula

| Kontzeptua | Adibidea | Azalpena |
|---|---|---|
| Paketea | `package com.ejemplo;` | Klaseak antolatzeko |
| Inportazioa | `import java.util.Scanner;` | Kanpoko klaseak ekartzeko |
| Klasea | `public class Kaixo {}` | Kodearen edukiontzia |
| main metodoa | `public static void main(String[] args)` | Exekuzioaren hasiera |
| Aldagaia | `int adina = 25;` | Datu biltegi bat |
| Jatorrizko mota | `int, double, boolean, char` | Balio sinpleak |
| Erreferentzia mota | `String, Scanner, int[]` | Objektuak |
| Pantailaratzea | `System.out.println()` | Irteera kontsolan |
| Iruzkina | `// ...` edo `/* ... */` | Kodearen azalpena |

---

## Ariketak

!!! question "1. Ariketa — Lehen programa"
    Sortu `NireIzena.java` fitxategi bat zure izena eta abizena pantailaratzen duena bi lerrotan.

??? success "Irtenbidea"
    ```java
    public class NireIzena {
        public static void main(String[] args) {
            System.out.println("Izena: Ane");
            System.out.println("Abizena: Etxeberria");
        }
    }
    ```

!!! question "2. Ariketa — Aldagaiak"
    Sortu programa bat ikasle baten datuak (izena, adina, nota) aldagaitan gordetzen dituena eta pantailaratzen dituena.

??? success "Irtenbidea"
    ```java
    public class IkasleaDatuak {
        public static void main(String[] args) {
            String izena = "Mikel";
            int adina = 20;
            double nota = 8.5;

            System.out.println("Izena: " + izena);
            System.out.println("Adina: " + adina);
            System.out.println("Nota: " + nota);
        }
    }
    ```

!!! question "3. Ariketa — Operadoreak"
    Bi zenbaki adierazi aldagaietan eta eragiketa hauek egin eta pantailan erakutsi: batuketa, kenketa, biderketa, zatiketa eta hondarra.

??? success "Irtenbidea"
    ```java
    public class Kalkulagailua {
        public static void main(String[] args) {
            int a = 15;
            int b = 4;

            System.out.println("Batuketa: " + (a + b));
            System.out.println("Kenketa: " + (a - b));
            System.out.println("Biderketa: " + (a * b));
            System.out.println("Zatiketa: " + (a / b));
            System.out.println("Hondarra: " + (a % b));
        }
    }
    ```

---

*Gai hau 1. DAMeko Programazio moduluaren sarrera da — Informatika Sistemen Administrazioa*

# Java Programazio Lengoaia

!!! abstract "Zer ikasiko duzu gai honetan?"
    Gai honetan Java programazio-lengoaiaren oinarriak ikasiko ditugu: zer den programazio-lengoaia bat, nola funtzionatzen duen Java makinak, zein diren Java-ren ezaugarri nagusiak eta nola idazten eta exekutatzen den lehen programa. Hau 1. DAMeko programazioaren sarrera teorikoa da.

📄 [Teoria PDF formatuan deskargatu](recursos/G_1_1_-_Java_Programazio_Lengoaia.pdf)

---

## 1. Programazio Lengoaia: Gizakiaren eta Makinaren Arteko Zubia

Ordenagailuak ez daki zer egin nahi dugun berez — aginduak eman behar dizkiogu. Baina ordenagailuak **0 eta 1** bakarrik ulertzen ditu. Hemen sartzen da programazio-lengoaia.

```
Gizakia                    Programazio Lengoaia                    Makina
────────────────      ──────────────────────────────────      ──────────────
Helburuak eta    →    Funtzio jakin bat betetzeko          →   Funtzionamendu
arrazoibideak         ordenatutako agindu edo jarraibide        bitarra
                      sorta bat. Ordenagailuari zer egin        (0 eta 1)
                      behar duen esaten dion sekuentzia.
```

**Adibidea:**

| Gizakia nahi duena | Java kodea | Makinak ulertzen duena |
|---|---|---|
| Sartu bi zenbaki eta batura erakutsi | `int batura = a + b;` | `10110100 00000001...` |

---

## 2. Programazio Lengoaien Maila

Hiru maila bereizten dira ordenagailuarekiko gertutasunaren arabera:

=== "Kode Makina"
    ```
    10110100
    00000001
    ```
    Ordenagailuak ulertzen duen hizkuntza bakarra. Konplexuegia gizakientzat — inork ez du zuzenean idazten.

=== "Assembler"
    ```asm
    MOV AX, 1
    ```
    Agindu sinpleak (hitzak) erabiliz prozesadoreari hitz egiteko modu zuzena. Gizakiarentzat irakurgarriagoa, baina oraindik zaila.

=== "Java (Goi Mailako Lengoaia)"
    ```java
    int zenbakia = 1;
    ```
    Gizakiontzat ulergarriagoa. Konpiladoreak edo interpreteak itzultzen du makina kodera automatikoki.

!!! tip "Analogia"
    Assembler eraikuntza-planoak dira (zehatzak baina konplexuak). Java arkitektoaren diseinua da (argia eta ulergarria). Biak eraikin bera deskribatzen dute, baina maila desberdinetan.

---

## 3. Java-ren Iraultza: Write Once, Run Anywhere

Lengoaia tradizionalek (C, C++) arazo bat zuten: sistema eragile bakoitzerako konpilazio desberdina behar zen.

### Tradizionala (C, C++)

```
Iturburu-kodea
      │
      ├── Konpilazioa → Linux Exekutagarria
      ├── Konpilazioa → Windows Exekutagarria
      └── Konpilazioa → Mac Exekutagarria
```

Makina bakoitzerako konpilazio desberdina behar da.

### Java-ren Irtenbidea

```
holamundo.java
      │
      ▼
  Konpilazioa (javac)
      │
      ▼
holamundo.class (Bytecode)
      │
      ├── Linux  + JVM → ✅ Exekutatu
      ├── Windows + JVM → ✅ Exekutatu
      └── Mac    + JVM → ✅ Exekutatu
```

!!! success "Behin idatzi, edonon exekutatu"
    **Write Once, Run Anywhere** — Java-ren filosofia nagusia. JVM (Java Virtual Machine) instalatuta dagoen edozein makinatan exekutatu daiteke programa bera.

---

## 4. Java Nola Funtzionatzen Den: Konpilazioa eta Interpretazioa

Java-k bi urrats erabiltzen ditu zure kodea exekutatzeko:

```
.java fitxategia          Konpiladorea (javac)        .class fitxategia         Interpretea (JVM)
────────────────    →    ──────────────────────   →   ─────────────────   →    ──────────────────
Iturburu-kodea           Programa osoa itzultzen       Bytecode                 Bytecode-a lerroz
(guk idatzitakoa)        du Java kodetik bytecode-ra   (tarteko kodea)          lerro interpretatzen
                                                                                du eta exekutatzen du
                                                                                        │
                                                                                 ┌──────┼──────┐
                                                                              Windows Linux  Mac
```

| Urratsa | Tresna | Zer egiten du |
|---|---|---|
| 1. Konpilazioa | `javac` | `.java` fitxategia `bytecode`-ra itzultzen du |
| 2. Exekuzioa | `java` (JVM) | `bytecode`-a lerroz lerro interpretatzen du |

!!! note "Bytecode-a"
    Bytecode-a ez da kode makina (0 eta 1 hutsak) baina ez da goi mailako kodea ere. Tarteko hizkuntza bat da, JVM-ak ulertzeko prestatua, plataforma guztietarako berdina dena.

---

## 5. JDK, JRE eta JVM: Zer Behar Dugu?

```
┌─────────────────────────────────────────────────────────┐
│                  JDK (Java Development Kit)              │
│  Programatzaileen tresnak. Aplikazioak sortzeko eta      │
│  garatzeko behar dena (konpiladoreak, araizketa tresnak) │
│                                                          │
│   ┌───────────────────────────────────────────────────┐  │
│   │           JRE (Java Runtime Environment)          │  │
│   │  Exekuzio-ingurunea. Java aplikazio bat           │  │
│   │  exekutatzeko soilik behar diren osagaiak         │  │
│   │                                                   │  │
│   │   ┌─────────────────────────────────────────────┐ │  │
│   │   │         JVM (Java Virtual Machine)          │ │  │
│   │   │  Makina birtuala. Bytecode-a ulertu eta     │ │  │
│   │   │  prozesadorearen agindu bihurtzen duen      │ │  │
│   │   │  motorra. Klase liburutegiak ere            │ │  │
│   │   │  hemen biltzen dira.                        │ │  │
│   │   └─────────────────────────────────────────────┘ │  │
│   └───────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────┘
```

| Osagaia | Nork behar du | Zertarako |
|---|---|---|
| **JVM** | Denek | Java programak exekutatzeko motor minimoa |
| **JRE** | Erabiltzaile arruntek | Java aplikazioak exekutatzeko (JVM + liburutegiak) |
| **JDK** | Programatzaileek | Java kodea idazteko eta konpilatzeko (JRE + tresnak) |

!!! tip "Laburpena"
    Programatzaile bezala **JDK** erabili behar dugu beti. JDK-k JRE eta JVM barne hartzen ditu.

---

## 6. JDK-ren Tresna-kutxa: Kontsola Tresnak

JDK instalatzean tresna multzo bat eskuratzen dugu terminaletik erabiltzeko:

| Komandoa | Azalpena |
|---|---|
| `javac` | Javaren konpiladorea. `.java` fitxategiak `.class`-era biltzen ditu |
| `java` | Javaren makina birtuala (exekuzio motorra) |
| `javap` | Klase-desmihiztatzaile (desensablador) bat da |
| `jdb` | Javako kontsola araztegia (depurador) akatsak aurkitzeko |
| `javadoc` | Dokumentazio-sortzailea da |
| `appletviewer` | Applet-ak ikusteko tresna |

**Erabilera adibidea:**

```bash
# 1. Konpilatu
javac Kaixo.java        → Kaixo.class sortzen du

# 2. Exekutatu
java Kaixo              → Programa exekutatzen du
```

---

## 7. Java-ren Ezaugarri Nagusiak

| Ezaugarria | Azalpena |
|---|---|
| **Multiplataforma** | Sistemaren araberakoa ez da — JVM egonda berdin funtzionatzen du |
| **Objektuei Zuzendurikoa** | Programak objektuetan eta klaseetan antolatzen dira |
| **Segurtasuna** | Memoria ez dugu zuzenean manipulatzen — JVM arduratzen da horretaz |
| **Liburutegi Ugari** | Aurrez eraikitako klase asko ditu eskuragarri (`String`, `Scanner`, `Math`) |
| **Komunitate Handia** | Oso erabilia da — dokumentazio eta baliabide ugari ditu mundu mailan |

---

## 8. Kodearen Arkitektura: Fitxategi Fisikoen Kudeaketa

Java programa batek hainbat fitxategi izan ditzake. Konpilazioak fitxategi bakoitzarentzat `.class` bat sortzen du:

```
Iturburu Kodea              Konpilazioa              Aplikazioa
──────────────────                 │              ──────────────────
  C1.java                          │                  C1.class
  C2.java          ───────────────►│◄───────────────  C2.class
  Cmain.java                       │                  Cmain.class
```

```bash
# Exekuzioa: main() metodoa duen klasetik hasten da
java Cmain
```

!!! note "Fitxategien banaketa"
    Konpilatutako `.class` fitxategiek ez dute zertan direktorio jakin batean egon — makinatan banatuta egon daitezke. Hau da Java-ren banaketa-arkitekturaren oinarria.

---

## 9. Lehen Programa: Kaixo Mundua

### Egitura aztertuta

```java
public class Kaixo {                              // ①
    public static void main(String[] args) {      // ②
        System.out.println("Kaixo Mundua!");      // ③
    }                                             // ④
}                                                 // ⑤
```

| Zenbakia | Zatia | Azalpena |
|---|---|---|
| ① | `public class Kaixo` | Fitxategiaren kanpotik erabil daitekeen aldatzailea. Klase izena eta fitxategi izena berdinak izan behar dira |
| ② | `public static void main(String[] args)` | Programaren hasierako puntua. JVM-ak beti metodo hau bilatzen du exekuzioa hasteko |
| ③ | `System.out.println(...)` | Testua erakusten duen metodoa. `;` ezinbestekoa |
| ④ | `}` | `main` metodoaren amaiera |
| ⑤ | `}` | Klasearen amaiera |

### `main` metodoaren hitzen esanahia

| Hitza | Esanahia |
|---|---|
| `public` | Edonondik (baita JVMtik ere) deitu ahal izateko |
| `static` | Klaseko objekturik sortu gabe zuzenean dei dakioke |
| `void` | Metodo honek ez du inongo baliorik itzultzen amaitzean |
| `main` | Programaren hasierako puntua. JVM-ak beti metodo hau bilatzen du |
| `String[] args` | Kanpotik (kontsolatik) pasatzen zaizkion parametroak onartzeko |

### `System.out.println` aztertuta

```java
System.out.println("Kaixo Mundua!");
  │      │    │              │
  │      │    │              └── Erakutsi nahi dugun testu katea
  │      │    └── Testua erakusten duen metodoa (lerro-itzulera egiten du)
  │      └── Pantailako informazioa ateratzeko atributua
  └── Programa bateko edozein puntutatik dei daitekeena
```

!!! warning "Puntu eta koma ezinbestekoa"
    Javako agindu guztiak **puntu eta komaz** amaitzen dira (`;`), giltza-itxiturak izan ezik. Ahaztu ezkero konpilazio-errorea jasoko duzu.

---

## 10. Iruzkinak Javan

Iruzkinak konpiladoreak **ez ditu kontuan hartzen** — programatzaileentzat idatzitako oharrak dira.

```java
/**
 * @author Irakaslea
 * This is a sample class for demonstration.
 */                                          ← Javadoc: dokumentazio ofiziala sortzeko

public class KodeaAdibidea {

    /*
     * This is a multi-line comment
     * spanning across several lines
     * for explanation.
     */                                      ← Lerro anitzekoa: bloke osoak hartzen ditu

    public static void main(String[] args) {
        int x = 10; // Hau iruzkin bat da    ← Lerro bakarrekoa: lerroaren amaierara arte
        int y = 20;
        System.out.println("Hello World!"); /* Another comment */

        // Calculate sum
        int sum = x + y;
        System.out.println("Sum: " + sum);
    }
}
```

| Mota | Sintaxia | Erabilera |
|---|---|---|
| **Lerro bakarrekoa** | `// testua` | Azalpen laburrak, kode ondoan |
| **Lerro anitzekoa** | `/* testua */` | Azalpen luzeak, bloke osoak |
| **Javadoc** | `/** testua */` | Dokumentazio ofiziala sortzeko (`@author`, `@param`...) |

---

## 11. Lan-fluxu Praktikoa: Kode batetik Exekuziora

```
1. Fitxategia Sortu    2. Kodea Idatzi         3. Konpilatu eta        4. Aldatu
                                                  Exekutatu
Sortu Kaixo.java  →   public class Kaixo {  →  javac Kaixo.java    →  Aldatu mezua eta
fitxategia IDE        public static void        java Kaixo              errepikatu
batean                main(String[] args) {     JVM-ak magia egingo     prozesua
                        System.out.println      du eta kontsolan
                        ("Kaixo ikasleak!");    mezua agertuko da
                      }
                    }
```

**Praktikan VS Code-rekin:**

```bash
# Terminal batean
javac Kaixo.java    # Konpilatu
java Kaixo          # Exekutatu
```

---

## 12. Errore Ohikoenak

!!! failure "Fitxategi izena eta klase izena ez datoz bat"
    ```java
    // Fitxategia: Kaixo.java
    public class Agur { ... }   // ❌ Errorea!
    public class Kaixo { ... }  // ✅ Zuzena
    ```
    Konpiladoreak errorea emango du — **lotura arkitektonikoa** apurtzen delako.

!!! failure "main metodotik public hitza kendu"
    ```java
    static void main(String[] args) { ... }   // ❌
    public static void main(String[] args) {  // ✅
    ```
    JVM-ak ezingo luke aurkitu — hasierako atea pribatu bihurtuko litzatekeelako.

!!! failure "Puntu eta koma ahaztu"
    ```java
    System.out.println("Kaixo")    // ❌ ; falta
    System.out.println("Kaixo");   // ✅
    ```

!!! quote ""
    *"Kodea ez da bakarrik idazten — arkitektura bat bezala diseinatzen da."*

---

## Ariketak

!!! question "1. Ariketa — Konpilazioa eta exekuzioa"
    Sortu `KaixoIkasleak.java` fitxategi bat `Kaixo ikasleak!` mezua pantailaratzen duena. Konpilatu eta exekutatu terminaletik.

??? success "Irtenbidea"
    ```java
    public class KaixoIkasleak {
        public static void main(String[] args) {
            System.out.println("Kaixo ikasleak!");
        }
    }
    ```
    ```bash
    javac KaixoIkasleak.java
    java KaixoIkasleak
    ```

!!! question "2. Ariketa — Errore intentzioa"
    Kopiatu lehen ariketa eta aldatu klase izena `Agur`-era, baina fitxategiaren izena `KaixoIkasleak.java` bezala utzi. Zer errorea ematen du konpiladoreak? Zergatik?

??? success "Irtenbidea"
    ```
    error: class Agur is public, should be declared in a file named Agur.java
    ```
    Java-n klase publiko baten izena eta fitxategiaren izena berdinak izan **behar** dira. Hau ez betetzeak konpilazio-errorea sortzen du.

!!! question "3. Ariketa — Iruzkinak"
    Sortu `NirePrograma.java` bat hirurak iruzkina motak erabiliz: lerro bakarrekoa, lerro anitzekoa eta Javadoc iruzkina. Programak zure izena eta ikastetxea pantailaratu behar ditu.

??? success "Irtenbidea"
    ```java
    /**
     * Nire lehen programa Javan.
     * @author IkasleIzena
     */
    public class NirePrograma {

        /*
         * main metodoa: programaren
         * hasierako puntua
         */
        public static void main(String[] args) {
            System.out.println("Izena: Mikel Etxeberria"); // Nire izena
            System.out.println("Ikastetxea: CIFP Txurdinaga");
        }
    }
    ```

!!! question "4. Ariketa — JDK tresnak"
    Erantzun galdera hauei zure hitzetan:

    - Zer da `javac`?
    - Zer da `java`?
    - Zein da ezberdintasuna JDK eta JRE artean?

??? success "Irtenbidea"
    - **`javac`**: Javaren konpiladorea. `.java` fitxategiak hartzen ditu eta `.class` fitxategiak (bytecode) sortzen ditu.
    - **`java`**: JVM-a martxan jartzen duen komandoa. `.class` fitxategiak interpretatzen eta exekutatzen ditu.
    - **JDK vs JRE**: JRE Java aplikazioak exekutatzeko nahikoa da. JDK programatzaileentzat da — JRE barne hartzen du eta gainera konpiladorea (`javac`) eta beste tresnak ditu.

---

## Kontzeptuen Laburpen-Taula

| Kontzeptua | Azalpena |
|---|---|
| Programazio-lengoaia | Gizakiaren eta makinaren arteko zubia |
| Bytecode | Java-ren tarteko kodea — JVM-ak ulertzen duen formatua |
| JVM | Bytecode-a exekutatzen duen makina birtuala |
| JRE | Java aplikazioak exekutatzeko ingurunea |
| JDK | Programatzaileen tresna-kutxa osoa |
| `javac` | Java konpiladorea |
| `java` | JVM exekutatzeko komandoa |
| `public class` | Klase publikoaren definizioa |
| `main` metodoa | Programaren hasierako puntua |
| `System.out.println` | Pantailaratzeko metodoa |

---

*Gai hau 1. DAMeko Programazio moduluaren sarrera teorikoa da — Informatika Sistemen Administrazioa*

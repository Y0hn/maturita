<div align="center">
    <div align="left">
        <a href="/README.md">Domov</a>
        >
        <a href="./PROGRAMOVANIE.md">PRO</a>
    </div>
    <div align="right">
        <a href="../OKRUHY.md#programovanie">Okruhy</a>
        |
        <a href="https://drive.google.com/drive/folders/1-R0QweppWve7l7rt23FboOdxdV9U58OT?usp=sharing">Materály</a>
    </div>

# 🧱 Objektovo orientované programovanie (OOP)
</div>

## 📌 Základné princípy OOP

- **Zapuzdrenie (Encapsulation)** – Skrytie interných detailov objektu, prístup cez metódy (get/set).
- **Dedičnosť (Inheritance)** – Trieda môže zdediť vlastnosti a metódy od inej triedy.
- **Polymorfizmus (Polymorphism)** – Objekt môže mať rôzne formy (napr. prepísanie metódy v dcérskej triede).

---

## 🧩 Základné prvky C#

### 🧱 Trieda, objekt, metóda

- Trieda je šablóna (napr. `class Auto`)
- Objekt je inštancia triedy (napr. `Auto mojeAuto = new Auto();`)
- Metóda je funkcia v triede (napr. `public void Jazdi() { ... }`)

### 📌 Typy metód

- Návratový typ určuje, čo metóda vracia: `void`, `int`, `string`, atď.
- Parametre metódy slúžia na odovzdanie hodnôt metóde:

    ```csharp
    public int Scitaj(int a, int b) { return a + b; }
    ```

### 🧰 get a set

Slúžia na prístup k súkromným premenným:

```csharp
private string meno;
public string Meno {
    get { return meno; }
    set { meno = value; }
}
```

### 🔄 Operátor this

Odkazuje na aktuálnu inštanciu triedy:

```csharp
public void NastavMeno(string meno) {
    this.meno = meno;
}
```

### ⚙️ Preťažovanie vs. prekrývanie

- **Preťažovanie (Overloading)** – rovnaký názov metódy, ale rôzne parametre.
- **Prekrývanie (Overriding)** – prepísanie metódy z rodičovskej triedy pomocou `override`.

---

## 🧮 Premenné a typy

### 📊 Hodnotové vs. referenčné typy

- **Hodnotové:** `int`, `double`, `bool` (ukladajú hodnotu priamo)
- **Referenčné:** `class`, `string`, `object` (ukladajú odkaz na objekt)

### 🔁 Pretypovanie

```csharp
int x = 10;
double y = (double)x; // explicitné pretypovanie
```

### 🔐 Public / Private premenné

- `public` – dostupné z iných tried
- `private` – dostupné iba v rámci tej istej triedy

### 🧷 Konštruktor

Metóda volaná pri vytvorení objektu:

```csharp
public Auto(string model) {
    this.model = model;
}
```

### 📍 Statické premenné/metódy

Nepatria objektu, ale triede:

```csharp
public static int PocetAut = 0;
```

---

## 🛠️ Výnimky

### 🧯 Ošetrenie výnimiek (try-catch)

```csharp
try {
    int a = 5 / 0;
} catch (DivideByZeroException e) {
    Console.WriteLine("Chyba: " + e.Message);
}
```

---

## 🧬 Dedičnosť a polymorfizmus

### 🌳 Dedičnosť

```csharp
class Zviera {
    public void Zvuk() { Console.WriteLine("Zviera vydáva zvuk"); }
}

class Pes : Zviera {
    public void Stekaj() { Console.WriteLine("Haf!"); }
}
```

### 🔄 Polymorfizmus

```csharp
class Zviera {
    public virtual void Zvuk() { Console.WriteLine("Zvuk"); }
}

class Pes : Zviera {
    public override void Zvuk() { Console.WriteLine("Haf!"); }
}
```

---

## 🧱 Abstraktné a finálne triedy

- **Abstraktná trieda** – nemôže byť inštanciovaná, obsahuje abstraktné metódy:

```csharp
abstract class Zviera {
    public abstract void Zvuk();
}
```

- **sealed trieda** – nemožno ju dediť:

```csharp
sealed class MojaTrieda { }
```

---

## 🧩 Interface

Rozhranie definuje zmluvu:

```csharp
interface IPrepravne {
    void Preprav();
}
class Auto : IPrepravne {
    public void Preprav() { Console.WriteLine("Preprava autom"); }
}
```

---

## 🗃️ Polia a kolekcie

### 📦 Statické pole

```csharp
int[] cisla = new int[5];
```

### 📂 Dynamické pole – List

```csharp
List<string> mena = new List<string>();
mena.Add("Ján");
```

### 🧾 Dictionary (kľúč-hodnota)

```csharp
Dictionary<string, int> veky = new Dictionary<string, int>();
veky["Peter"] = 30;
```

---

## 🧮 Základné prvky jazyka C#

### 📌 Premenná, dátový typ, pretypovanie

```csharp
int vek = 25;
double priemer = (double)vek;
```

### 📥📤 Vstup, výstup

```csharp
Console.Write("Zadaj meno: ");
string meno = Console.ReadLine();
Console.WriteLine("Ahoj " + meno);
```

### 🔀 Podmienky

```csharp
if (vek > 18) { ... }
else if (vek == 18) { ... }
else { ... }

switch (den) {
    case 1: Console.WriteLine("Pondelok"); break;
}
```

### 🔁 Cykly

```csharp
for (int i = 0; i < 5; i++) { ... }
while (podmienka) { ... }
do { ... } while (podmienka);
```

### 🧩 Funkcie/metódy

```csharp
public int Scitaj(int a, int b) {
    return a + b;
}
```

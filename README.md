# 🛡️ MD5 Password Cracker - Multithreading & Backtracking

Acest proiect este o aplicație de consolă dezvoltată în **C#** menită să demonstreze eficiența algoritmilor de tip **Backtracking** în combinație cu tehnici de **procesare paralelă** (Multithreading) pentru decriptarea (brute-force) a unor hash-uri MD5.

## 📖 Descriere Proiect
Aplicația simulează un generator de parole care încearcă să identifice textul clar (din 4 litere mici) corespunzător unor semnături MD5 predefinite. Proiectul este împărțit în două etape majore pentru a evidenția diferențele de performanță:

1. **Etapa Secvențială (Single-thread):** Căutarea se face clasic, folosind un singur fir de execuție care procesează fiecare combinație pe rând.
2.  **Etapa Paralelă (Multithreading):** Căutarea este optimizată prin distribuirea spațiului de soluții pe toate nucleele disponibile ale procesorului.

---

## 🚀 Caracteristici Tehnice

### 1. Algoritmul de Backtracking
* Explorează recursiv toate combinațiile posibile din alfabetul "a-z".
* Condiția de oprire este atingerea lungimii de 4 caractere.
* Fiecare iterație verifică dacă hash-ul textului generat coincide cu hash-ul țintă.

### 2. Hashing MD5 (Cerința 1)
* Utilizează biblioteca nativă `System.Security.Cryptography`.
* Convertește textul clar în bytes folosind codificarea ASCII.
* Rezultatul este formatat într-un string hexazecimal de 32 de caractere.

### 3. Administrarea Firelor de Execuție (Cerința 2)
* Folosește `Parallel.ForEach` pentru a împărți alfabetul pe fire de execuție separate.
* Fiecare fir de execuție primește un ID unic (`ManagedThreadId`) pentru monitorizare.
* Execuția este întreruptă imediat ce o soluție este găsită de oricare dintre fire.

---

## 📊 Monitorizarea Performanței
Aplicația utilizează clasa `Stopwatch` pentru a măsura cu precizie timpul necesar găsirii fiecărei parole. Rezultatele afișate în consolă permit utilizatorului să observe direct scalabilitatea și avantajul vitezei în modul multithreading față de cel secvențial.

---

## 📂 Structura Fișierelor
* [cite_start]`Parole_Ivana.txt` / `Proiect.txt`: Conțin codul sursă complet al aplicației, inclusiv logica de backtracking și gestionarea paralelizării.
* **Namespace-uri utilizate:**
    * `System.Security.Cryptography` — pentru funcția hash.
    * `System.Threading.Tasks` — pentru biblioteca TPL (Task Parallel Library).
    * `System.Diagnostics` — pentru profilarea timpului.

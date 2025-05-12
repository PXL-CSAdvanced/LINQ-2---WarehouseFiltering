# LINQ-2---Warehouse Filtering

Een bedrijf heeft magazijnen over heel België. Gebruik LINQ en modelklassen om onderstaande queries uit te voeren.

## Vereiste modelklassen (niet inbegrepen in deze code)

Zorg ervoor dat je twee modelklassen maakt met de volgende properties:

**Warehouse:**

- BuildingName  
- WarehouseID  
- City  
- PostCode  
- Street  
- HouseNumber  
- StorageCapacity (in m²)  
- EmployeeSatisfactionRating (een lijst van scores van 1 tot en met 5)  
  - *Bonus:* Voorzie een setter die controleert of elk getal in de gegeven lijst effectief een score is tussen 1 en 5.

**Employee:**

- FirstName  
- LastName  
- ID  
- WarehouseID

**Let op!** Zorg er voor dat de constructors die in start gegevens staan werken met model classes die je schrijft.

---

## Start gegevens

Gebruik onderstaande code om data in te laden in je programma:

```csharp
List<Warehouse> warehouses = new List<Warehouse>
{
    new Warehouse("Brug4", 0, "Arendonk", 2370, "Holstraat", 14, 3000, new List<int>{ 4, 3, 1, 5 }),
    new Warehouse("Brug1", 1, "Arendonk", 2370, "Holstraat", 3, 8000, new List<int>{ 1, 4, 3, 5, 2, 3, 3, 4, 4}),
    new Warehouse("Poort1", 2, "Gent", 9000, "Stropkaai", 12, 7000, new List<int>{ 5, 4, 3, 4 , 4}),
    new Warehouse("Rijsteller", 3, "Hasselt", 3500, "Industrielaan", 1, 2500, new List<int>{ 5, 4, 3, 5, 2, 3, 4, 4}),
    new Warehouse("Automa klein", 4, "Berchem", 2600, "Nieuwevaart", 77, 10000, new List<int>{ 4 }),
    new Warehouse("Schuifla", 5, "Hasselt", 3500, "Industrielaan", 15, 1500, new List<int>{ 3, 5, 2 }),
    new Warehouse("Automa groot", 6, "Berchem", 2600, "Nieuwevaart", 76, 30000, new List<int>{ 5 }),
    new Warehouse("Brug2", 7, "Arendonk", 2370, "Molenweg", 7, 3000, new List<int>{ 4, 3, 5, 2 }),
    new Warehouse("Veerhal", 8, "Melle", 9090, "Merelstraat", 48, 500, new List<int>{ 5, 5 }),
    new Warehouse("Poort2", 9, "Gent", 9000, "Burgstraat", 113, 6600, new List<int>{ 1, 2, 1, 1, 2, 3}),
    new Warehouse("D1", 10, "Knokke", 8300, "Vaart", 2, 2200, new List<int>{ 5, 4, 1 }),
    new Warehouse("Brug3", 11, "Arendonk", 2370, "Molenweg", 8, 8000, new List<int>{ 5, 2, 3, 5, 5 }),
    new Warehouse("D2", 12, "Knokke", 8300, "Vaart", 4, 2200, new List<int>{ 2, 3, 4 }),
    new Warehouse("D3", 13, "Knokke", 8300, "Vaart", 6, 2200, new List<int>{ 3, 4, 3 })
};

List<Employee> employees = new List<Employee>
{
    new Employee("Jos", "Jansen", 0, 1),
    new Employee("Ted", "Bériault", 1, 0),
    new Employee("Tony", "Hawk", 2, 3),
    new Employee("Peggy", "Corona", 3, 12),
    new Employee("Edna", "Goosen", 4, 0),
    new Employee("Mac", "Kowalski", 5, 11),
    new Employee("Alejandro", "Mendoza", 6, 8),
    new Employee("Aysha", "Lyon", 7, 7),
    new Employee("Tyson", "Dyer", 8, 4),
    new Employee("Nanou", "Hahn", 9, 6),
    new Employee("Kevin", "Hahn", 10, 5),
    new Employee("Kris", "Jacobsen", 11, 1),
    new Employee("Boros", "Orzsebet", 12, 2),
    new Employee("Buday", "Gedeon", 13, 2),
    new Employee("Szölôsi", "Taksony", 14, 1),
    new Employee("Kocsis", "Gyula", 15, 8),
    new Employee("Asif", "Atiyeh", 16, 7),
    new Employee("Ruwayd", "Akram", 17, 13),
    new Employee("Makary", "Sobczak", 18, 12),
    new Employee("Pawel", "Symanski", 19, 1),
    new Employee("Settimio", "Calabresi", 20, 10),
    new Employee("Ivo", "Bellucci", 21, 7),
    new Employee("Matthieu", "Camus", 22, 9),
    new Employee("Jacques", "Huard", 23, 8),
    new Employee("Melville", "Bériault", 24, 4),
    new Employee("René", "Michaud", 25, 9)
};
```

---

## LINQ Queries
Los onderstaande vragen op met LINQ.
1. Wat zijn de namen van de magazijnen in Berchem?
2. Wat zijn de namen en steden van alle magazijnen, geordend van hoog naar laag op het aantal ratings van hun werknemers?
3. Wat zijn de volledige namen en ID’s van alle werknemers, alfabetisch geordend op hun achternaam (A-Z)?
4. Rangschik alle magazijnen van hoog naar laag op basis van gemiddelde rating van werknemerstevredenheid.
5. Wat zijn de magazijnen met postcode onder 4000, gegroepeerd per stad?
6. Wat zijn de volledige namen van werknemers die werken in een magazijn met een opslagcapaciteit groter dan 2000 m²? Vermeld ook de naam en capaciteit van het magazijn.
7. Wat zijn de ID’s en voornamen van werknemers die een achternaam delen met een andere werknemer uit hetzelfde magazijn?
8. Wat zijn de voornamen van werknemers die werken in een magazijn met een opslagcapaciteit groter dan 5000 m²? Vermeld ook de volledige locatie (stad, postcode, straat, huisnummer) van het magazijn.
9. Groepeer de werknemers per straat van het magazijn waarin ze werken.
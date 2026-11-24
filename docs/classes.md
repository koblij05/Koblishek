# Classes

## Catalog

Katalog koblih.

Atributy:
- donuts: Donut[]

Metody:
- getDonuts(): Donut[]
- getDonut(id: number): Donut | null

## Donut

Produkt v katalogu.

Atributy:
- id: number
- name: string
- description: string
- price: number

Metody:
- getPrice(): number

## CartItem

Jedna kobliha s vlastní konfigurací.

Atributy:
- id: number
- donut: Donut
- filling: string
- topping: string

Metody:
- customize(filling: string, topping: string): void
- getPrice(): number

## Cart

Nákupní košík.

Atributy:
- items: CartItem[]

Metody:
- addItem(item: CartItem): void
- removeItem(id: number): void
- getItems(): CartItem[]
- getTotal(): number
- createOrder(customerName: string, deliveryAddress: string): Order

## Order

Vytvořená objednávka.

Atributy:
- id: number
- customerName: string
- deliveryAddress: string
- items: CartItem[]
- total: number

Metody:
- getTotal(): number

## Vztahy

- Catalog obsahuje 0..* Donut.
- CartItem odkazuje na 1 Donut.
- Cart obsahuje 0..* CartItem.
- Order obsahuje 1..* CartItem (kopie položek).
- Cart vytváří Order.

## Funkcionality

| Požadavek | Třída a metoda |
|---|---|
| FR01 - nabídka koblih | Catalog.getDonuts() |
| FR02 - detail koblihy | Catalog.getDonut() |
| FR03 - personalizace | CartItem.customize() |
| FR04 - přidání do košíku | Cart.addItem() |
| FR05 - zobrazení košíku | Cart.getItems(), Cart.getTotal() |
| FR06 - odebrání z košíku | Cart.removeItem() |
| FR07 - vytvoření objednávky | Cart.createOrder() |

## Pravidla

- Každá položka košíku představuje jednu koblihu.
- Personalizace nemění cenu koblihy.
- Objednávka vyžaduje neprázdný košík, jméno a doručovací adresu.
- Objednávka uchovává kopie položek a celkovou cenu.
- Po úspěšném vytvoření objednávky se košík vyprázdní.

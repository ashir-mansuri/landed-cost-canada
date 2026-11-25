# Landed Cost Canada

A web app that works out what imported goods really cost once they reach a warehouse in Canada, and compares suppliers on more than price.

**Live app:** https://ashir-mansuri.github.io/landed-cost-canada/

## The problem

The supplier with the lowest unit price is often not the cheapest once freight, insurance, port charges, customs brokerage and duty are added. Quotes also come on different Incoterms (FOB, CIF, DAP, DDP and so on), so some include freight and others don't. Comparing them side by side by hand is slow and easy to get wrong. Tariff changes and exchange-rate swings make it harder still.

## What it does

- Converts each quote to Canadian dollars and works out the **full landed cost**, per order and per unit.
- Reads the **Incoterm** on each quote to decide which costs are already in the supplier's price and which ones the buyer pays.
- Calculates the **value for duty** the way the Canada Border Services Agency (CBSA) does: transport after the goods leave for Canada is taken out of the duty base.
- Applies **duty, surtax or counter-tariffs, and GST**. GST can be left out because registered businesses usually recover it.
- Scores each supplier on **landed cost, quality, delivery reliability, lead time, supply risk and CO₂**, using weights the buyer sets.
- Shows the **route from supplier to warehouse**, with the cost added at each stage.
- Runs an **exchange-rate scenario** to show how costs change if the Canadian dollar weakens or strengthens.
- Pulls **today's exchange rates** from the Bank of Canada, with the European Central Bank as a backup.
- Exports a **CSV** for Excel and prints a **clean report** to take to a purchasing meeting.

## Example: sample comparison

5,000 deep-groove ball bearings delivered to Toronto, with four quotes (illustrative figures):

| Supplier | Incoterm | Landed per unit | Lead time | Overall score |
|---|---|---|---|---|
| Ningbo Motion Parts, China | CIF | CA$2.73 | 38 days | 66 |
| Gujarat Precision Bearings, India | FOB | CA$3.47 | 42 days | 65 |
| Monterrey Rodamientos, Mexico | DAP | CA$3.65 | 9 days | **77** |
| Hamburg Bearings GmbH, Germany | FCA | CA$4.53 | 28 days | 71 |

China is the cheapest landed. Mexico wins overall because of its short lead time, strong reliability and lower supply risk. Germany has the best quality and the lowest CO₂. Cheapest is not always best, and the tool shows why.

## How the numbers work

- **Value for duty** = supplier price in CA$ + costs to the place of export − freight, insurance and delivery after that point when the price includes them.
- **Duty** = value for duty × duty rate, plus any surtax at the same base.
- **GST** = 5% × (value for duty + duty + surtax).
- **Landed cost** = supplier price + charges the buyer pays under the Incoterm + duty + surtax (+ GST if chosen).
- **CO₂** = tonnes × km × typical factor (sea 0.016, rail 0.026, truck 0.11, air 0.65 kg CO₂e per tonne-km, rounded from UK government conversion factors).
- **Scores**: cost, lead time and CO₂ are scored against the best supplier (best = 10). Quality, reliability and risk are the buyer's own 1 to 10 ratings. The overall score is the weighted average, out of 100.

## Built with

Plain HTML, CSS and JavaScript in a single file. No frameworks and no server: everything runs in the browser and data stays on the user's device.

## Sources

- CBSA, [Importing commercial goods: determining duties and taxes](https://www.cbsa-asfc.gc.ca/import/guide-3-eng.html)
- CBSA, [Memorandum D13-3-5: transportation costs and value for duty](https://www.cbsa-asfc.gc.ca/publications/dm-md/d13/d13-3-5-eng.html)
- CBSA, [Customs Tariff](https://www.cbsa-asfc.gc.ca/trade-commerce/tariff-tarif/)
- Government of Canada, [Canada Tariff Finder](https://www.tariffinder.ca/)
- UK Government, greenhouse gas conversion factors for company reporting

## About

Built by Ashir Mansuri. MS in Global Supply Chain Management (CBS International Business School, Germany), with experience in warehouse operations in Hamburg and procurement at SKF.

## License

Released under the [MIT License](LICENSE). You're free to use and adapt it, as long as the copyright notice stays with it.

*Planning estimates only. Confirm tariff classification, duty rates and taxes with CBSA or a licensed customs broker before buying.*

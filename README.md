# Zadání cvičení na Slicing

Před odevzdáním úlohy přes GitHub je třeba
[projevit souhlas se zpracováním osobních údajů](https://courses.fit.cvut.cz/BI-3DT/cs/gdpr.html).

Vaším dnešním úkolem bude naslicovat několik modelů v aplikaci Slic3r.
Abyste ale nezačínali s prázdnou, máme pro vás jako config bundle,
který si importujte do Slic3ru pomocí volby _Load Config Bundle_.

- [slic3r_config_bundle.ini](https://github.com/3DprintFIT/BI-3DT/blob/master/configs/printing/slic3r_config_bundle.ini)

\*\*Repozitář vytvořte na odkazu https://classroom.github.com/a/pkFhV4OT
Do vašeho vytvořeného repozitáře odevzdáte soubory `bulbasaur.gcode`,
`vader_cup_v03.gcode`, `bottle_opener.gcode`,
`cube.gcode`, `z_bottom.gcode` a `koch_snowflake.gcode`.
Doporučujeme si jednotlivé configurace Slic3eru ukládat.

## Hodnocení

- Naslicování všech šesti modelů (max. 3 body)
- Úloha nesplňuje zadání (0 bodů)

**Musíte použít Slic3r 1.3.0.** Nepoužívejte starší verzi Slic3ru
ani různé další varianty Slic3ru (Prusa Edition apod.).

## Rady

Tiskárnu mějte nastavenou Hybrix a filament PET z config bundlu.
V tisku vycházejte z profilu Normal.
Po jednotlivých vygenerováních gcodu prozkoumejte výstup jednotlivých nastavení
v panelu _Preview_ (dole ve Slic3ru).

## Modely

Před každou dílčí úlohou se **vraťte na výchozí konfiguraci**, opětovné _Load Config Bundle_, nebude fungovat tak jak očekáváte, je potřeba buď Slic3r zavřít a znovu otevřít, nebo uložit aktualní změny v změněné konfiguraci pomocí ikony diskety jako nový konfig. A poté používat ten originální, pro další úlohu.

### Bulbasaur

První z modelů je [bulbasaur.stl](bulbasaur.stl)
(CC BY-NC-SA 3.0 [FLOWALISTIK](https://www.thingiverse.com/thing:327753)) s parametry

- Materiál PETG
- 5 perimetrů vertikálního shellu, 4 plné dolní vrstvy a 3 horní
- Rychlost tisku vnějších perimetrů je 245 mm/s
- Brim tloušťky 3mm, Outer brim only
- Infill typu Gyroid s hustotou 15 %
- Teplota Bedu je při první vrstvě 79°C

![bulbasaur.png](bulbasaur.png)

### Bottle opener

Nechcete pořád tisknout jen figurky, ale také něco praktického
a to otvírák na pivo – [bottle_opener](bottle_opener.stl)
(CC BY-SA 3.0 [leemes](https://www.thingiverse.com/thing:132632))

- 30% infill se vzorem 3D Honeycombu
- 3mm (exterior) brim
- Infill se tiskne s rychlostí 240 mm/s
- Prvních 5 vrstev nemá žádné chlazení
- Zpomalte tisk, pokud je doba výtisku jedné vrstvy menší než 6 s
  - (hint: je to proto, aby **plast** měl čas **vychladnout**)
- Větráček bude permanentně zaplý s minimální rychlostí 10 %
- Během retrakce by se tisková hlava měla zvednout o 2 mm (Z-hop), když se přejíždí prázdným místem
  - (hint: nastavení Z-hop je specifické pro **extruder**)

![bottle_opener.png](bottle_opener.png)

Teď, když už máte prozkoušené úlohy s přesnými parametry,
tak si vyzkoušíte i varianty bez nich,
které by se vám v životě 3D tiskaře mohly hodit.

### Kostičky

Kamarád chce vytisknout čtyři kostičky z ABS. Všechny s tenkou stěnou,
infill ten co má na sebe kolmé čáry, hustota 10 %,
výplň rovnoběžná s hranami kostky. Jeden perimetr a po jedné stěně nahoře i dole.
Kamarád je ale neskutečně nedočkavý a chce, aby se mu kostičky tiskly jedna po druhé, ne všechny najednou.
Model jedné kostičky kamarád zvládnul vytvořit.

Kostičkami je zakázáno otáčet, protože kamarád má iracionální strach z kosočtverců.

- Model: [cube.stl](cube.stl)

![cube](cube.png)

### Náhradní díl k tiskárně

Na vaší 3D tiskárně Voron napraskl díl držící Z motor.
Máte k dispozici pouze STL, kde jsou oba držáky motorů vedle sebe,
a chcete vytisknout pouze jeden. Měl by mít pevnost takovou, jako udává [dokumentace Voron](https://docs.vorondesign.com/sourcing.html#print-settings). Udávají několik možností výplně, ale vy víte, že máte pouze 19 minut na tisk. Rozhodnete se proto použít výšší výšku vrstvy. Použijte nejnižší možnou výšku vrstvy, která vám umožní vytisknout díl do 19 minut. Na druhu infillu nezáleží, ale doporučujeme Cubic.

Dokumentace Voron doporučuje filament ABS, takže vyberte profil ABS @Voron.

Tip: Používejte inkrement výšky vrstvy 0.05 mm, začněte na 0.2 mm a zvyšujte, dokud se vám nepodaří dostat na vhodný čas tisku. Nemůžete mít vyšší výšku vrstvy než 0.4 mm, protože máte trysku s průměrem 0.4 mm.

- Model: [T8_Nut_Block.stl](https://github.com/VoronDesign/Voron-0/blob/a53fc87562fd630c846af38d7de850c894dc3d85/STLs/T8_Nut_Block_x1.stl)

![T8_Nut_Block.png](T8_Nut_Block.png)

### Fraktálová váza

Předvádíte 3D tisk na konferenci okrasných indoor zahradníků se zálibou v matematice
a rozhodli jste se vytisknout vázu definovanou fraktálem.
Protože STL soubor je však vytvořen jako plný blok (pro představu si ho prohlédněte),
musíte vhodným nastavením docílit toho, aby se váza vytiskla dutá, s dírou nahoře.
(Neupravujte mesh v editoru, výsledku dosáhnete pouze správným nastavením OrcaSliceru!)
Protože chcete tisknout rychle, ale vodotěsně,
rozhodli jste se použít metodu tisku do spirály.

- Model: [koch_snowflake.stl](koch_snowflake.stl)

![koch_snowflake.png](koch_snowflake.png)

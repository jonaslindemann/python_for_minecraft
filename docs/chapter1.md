# Koda i Minecraft

## Vad är programmering

En dator är uppbyggd kring ett antal delar som samarbetar för att du ska kunna använda program, spela spel och titta på bilder. Den viktigaste delen är processorn eller central processing unit (CPU). Processorn är expert på att utföra instruktioner, som t ex beräkna summan av 2+2, fyll minnet med text eller rita linjer på skärmen. Den andra viktiga delen i datorn är minnet. Minnet används för att lagra de instruktioner som ska utföras av processorn samt information som används för att visa text, grafik och video på skärmen. Ett antal av dessa instruktioner som tillsammans utför en uppgift kallar man ett program eller en applikation. 

De instruktioner som processorn utför kallas för maskininstruktioner och är mycket komplicerade att skriva. För att göra det enklare använder man istället någon form av programmeringsspråk, som använder instruktioner som är enklare för oss att skriva och förstå. Dessa instruktioner översätts med hjälp av ett speciellt program som kallas kompilator eller översättare till maskininstruktioner.
 
Instruktioner skrivna i ett programmeringsspråk kallas tillsammans för programkod eller källkod. Programkoden skrivs ofta i en texteditor eller en speciell utvecklingsmiljö som kopplar ihop en texteditor med en kompilator.
 
För att få datorn att göra något använder vi oss av något som kallas funktioner eller kommandon. Dessa talar om för datorn vad vi vill göra. Ett typiskt kommando eller funktion i Python består av 2 delar, funktionsnamnet och indata till funktionen (...). Följande exempel visar hur vi kan skicka ett meddelande till chatt-fönstret i Minecraft.
 
	minecraft.postToChat("Hejsan Minecraft!")

**minecraft.postToChat** är funktionsnamnet, **("Hejsan Minecraft!")** är indata till kommandot. 

Genom att sätta ihop flera instruktioner talar man om för datorn hur den ska utföra en uppgift på samma sätt som instruktionerna i recepten i kokboken. I nästa exempel lägger vill 2 kommandon till. Ett kommando, **sleep(5)**, anger att programmet ska vänta i 5 sekunder och ett kommando som skriver ut "Hej igen!" i chatt-fönstret:

	minecraft.postToChat("Hejsan Minecraft!")
	sleep(5)
	minecraft.postToChat("Hej igen!")

Kör man programmet igen kommer följande upp i Minecraft:

![](a_first_example.png)

## Anpassa Minecraft

För att det ska bli lättare att programmera med Minecraft kan det vara bra att stänga av funktionen i Minecraft som pausar programmet när man byter program i Windows. Detta görs genom att trycka på **F3 + P**. När detta är gjort tryck en kort gång på **F3** för att ta bort informationstexten. Tryck **F3 + P** igen för att återställa Minecraft inställningen igen.

Många egenskaper i Minecraft går att styra ifrån chattfönstret. Detta fönster öppnas genom att trycka på T. Några bra kommandon man kan skriva i detta är:

 - **/time set day** - Återställer tiden till morgon (10:00)
 - **/weather clear** - Fint väder 
 

## Mitt första Minecraft program

Vi ska nu skapa vårt första Minecraft program i Python. Skapa en ny Python-fil i IDLE eller i Python för Minecraft Editorn. 

Det första vi måste göra i vårt program är att tala om för Python att vi behöver kommandon för att prata med Minecraft, samt kommandon för att kunna göra pauser i programkörningen. Skriv in följande rader i editorn. 

	from mc import *
	from time import *

I nästa steg skapar vi kopplingen till Minecraft. 

	minecraft = Minecraft()

Detta gör att vi får tillgång till Minecraft genom en objektet, minecraft. minecraft-objektet innehåller alla de kommandon som behövs för att styra Minecraft, t ex genom att lägga till följande kommandon:

	minecraft.postToChat("Hejsan Minecraft!")
	sleep(5)
	minecraft.postToChat("Hej igen!")
 
Det kompletta programmet ser ut så här:

	from mc import *
	from time import *
	
	minecraft = Minecraft() 
	
	minecraft.postToChat("Hejsan Minecraft!")
	sleep(5)
	minecraft.postToChat("Hej igen!")


----------
### Övning 1

Modifiera programmet så att det skriver ut fler meddelanden i chattfönstret. Vad händer om man ändrar siffran i sleep(..) kommandot?

----------

## Var är jag någonstans?

Om vi skall bygga och skapa saker i Minecraft kan det vara bra att veta var man är någonstans. I Minecraft bestäms detta av ett så kallat koordinatsystem med 3 axlar, X, Y och Z. Det går att se var man befinner sig i detta koordinatsystem genom att trycka på **F3**.  

![](player_position.png)

XYZ: anger var spelaren befinner sig i världen. I bilden befinner sig spelare i position (X = -310, Y =  4, Z = 478). X och Z anger var spelaren befinner sig längs marken. Y anger på vilken höjd spelaren befinner sig.

I programkoden kan man ta reda på spelarens position med följande kommando:

	pos = minecraft.player.getTilePos()

Kommandot minecraft.player.getTilePos frågar Minecraft var spelaren befinner sig för tillfället. Vi får tillbaka en s.k. variabel, **pos** som innehåller spelarens position. 

> **Variabler** - I början av denna text pratade vi om hur datorn lagrar program och information i minnet. I program behöver vi också ofta lagra information, som t ex siffror, text och grafik i minnet för att kunna hämta tillbaka det när vi behöver det. I de tidigare exemplen har vi angett siffror direkt till funktionerna. Många gånger har vi också angett samma siffra många gånger. För att förenkla hanteringen av information i program använder man sig av variabler. Variabler kan liknas vid en låda i en byrålåda med en etikett på. I lådan kan vi lägga olika saker. Etiketten gör det lätt att hitta sakerna i lådan igen. I datorns värld anger en variabel en plats i minnet. Namnet på variabeln är etiketten som gör att vi kan hitta tillbaka till denna minnesplats igen.

**pos** innehåller spelarens X, Y och Z position i förhållande till den position man startade i världen. Vi kan skriva ut innehållet i dessa till chattfönstret med följande kommandon:

	minecraft.postToChat(pos.x)
	minecraft.postToChat(pos.y)
	minecraft.postToChat(pos.z)

I Minecraft visas då 

![](player_position_chat.png)

i chattfönstret. 20 är vår position i x-led, 0 är positionen i y-led och 15 är vår position i z-led.

Det kompletta programmet visas i följande listning:

	from mc import *
	
	minecraft = Minecraft()
	
	pos = minecraft.player.getTilePos()
	
	minecraft.postToChat(pos.x)
	minecraft.postToChat(pos.y)
	minecraft.postToChat(pos.z)
    
----------
### Övning 2

Prova att gå till olika ställen i Minecraft för att se hur det påverkar X, Y och Z värdena i **pos** variabeln.

----------

Vi kan skriva ut spelarens position på ett mer elegant sätt genom att ändra de tre tidigare kommandona till ett enda kommando:
 
	minecraft.postToChat("x = " + str(pos.x) + ", y = " + str(pos.y) + ", z = " + str(pos.z))

I det ovanstående kommadot använder vi + för att slå ihop flera texter. str(...) översätter siffror till text.

## Enkel upprepning

Många gånger när man skriver program måste man upprepa kommandon många gånger. För att göra det enklare kan vi instruera datorn att hela tiden upprepa vissa kommandon. Detta kallas ofta för att man skapar loopar. Vi skall nu modifiera vårt program att med jämna mellanrum skriva ut spelarens position i chattfönstret. I exemplet skall vi använda en s.k. while-sats. Denna upprepar kommandon tills dess att ett visst villkor inte är uppfyllt längre. Vi skriver in följande:

	while True:
	    sleep(1)
	    pos = minecraft.player.getTilePos()
	    minecraft.postToChat("x = %g, y = %g, z = %g" % (pos.x, pos.y, pos.z))

Kommandon som skall upprepas måste vara indragna i förhållande till while-satsen. While-satsen måste också avslutas med ett : för att indikera var de upprepade kommandona börjar. **sleep(1)** anger att programkörningen skall pausa i 1 sekund. Övriga kommandon tar reda på spelarens position och skriver ut denna i chattfönstret. Om allt fungerar visas följande i chattfönstret:

![](while_loop.png)

Tänk på att detta program aldrig stannar, så att vi måste trycka på stopp-knappen i editorn eller Ctrl-C i IDLE.

Det kompletta programmet visas i följande listning:

	from mc import *
	from time import *
	
	minecraft = Minecraft()
	
	while True:
	    sleep(1)
	    pos = minecraft.player.getTilePos()
	    minecraft.postToChat("x = %g, y = %g, z = %g" % (pos.x, pos.y, pos.z))

## Skapa block

Block skapas Minecraft med kommandot **setBlock(..)** Indata till kommandot är positionen in X, Y och Z samt blockets id. För att sätta ut ett stenblock anger man följande kommando:

	pos = minecraft.player.getTilePos()

	minecraft.setBlock(pos.x+3, pos.y, pos.z, STONE.id)

Detta sätter ut ett block av typen STONE.id 3 block från spelaren i X-led och på samma höjd som spelaren. Vi kan nu skapa fler block genom att lägga till fler kommandon:

	pos = minecraft.player.getTilePos()
	
	minecraft.setBlock(pos.x+3, pos.y, pos.z, STONE.id)
	minecraft.setBlock(pos.x+3, pos.y+1, pos.z, COBBLESTONE.id)
	minecraft.setBlock(pos.x+3, pos.y, pos.z+1, WOOD_PLANKS.id)
	minecraft.setBlock(pos.x+3, pos.y+1, pos.z+1, GOLD_ORE.id)

![](creating_blocks_1.png)

Man kan använda bläddraren i editorn för att klistra in block i koden. Välj ett block i lista n och klicka sedan **Lägg till** enligt följande figur:

![](blocks_in_editor.png)

Det går att skapa många block på en gång genom att använda kommandot **setBlocks**. I detta kommando kan man ange start och slut position mellan vilka blocken skall placeras. I följande kommandon sätter vi ut lövblock från (X + 10, Y, Z + 10) - (X + 20, Y + 4, Z + 20):

	pos = minecraft.player.getTilePos()
	
	minecraft.setBlocks(pos.x + 10, pos.y, pos.z + 10, pos.x + 20, pos.y + 4, pos.z + 20, LEAVES.id)

![](creating_blocks_2.png)

Det går också att sätta ut luftblock AIR.id och vatten block, WATER.id, på detta sätt. I följande exempel bygger vi ett akvarie genom att först skapa block av glas och sedan fylla den inre delen av detta block med vatten:

	pos = minecraft.player.getTilePos()
	
	minecraft.setBlocks(pos.x - 20, pos.y, pos.z - 20, pos.x - 10, pos.y + 6, pos.z - 10, GLASS.id)
	minecraft.setBlocks(pos.x - 19, pos.y + 1, pos.z -19, pos.x - 11, pos.y + 5, pos.z -11, WATER.id)

![](creating_blocks_3.png)

Att det är vatten kan vi se om vi slår i sönder ett av fönsterblocken:

![](spilling_water.png)

----------
### Övning 3

Prova att skapa ett hus av sten eller något annat material och sedan gröpa ur det genom att skapa luftblock inuti.

----------

## Använda sköldpaddsgrafik (turtle) i Minecraft

För att göra det lättare att skapa och ta bort block kan man använda en s.k. sköldpadda med en 3D penna för att skapa block eller ta bort block. Tunnlar i Minecraft kan vara jobbiga att göra för hand. Med hjälp av sköldpaddan kan vi snabbt och enkelt borra hål i vår värld precis som när man skapar riktiga tunnlar. Följande exempel visar hur vi gräver en 5 block bred tunnnel ner i marken och sedan upp igen:

	from mc import *
	from mcturtle import *
	
	minecraft = Minecraft()
	
	turtle = Turtle()
	
	turtle.pendelay(0)         # Anger hur om uppritningen skall ske långsamt eller snabbt 
	material = AIR             # Variabel för materialet som skall användas
	turtle.penwidth(5)         # Tjocklek på "pennan"
	turtle.penblock(material)  # Sätt pennans material
	turtle.pendown()           # Börja gräva
	turtle.down(45)            # 45 grader nedåt
	turtle.go(20)              # 20 block framåt
	turtle.up(45)              # 45 grader uppåt
	turtle.go(20)              # 20 block framåt
	turtle.up(45)              # upp 45 grader
	turtle.go(20)              # 20 block framåt
	turtle.penup()             # Avsluta ritandet

Om programmet körs skapas nu en tunnel ner i marken:

![](turtle_1.png)

Påväg ner i tunneln.

![](turtle_2.png)

Nere i tunneln. Lamporna är tillagda i efterhand.

![](turtle_3.png)

Påväg upp.

![](turtle_4.png)

I det tidigare exemplet använde vi tomma block, AIR.id, för att skapa tunnlar. Vi kan också skapa strukturer med sköldpaddan. I följande exempel skapar vi en skulptur av GOLD_BLOCK.id.

	from mc import *
	from mcturtle import *
	
	minecraft = Minecraft()
	
	turtle = Turtle()
	
	turtle.pendelay(0)
	material = GOLD_BLOCK.id
	turtle.penwidth(2)
	turtle.penblock(material)
	turtle.pendown()
	turtle.up(90)
	turtle.go(20)
	turtle.down(90)
	turtle.go(20)sw
	turtle.left(90)
	turtle.go(20)
	turtle.up(90)
	turtle.go(20)
	turtle.penup()

Kör vi detta program får vi följande vackra struktur:

![](turtle_5.png)

## Att göra saker ett visst antal gånger (for-loopar)

Om man i Python vill upprepa något bara ett visst antal gånger kan vi använda en for-loop. Följande exempel skriver ut texten "Det är kul med Minecraft." 10 ggr i chatfönstret:

	# -*- coding: utf-8 -*-
	
	from mc import *
	
	minecraft = Minecraft() 
	
	for i in range(10):
	    minecraft.postToChat("Det är kul med Minecraft.")

Den första raden i exemplet säger till Python att vi vill kunna använda svenska tecken i utskriften.

![](for_loop1.png)

En for-loop kan vi också använda för att sätta ut flera block:

	from mc import *
	
	minecraft = Minecraft() 
	
	pos = minecraft.player.getTilePos()
	
	for i in range(10):
	    minecraft.setBlock(pos.x, pos.y, pos.z + i, STONE.id)

![](for_loop2.png)

i är en variabel som innehåller ett värde som kan användas att ändra positionen på blocken i loopen. I exemplet kommer i att gå från 0 till 9. Alltså kommer programmet att sätta ut block från spelarens z-koordinat till spelarens z-koordinat + 9 block.

----------
### Övning 4

Vad händer om man lägger till i för spelarens x-koordinat samtidigt?

	for i in range(10):
	    minecraft.setBlock(pos.x, pos.y, pos.z + i, STONE.id)

Prova också att lägga till i för spelarens y-koordinat.

----------

## flera for-loopar samtidigt

Vill man placera ut block i flera rader måste man använda 2 st for-loopar på följande sätt:

	from mc import *
	
	minecraft = Minecraft() 
	
	pos = minecraft.player.getTilePos()
	
	for i in range(10):
	    for j in range(20):
			
	        minecraft.setBlock(pos.x + i, pos.y, pos.z + j, WOOD_PLANKS.id)

![](for_loop3.png)

----------
### Övning 5

Skriv ut variablerna i och j i chat-fönstret för att se vad som händer i koden.

	for i in range(10):
	    for j in range(20):
	        minecraft.postToChat("i = "+str(i)+", j = "+str(j))
	        minecraft.setBlock(pos.x + i, pos.y, pos.z + j, WOOD_PLANKS.id)

Funktionen str(i) omvandlar värdet i variabeln i till en text, så att denna kan skrivas ut i chat-fönstret.

----------
### Övning 6

Vad gör denna kod?

	for i in range(10):
	    for j in range(20):
	        for k in range(30):
	            minecraft.postToChat("i = "+str(i)+", j = "+str(j))
	            minecraft.setBlock(pos.x + i, pos.y + k, pos.z + j, BRICK_BLOCK.id)

![](for_loop4.png)

----------

Det går också att hoppa över steg när man kör en loop.

----------
### Övning 7

Vad gör denna kod?

	for i in range(0,10,2):
	    for j in range(0,20,2):
	        for k in range(0,30,2):
	            minecraft.setBlock(pos.x + i, pos.y + k, pos.z + j, GLOWING_OBSIDIAN.id)
    

![](for_loop5.png)

Vad händer om man ändrar siffran 2 i range till ett högre värde?

## Att göra egna kommandon

När man börjar skriva större program märker man snart att man skriver samma kod flera gånger. För att slippa detta kan man flytta denna kod till egna kommandon som anropas precis som de kommandon vi redan lärt oss.

För att visa hur detta kan fungera skall vi nu göra en funktion som skapar ett litet hus med vissa mått och egenskaper.

Indata till funktionen kommer att vara:

- minecraft - objektet vi använder för att prata med Minecraft. Funktionen ser inte de variabler som vi använder i resten av programmet.
- x, y, z - Koordinater som anger var huset skall börja.
- b, h, d - Anger bredd, höjd och djup i block för huset
- vaggBlock - Anger block som skall användas för väggen
- golvbBlock - Anger block som skall användas för golvet
- takBlock - Anger block som skall användas för husets tak

Funktioner eller kommandon skapas med Python-kommandot **def**, följt av funktionens namn och därefter indata till funktionen. Vi definierar vår hus funktion längs upp i vårt program:

	# -*- coding: utf-8 -*-

	from mc import *

	def hus(minecraft, x, y, z, b, h, d, vaggBlock, golvBlock, takBlock):
	    minecraft.setBlocks(x, y, z, x + b, y, z + d, golvBlock)
	    minecraft.setBlocks(x, y + 1, z, x + b, y + h, z + d, vaggBlock)
	    minecraft.setBlocks(x + 1, y + 1, z + 1, x + b - 1, y + h, z + d - 1, AIR.id)
	    minecraft.setBlocks(x, y + h + 1, z, x + b, y + h + 1, z + d, takBlock)

Vi skapar sedan på vanligt sätt kopplingen till Minecraft och därefter spelarens position.

	minecraft = Minecraft() 
	
	pos = minecraft.player.getTilePos()

Nu har vi all information som behövs för att anropa vårt eget kommando eller funktion.
	
	hus(minecraft, pos.x + 5, pos.y, pos.z + 5, 15, 4, 10, BRICK_BLOCK.id, STONE_BRICK.id, STONE_SLAB.id)

Kör vi vårt program nu skapas ett hus utan fönster:

![](hus.png)

----------
### Övning 8

Lägg till följande kod i funktionen, hus, för att skapa fönster på ena sidan av huset:

    for xp in range(x+2, x+b, 2):
        minecraft.setBlock(xp, y + h/2, z, GLASS_PANE.id)
        minecraft.setBlock(xp, y + 1 + h/2, z, GLASS_PANE.id)

Skapa på samma sätt fönster på motstående sida av huset (z+d). Skapa också fönster i z-led:

	for zp in range( ... fyll i ... ):
        minecraft.setBlock(??, ??, ??, GLASS_PANE.id)
		...
		
----------

![](hus2.png)

När vi nu har vår hus-funktion är det jätteenkelt att skapa ett höghus. Vi kombinerar då en for-loop med anrop till vår funktion:

	for i in range(10):
	    hus(minecraft, pos.x + 5, pos.y + i*5, pos.z + 5, 15, 4, 10, BRICK_BLOCK.id, STONE_BRICK.id, STONE_SLAB.id)

![](hus3.png)
	
----------
### Övning 9

Skriv en ny funktion, hoghus, med följande indata:

- minecraft - objektet vi använder för att prata med Minecraft. Funktionen ser inte de variabler som vi använder i resten av programmet.
- x, y, z - Koordinater som anger var huset skall börja.
- b, h, d - Anger bredd, höjd och djup i block för huset
- antalVaningar - Antal våningar
- vaggBlock - Anger block som skall användas för väggen
- golvbBlock - Anger block som skall användas för golvet
- takBlock - Anger block som skall användas för husets tak

Funktionen anropas sedan med:

	hoghus(minecraft, pos.x + 5, pos.y, pos.z + 5, 15, 4, 10, 8, BRICK_BLOCK.id, STONE_BRICK.id, STONE_SLAB.id)

8 är i detta fallet antalet våningar.

----------
### Övning 10

Använd 2 for-loopar för att skapa en stad med 10 x 10 höghus. 

Positionen för husen kan beräknas på följande sätt:

Om i och j är variabler från for-looparna och husens mått är 10 respektive 20 blir koordinaterna som anges i funktionen:

	... pos.x + 5 + i*20*2, pos.y, pos.z + 5 + j*10*2, ...

dvs husen sätts ut med dubbla bredden och djupet mellan varandra.


![](hus4.png)

## Slumptal - Kasta tärning med datorn

För att spel inte skall vara så förutsägbara kan man låta dator kasta tärning och låta tärningens siffror bestämma vad och hur saker skall placeras.

Slumptal i Python skapas med kommandot randint(...). Kommandot behöver 2 indata startvärde och slutvärde. Dessa anger mellan vilka värden slumptalet skall hamna. Följande kod visar hur man kan skapa slumptal mellan 1 och 6 dvs en vanlig tärning.

	from mc import *
	from time import *
	
	# Denna behövs för att få tillgång till slumptalskommandot.
	from random import * 
	
	minecraft = Minecraft()
	
	pos = minecraft.player.getTilePos()
	
	minecraft.postToChat(str(randint(1,6)))

Kör man programmet i Minecraft visas värden mellan 1 och 6 i chat-fönstret.

![](random1.png)

radint(...) kan också användas som indata till andra kommandon. Följande kod skapar 100 st sten block slumpmässigt run spelaren

	from mc import *
	from time import *
	from random import *
	
	minecraft = Minecraft()
	
	pos = minecraft.player.getTilePos()
	
	for i in range(100):
		x = randint(-20,20)
		y = randint(1,40)
		z = randint(-20,20)
		minecraft.setBlock(pos.x + x, pos.y + y, pos.z + z, STONE)

![](random1.png)

----------
### Övning 10

Vad händer om man sätter ut vatten (WATER_FLOWING) eller sand block (SAND)?

Prova att ändra antal block och start och slutvärden i randint-kommandona.

----------

## Samla block spel

I detta avsnitt skall vi skriva ett spel där spelaren skall samla block på en bana. När 20 block är samlade slutar spelet och den totala tiden för att samla in blocken skrivs ut.

Spelet kan delas upp i ett antal delar:

 1. Koppla oss mot Minecraft
 2. Skapa och rensa spelplan
 3. Sätt ut 20 st block slumpmässigt. Se till att det inte finns ett block på den plats man sätter ut blocket.
 4. Initiera variabler som behövs för spelet
 5. Starta spelloopen
 6. Skriv ut totaltiden
 
### 1 - Koppla oss mot minecraft

Vi startar med följande kod som ni redan sett i de tidigare exemplen. 

	# -- coding: utf-8 --
	
	from mc import *
	from time import *
	from random import *
	
	minecraft = Minecraft()
	
	pos = minecraft.player.getTilePos()
	
Först raden gör att vi kan använda å, ä och ö i koden.
 
### 2 - Skapa och rensa spelplan

I detta steg skall vi skapa en spelplan runt spelaren 20 x 20 block centrerad runt spelaren. Spelplanen skall ha en kant runt om. Vi rensar tidigare block genom att sätta ut luft block (AIR). 

### 3 - Sätt ut 20 block som skall samlas upp

I detta steg använder vi randint för att sätta ut 20 st block på vår spelplan. För att vi skall vara säkra på att vi inte sätter ut block ovanpå varandra måste vi kontrollera om det redan finns ett block på samma ställe. Detta gör vi med en s.k. if-sats. Med en if-sats kan man kontrollera att ett villkor är uppfyllt. Om det är uppfyllt körs koden i dess block. Vår kod för att sätta ut block blir då:

	for i in range(20):
		x = randint(-10, 10) 
		y = 0
		z = randint(-10, 10) 
		
		# Kontrollera att det inte finns ett block på samma plats
		
		if minecraft.getBlock(pos.x + x, pos.y + y , pos.z + z) != GLOWSTONE_BLOCK.id:
			minecraft.setBlock(pos.x + x, pos.y + y , pos.z + z, GLOWSTONE_BLOCK)
			
### 4 - Variabler

För att spelet skall fungera behöver vi ett antal variabler för att hålla koll på tid, antal block som har samlats in och om spelet är slut. 

	hitCount = 0
	startTime = 0
	endTime = 0
	playing = True

### 5 - Spelloop

Själva spelet sker i en spelloop. Det är kod som hela tiden körs för att kontrollera vad som händer i spelet. Loopen i vårt spel börjar med:

	while playing:
		# Kod för vårt spel
	
Detta betyder att koden i loopen kommer att köra fram tills dess att variabeln playing sätts till False

I nästa steg behöver vi be Minecraft kontrollera om spelaren har aktiverat ett block genom att slå på det med svärdet. Detta görs med kommandot:

		blockHits = minecraft.events.pollBlockHits()
		
Om spelaren aktiverat några block kommer blockHits innehålla en lista över dessa block annars kommer den att vara 0. Vi testar detta och skapar en loop som går igenom alla träffar.

	if blockHits:
				
		for blockHit in blockHits:
			
Första kontrollen vi måste göra är att se om det är rätt block som har träffats. Om det är rätt raderar vi blocket från Minecraft genom att sätta ut ett luftblock (AIR).

			blockType = minecraft.getBlock(blockHit.pos.x, blockHit.pos.y, blockHit.pos.z)
			
			if blockType == GLOWSTONE_BLOCK.id:
				
				# Om det är ett glowstone block tar vi bort det 
				
				minecraft.setBlock(blockHit.pos.x, blockHit.pos.y, blockHit.pos.z, AIR)

I nästa steg måste vi kontrollera om detta är det första blocket spelaren har aktiverat, isåfall lagrar vi start tiden i startTime. Vi räknar också upp antalet block som samlats upp.

				if hitCount == 0:
					startTime = time()
					
				hitCount = hitCount + 1

Spelet avslutas när 20 block har samlats in. För att avsluta spelloopen sätter vi playing = False. Detta gör att while loopen inte kommer att fortsätta. Vi lagrar också sluttiden.

				if hitCount == 20:
					endTime = time()
					playing = False

Varje gång användaren aktiverat ett block, skriver vi totalt insamlade block.

				minecraft.postToChat("Antal block samlade = "+str(hitCount))
				
När spelloopen avslutats skriver vi ut resultaten i chatfönstret.

	totalTime = endTime - startTime
	minecraft.postToChat("Total time = "+str(totalTime))
	
![](collect_game.png)

-----
### Övningar

 * Prova att ändra storleken på banan
 * Prov att sätta ut slumpmässiga hinder på banan
 * Ändra material
 * Avsluta spelet efter en viss tid. Räkna poäng för olika typer av block
 
-----
### Hela programmet

	# -- coding: utf-8 --
	
	from mc import *
	from time import *
	from random import *
	
	minecraft = Minecraft()
	
	pos = minecraft.player.getTilePos()
	
	# Skapa spelplan
	
	minecraft.setBlocks(pos.x-11,pos.y,pos.z-11,pos.x+11,pos.y,pos.z+11,STONE)
	minecraft.setBlocks(pos.x-10,pos.y,pos.z-10,pos.x+10,pos.y,pos.z+10,AIR)
	minecraft.setBlocks(pos.x-11,pos.y-1,pos.z-11,pos.x+11,pos.y-1,pos.z+11,STONE)
	
	# Satt ut vi skall samla ihop
	
	for i in range(20):
		x = randint(-10, 10) 
		y = 0
		z = randint(-10, 10) 
		
		# Kontrollera att det inte finns ett block på samma plats
		
		if minecraft.getBlock(pos.x + x, pos.y + y , pos.z + z) != GLOWSTONE_BLOCK.id:
			minecraft.setBlock(pos.x + x, pos.y + y , pos.z + z, GLOWSTONE_BLOCK)
		
	# Variabler för poäng och tidtagning
	
	hitCount = 0
	startTime = 0
	endTime = 0
	playing = True
		
	while playing:
		
		# Kontrollera vilka block som har träffats
		
		blockHits = minecraft.events.pollBlockHits()
		
		if blockHits:
			
			# Loopa över alla block som träffats
			
			for blockHit in blockHits:
	
				# Kontrollera vilka block som träffats
							
				blockType = minecraft.getBlock(blockHit.pos.x, blockHit.pos.y, blockHit.pos.z)
				
				if blockType == GLOWSTONE_BLOCK.id:
					
					# Om det är ett glowstone block tar vi bort det 
					
					minecraft.setBlock(blockHit.pos.x, blockHit.pos.y, blockHit.pos.z, AIR)
					
					# Spelet startar när man slår på första glowstone blocket.
					
					if hitCount == 0:
						startTime = time()
						
					hitCount = hitCount + 1
					
					# När man har samlat 20 block är spelet slut och vi kontrollerar tiden igen.
						
					if hitCount == 20:
						endTime = time()
						playing = False
						
					# Skriv antal samlade block
						
					minecraft.postToChat("Antal block samlade = "+str(hitCount))
	
	totalTime = endTime - startTime
	minecraft.postToChat("Total time = "+str(totalTime))


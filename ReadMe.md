```table-of-contents
title: 
style: nestedList # TOC style (nestedList|nestedOrderedList|inlineFirstLevel)
minLevel: 0 # Include headings from the specified level
maxLevel: 3 # Include headings up to the specified level
includeLinks: true # Make headings clickable
hideWhenEmpty: false # Hide TOC if no headings are found
debugInConsole: false # Print debug info in Obsidian console
```
# Project Title 
WIFO-Modell DEIO (Dynamic Econometric Input-Output)

# Project Description
This file provides:  
	a) a brief overview of the WIFO-DEIO Model and its structure,  
	b) instructions on how to use the DEIO-Shiny App, and  
	c) a concise description of the underlying R code.

# Description of DEIO

The following desciption of the DEIO Model is from @franz_2023: 

[[Franz_2023.pdf#page=232&selection=12,0,26,14&color=yellow|Franz_2023, p.232]]
#### Methodischer Ansatz
Die Abschätzung der gesamtwirtschaftlichen Effekte der Investitionen bzw. der Förderungen wird mit einer Erweiterung der traditionellen Input-Output-Analyse durchgeführt, welche im **WIFO-Modell DEIO** (Dynamic Econometric Input-Output) umgesetzt wurde. Diese Analyse liefert Informationen darüber, welche Nachfragewirkungen die Verwendung einer gewissen Investitionssumme in einem bestimmten Bereich (z.B. Maschinenbau, Tiefbau) kurzfristig auslöst. Im Folgenden werden demnach die Wirkungen der Investitionen mithilfe dieses Modellansatzes abgeschätzt, der auf den Input-Output-Tabellen 2019 (default) nach ÖNACE-Klassifikation beruht. Die Erweiterung im Vergleich zur Traditionellen Multiplikatoranalyse umfasst i) die Nutzung weiterer von Statistik Austria angebotenen Tabellen sowie ii) die Integration von konsuminduzierter Nachfrage der Privaten Haushalte aufgrund geänderter Einkommensströme und iii) die Abschätzung der Auswirkungen auf öffentliche Einnahmen und Ausgaben. Auf Basis der Input-Output-Tabelle in DEIO können Multiplikatoren ermittelt werden, die angeben, wie viele Güter in einer Wirtschaft insgesamt produziert werden, wenn eine Einheit an die Endnachfrage (Investitionen sind Teil der Endnachfrage) geliefert werden soll bzw. welche Beschäftigungswirkung damit verbunden ist. Die Multiplikatoren ergeben sich dabei durch die Vorleistungsverflechtungen der Wirtschaft. Die Multiplikatoreffekte aus dieser statischen Input-Output-Analyse sind als „Erstrundeneffekte“ („indirekte Effekte“) zu interpretieren. Berücksichtigt werden die Güterproduktion und Beschäftigung, die durch die Endnachfrage (Investitionen) und die dafür notwendige Produktion an Vorleistungen ausgelöst werden. Zusätzlich zum Erstrundeneffekt wird in DEIO ein zusätzlicher Effekt berechnet, der sich aus der durch die Nachfrageerhöhung (Investitionen) ausgelösten Einkommenssteigerung ergibt, welche wiederum über den privaten Konsum positiv auf die Nachfrage wirkt. Dieser Effekt ist als „Zweitrundeneffekt“ („konsuminduzierter Effekt“) zu interpretieren.
#### Input-Output Tabelle  
Die Grundlage des DEIO ist die Input-Output-Tabelle (vgl. hierzu Statistik Austria). Diese stellt die intersektoralen Verflechtungen der Volkswirtschaft dar, indem einerseits die Verteilung des Outputs (Bruttoproduktionswert) jedes Sektors auf die einzelnen empfangenden Sektoren gezeigt wird und andererseits die von anderen Sektoren empfangenen Lieferungen aller Sektoren (Inputs) dargestellt werden. Die Gesamtproduktion eines Sektors entspricht somit allen an andere Sektoren gelieferten Gütern und den Kategorien der Endnachfrage (z.B. Bau, Ausrüstungsinvestitionen, etc.). Von der Kostenseite her betrachtet besteht die Gesamtproduktion aus der Summe der empfangenen Vorleistungen sowie den Wertschöpfungskomponenten.
#### Transport- und Handelsspannen sowie Gütersteuern und subventionen 
Neben der Input-Output-Tabelle werden in DEIO zwei weitere Tabellensätze verwendet, die relevante Informationen beinhalten. Der erste Satz sind die Tabellen der Handels- und Transportspannen. Diese liegen in der gleichen Sektor- und Güterstruktur vor wie die Input-Output-Tabellen. Sie enthalten Informationen darüber, wieviel von der Nachfrage eines Gutes in Transportkosten und Handelsmargen übergeht und somit nicht beim Erzeuger ankommt. Wenn beispielsweise ein Gut im Handel gekauft wird, stecken im angebotenen Preis die Gewinnspanne des Handels und die dahinterliegenden Transportkosten. D.h. die Nachfrage nach einem Gut löst die Nachfrage nach Transport und Handelsdienstleistungen aus und nur zu einem Teil die Nachfrage nach der Produktion des Gutes selbst. Der zweite Tabellensatz sind die Tabellen der Gütersteuern und -subventionen, die ebenfalls in der gleichen Struktur vorliegen. Sie zeigen, wieviel der Nachfrage in Steuern abfließt bzw. wieviel Gütersubvention im jeweiligen Gut steckt. Entsprechend weniger (bei Steuern) oder mehr (bei Subventionen) Nachfrage fließt dann zum Erzeuger. In DEIO wird zusätzliche Nachfrage zu „Aufkommenspreisen“ um die Handels- und Transportspannen sowie um die Nettosteuern korrigiert, sodass eine Nachfrage zu „Herstellungspreisen“ vorliegt, die dann die ökonomischen Effekte in den Sektoren auslöst.
#### Induzierter Konsumeffekt 
Das Modell DEIO berechnet neben den indirekten Effekten einen konsuminduzierten Effekt. Das zusätzliche Einkommen, welches durch den Erstrundeneffekt der Nachfrage (Investitionen) generiert wird, verändert das verfügbare Einkommen der Haushalte. Diese geben einen Teil des zusätzlich verfügbaren Einkommens für Konsum aus und sorgen somit für weitere induzierte Nachfrage.
#### Abschätzung Öffentliche Einnahmen und Ausgaben 
In den Input-Output-Tabellen, die in DEIO verwendet werden, sind ein Großteil (~ 97 %) der in Österreich eingenommenen Steuern abgebildet. Das betrifft in erster Linie indirekte Steuern wie Produktions- und Güterabgaben aber auch direkte Zahlungen wie die Sozialbeiträge der Arbeitgeber. Darüber hinaus werden die von den Haushalten bezahlten Einkommenssteuern und Sozialbeiträge als fixe Anteile am Bruttoeinkommen berechnet. Somit kann die Änderung des Steueraufkommens durch eine Nachfrageänderung abgeschätzt werden.
Ausgabenseitig werden in dieser Studie ausschließlich die Aufwendungen für Arbeitslosenunterstützung abgeschätzt. Dazu werden durchschnittliche Aufwendungen pro Arbeitslosen (in VZÄ) auf Basis der Ausgabenposten und der Arbeitslosenzahlen von Statistik Austria ermittelt und in der Simulation in DEIO mit der Änderung der Beschäftigung kombiniert. Dadurch lässt sich der Effekt der Investitionen auf diesen Ausgabenposten abschätzen. Eine Änderung der Arbeitslosenunterstützung wird auf das verfügbare Einkommen der Haushalte übertragen, d.h. wenn die Beschäftigung zunimmt, steigen die Einkommen und sinken die Transfers zur Arbeitslosenunterstützung.
#### Beschäftigungseffekt 
Bei der Ermittlung des Beschäftigungseffekts mittels typischer Input-Output-Analyse handelt es sich nicht notwendigerweise um zusätzlich geschaffene, also neue Arbeitsplätze. Vielmehr ist es die Zahl der durch die simulierten Wirtschaftseffekte ausgelasteten Beschäftigten (Zahl der "branchentypischen Beschäftigungsverhältnisse"). Die errechnete Zahl der Arbeitsplätze stellt also in einem gewissen Sinn die "benötigte" Anzahl dar, die durch einen Mix aus Neueinstellungen, Überstunden und Behebung von Unterauslastung bestehender Beschäftigungsverhältnisse (also "gesicherte Arbeitsplätze") abgedeckt wird. Dieser Mix wird nicht zuletzt von der konjunkturellen Lage in den betroffenen Sektoren bestimmt sein. Im DEIO Modell wurde versucht, mit dieser Problematik umzugehen und die Abschätzung der Beschäftigungseffekte zu verbessern. Dazu wurde ein Parameter geschätzt, der repräsentiert, inwieweit historische (2000 – 2016) (default) Produktionsänderungen sich im Durchschnitt in zusätzlicher Beschäftigung niedergeschlagen haben. Dadurch kann ein durchschnittlicher Effekt simuliert werden, der angibt, in welchem Ausmaß zusätzliche Nachfrage in Folge zusätzliche Beschäftigung generiert.
#### Emissionen
Zusätzlich zum Beschäftigungseffekt können mittels Emissionserweiterung die resultierenden zusätzlichen CO2 Emissionen ermittelt werden. Die Emissionsdaten bestehen (default) aus: [Luftemissionsdaten von Statistik Austria](https://www.statistik.at/statistiken/energie-und-umwelt/umwelt/luftemissionsrechnung) (CO2 Emissionen in 1000 Tonnen aus fossilen und sonstigen Quellen) für lokal Emissionen, sowie Emissionsintensitäten (Tonnen / USD) basierend auf [OECD Daten](https://data-explorer.oecd.org/vis?lc=en&fs[0]=Topic%2C1%7CEnvironment%20and%20climate%20change%23ENV%23%7CAir%20and%20climate%23ENV_AC%23&pg=0&fc=Topic&bp=true&snb=15&df[ds]=dsDisseminateFinalDMZ&df[id]=DSD_AEA%40DF_AEA&df[ag]=OECD.SDD.NAD.SEEA&df[vs]=1.2&dq=.A........).  
#### Simulation 
Erfasst werden durch die vorliegende Analyse die direkten und indirekten Effekte der Investitionen. Direkte Effekte beziehen sich etwa auf die Beschäftigungswirkung in den Bausektoren durch verschiedene Investitionen, während die indirekten Effekte durch die Vorleistungsbeziehungen des Sektors determiniert werden. Induzierte Effekte ergeben sich durch die zusätzlich ausgelöste Nachfrage der Haushalte. Die Summe der direkten, indirekten und induzierten Wirkungen ergibt den Gesamteffekt der Investitionen. Berechnet wird der Gesamteffekt auf Output (Bruttoproduktionswert, BPW) und Wertschöpfung (BPW abzüglich Vorleistungen). Weiters werden die Beschäftigungseffekte (zusätzliche Beschäftigung) der Investitionen in Beschäftigungsverhältnissen und Vollzeitäquivalenten abgeschätzt, sowie daraus resultierende CO2 Emissionen.


# Use of Shiny App

> [!note] Default Settings
> The Shiny App comes with pre-installed data:
> - Input Output Tables:
> 	- from Statistic Austria (Aufkommens und Verbrauchstabellen nach 2 Stellern)  
> 		- for the year 2019
> 		- 74 NACE Sectors
> 		- 74 Commodities
> - Emission Data: 
> 	- domestic emissons - Luftemissionsrechnung (CO2 aus fossilen Quellen und sonstigen Quellen) (in 1000 tons)
> 	- imported emissions - own calculation (Mark) - based on OECD Data (in t/USD)

### (1) Pre-Set Model Settings  
The Shiny App includes pre-defined model settings, which can be adjusted under:  
#### Model Settings  
- Maximum number of iterations  
- Convergence criteria  
#### Parameter Settings  
- Settings for revenue (*Einstellung für Einnahmen*)  
- Labor market settings (*Einstellung für Arbeitsmarkt*)  
- Additional information (*Sonstige Informationen*)  
---
### (2) Adjusting Model Settings & Applying Demand Shock  
After modifying the model settings or using the default ones, click the **blue "Shock Sector" button**.  
Here, you can enter a demand shock (in million Euros) for domestic or imported demand.  
> *(At the top of the page, you can see the number of sectors in your model.)*  
---
### (3) Running the Model  
Next, click the **red "Run Model" button** to execute the model.  

### (4) Reviewing Parameter Settings  
In the **"Parameter"** tab, you get an overview of your selected parameters.  

### (5) Viewing Model Results  
In the **"Result"** tab, the following model outcomes are available:  
1. **Übersicht** – Displays the main results.  
2. **Sektor** – Presents key results by sector.  
3. **Branche** – Provides main results by industry groups.  
4. **Emissionen** – Shows total, domestic, and imported emissions (by sector and commodity).  
5. **Plots** – Offers a selection of visual representations.  
Most result tables can be downloaded as CSV via the button in the top-right corner.
***

> [!tip] Adjust Digits
> If you want to see the results with a different number of digits, adjust the setting on the left side under **"#Select Digits"**. After selecting the desired number of digits, rerun the model using the **red "Run Model" button**. The results will now be displayed with the updated digit format.

# Import Own/New Data  

If you want to use new or different data, ensure that your files are saved in the correct format. You will need:  
## Required Data
### 1) Input-Output Tables  
- Each file should be a separate Excel file, stored in one folder, and starting with the same prefix (e.g., `ET_.xlsx`).  
- The function automatically reads the number of sectors and commodities. To ensure it works correctly, use the provided data from Statistics Austria as is.  
- Data should only start after the **7th row** in the Excel file.  
### 2) Emission Data  
- A template for emission data is available in the **"raw_data"** folder.  
- The number of emission sectors must match the sectors in the input-output tables.  
- Provide domestic emission data in **1,000 tons**.  
- Provide imported emission intensity data in **tons per €**.  
### 3) Sector Name Table  
- A template for the sector name configuration is available in the **"raw_data"** folder.  
- Stick to the provided template.  
- The number of sectors/commodities must match those in the input-output tables.  

---
## Import New Data  

1. Click on **"Source Data"** on the left side.  
2. Provide the **directory** of the folder containing your input-output tables  
   *(e.g., `D:\mmusterman\OneDrive - WSR\Projekte\DEIO_R\raw_data\raw_iodata_v94\2019`)*.  
3. Enter the **prefix** of your raw data  
   *(e.g., type `E_tab` if your files are named `E_tab01.xlsx`, `E_tab03.xlsx`, etc.)*.  
4. Provide the **path** to the Excel file containing the emission data  
   *(e.g., `D:\mmusterman\OneDrive - WSR\Projekte\DEIO_R\raw_data\emissions\df_emissions_74.xlsx`)*.  
5. Provide the **path** to the Excel file containing the sector/branch names  
   *(e.g., `D:\mmusterman\OneDrive - WSR\Projekte\DEIO_R\raw_data\sector_names\sector_names_v74.xlsx`)*.  
6. **IMPORTANT:** Click **"Reset Data"**—this will delete all previously created data in the "data" folder.  
7. Click **"Source Data"** to generate new data for the IO analysis.  
8. Proceed as described above. If your new data contains more sectors, this will be reflected in the **"Shock Sector"** panel.  
9. **Remember:** After closing the Shiny App, the default settings will be restored.  


> [!check] **Data Folder**  
> All files created during the process will be saved in the **"data"** folder:  
> - **raw_data.rds** – Contains the raw imported data.  
> - **derived_data.rds** – Stores the derived matrices.  
> - **par_list.rds** – Saves the set parameters.  
> - **shocked_sectors.rds** – Records the shocked sectors.  
> - **result_data.rds** – Contains the main results.  
>  
> However, these files may be difficult to interpret directly.  
> It is recommended to export the results as **CSV files** via the Shiny App for better readability and usability.  


# Structure of the Shiny App Code  

The following table outlines the structure of the Shiny App code:  

| **Folder**   | **File**                                      | **Task**                                               |
|-------------|---------------------------------------------|------------------------------------------------------|
| **main**     | **Main folder**                              |                                                      |
|             | `ui.R`                                       | Loads the necessary libraries, server, and runs the UI. |
|             | `server.R`                                   | Contains server functions.                          |
|             | `dependencies.R`                             | Loads required libraries.                          |
|             | `DEIO_R.Rproj`                               | Main project file – start here!                    |
|             | `help.csv`                                   | Contains help text for the Shiny App.              |
| **www**      | **CSS Styling**                              |                                                      |
|             | `deio_style.css`                             | Contains CSS style elements.                        |
| **raw_data** | **Templates + Example Data**                 |                                                      |
|             | `emissions/`                                 | Folder containing the emission template.            |
|             | `sector_names/`                              | Folder containing the sector name template.        |
|             | `...`                                        | Other folders with raw example data.                |
| **data**     | **(If empty, run the model – this folder must exist)** |                                               |
|             | `derived_data.rds`                           | Stores derived matrices.                           |
|             | `par_list.rds`                               | Saves used parameter settings.                     |
|             | `raw_data.rds`                               | Contains imported raw data.                        |
|             | `result_data.rds`                            | Stores results.                                   |
|             | `shocked_sectors.rds`                        | Contains sectors and shocks.                       |
| **code**     | **Main Code Files**                          |                                                      |
|             | `00_raw_data_import.R`                       | Imports IO Tables, emission data, etc.             |
|             | `01_derive_data.R`                           | Derives matrices and creates an empty dataframe for further analysis. |
|             | `02_io_analysis.R`                           | Runs the IO analysis.                              |
|             | `03_output_tables.R`                         | Creates result tables for the Shiny App.           |
|             | `functions.R`                                | Contains utility functions.                        |
|             | `raw_data_path.R`                            | Stores file paths when new data is loaded.         |






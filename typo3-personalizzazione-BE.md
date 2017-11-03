
# Personalizzare il backend di typo3

## Eliminare i campi non utilizzati 
Per nascondere un campo non utilizzato pre tutti gli utenti di BE
```
TCEFORM.tt_content.section_frame.disabled = 1 
```
Se devo nasconderlo solo ad utenti non Admin ricorro ai permessi

## personalizzazione RTE
Rimuovere i bottoni disponibili dall'RTE
```
RTE.default.hideButtons = blockstylelabel, blockstyle, textstylelabel, textstyle, fontstyle, fontsize, table, about
```
Rimuovere le opzioni disponibili dal menu a tendina formatblock
```
#Remove item fron formatblock drlop-down list
#Formatblock default items are: p,h1,h2,h3,h4,h5,h6,pre,address,article,aside,blockquote,div,footer,header,nav,section
RTE.default.buttons.formatblock.removeItems = h0,h1,h2,address,article,aside,div,footer,header,nav,section
```
(Documentazione)[https://docs.typo3.org/typo3cms/extensions/rtehtmlarea/Configuration/PageTsconfig/interfaceConfiguration/Index.html]


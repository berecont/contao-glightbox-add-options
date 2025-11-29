# contao-glightbox-add-options
Stellt ein Template js_glightbox.html5 Template zur Verfügung das Optionen aus einer config.yaml aussliest.  

Wurde für die Erweiterung [https://github.com/inspiredminds/contao-glightbox] erstellt.  

## Installation  
Kopiere die Datei `js_glightbox.html5` in den `\templates\`-Ordner.  
Oder überschreibe den Inhalt von der aus dem Backend heraus erstellten Templatedatei `\templates\js_glightbox.html5`  
oder `\templates\mytheme\js_glightbox.html5`  

Kopiere den Inhalt der `config.yaml` in die `\config\config.yaml`.  
Exsistiert in deiner Installation diese Datei noch nicht, dann legst du einen Ordner `config` im root deiner Installation an - auf gleicher Ebene wo auch deine `composer.json` oder der `files`-Ordner sich befinden.  
In diesen Ordner kopierst du dann die hier bereit gestellte `config.yaml` ... `\config\config.yaml`  

## Verwendung  
Anpassungen für weitere/deine gewünschten Optionen kannst du nun in der `config.yaml` vornehmen.  
**Wichtig:** das Set `fallback` muss mindestens in dieser Ausführung erhalten bleiben! Kann jedoch ebenfalls mit Optionen befüllt werden.  

Über ein **Set** und die dann verwendete, im Inhaltselement eingetragene CSS Klasse, werden die Optionen für genau diese(s) Inhaltselement(e) gesetzt.  
**Sets** können beliebig erweitert und mit Optionen befüllt werden.  
Eigene **Sets** können hinzugefügt, gelöscht oder angepasst werden. Die beiden **Sets** `loop` und `fade` sind Beispiel-Sets.  
Möchtest du, dass z.B. immer die Option `loop` gesetzt ist, ohne, dass im Inhaltselement eine CSS Klasse eingetragen sein muss, dann füge die Option `loop` im Set `fallback` hinzu:  
```
parameters:
  glightbox_sets:
    ## fallback ist zwingend damit das script in js_glightbox.html5 funktioniert
    fallback:
      selector: 'a[data-lightbox].gboxDefault'
      loop: true
```
**Beachte, dass nach einer Änderung der `\config\config.yaml` der Prod.Cache gelöscht werden muss, damit die Änderung greift**  

Der **Set**-Name ist zugleich die CSS Klasse, die im Backend in den `Experteneinstellungen` im Feld `Klasse` eingetragen wird. Damit greift dein benutzerdefiniertes Set. Wird hier keine CSS Klasse, die einem **Set** entspricht, dann greift automatisch das **Set** `fallback`.  

## Ziel dieser Anwendung  
Optionen können auch direkt im angepassten Standard-Template - im `js_glightbox.html5` das mit der Erweiterung mitgeliefert wird - eingetragen werden.  
Dazu wird dieser Teil ergänzt:  
```
  GLightbox({
    selector: 'a[data-lightbox]'
    ## packe hier deine eigenen Optionen rein ##
  });
```
**Nachteil:** alle Optionen wirken sich auf alle Inhaltselemente aus.  
Ich kann damit keine unterschiedlichen Medien-Elemente steuern.  

Mit der hier angeführten Möglichkeit können gezielt Optionen je Medien-Element eingefügt werden. Und dies flexibel und einfach über die `\config\config.yaml`.  

## Weiterführende Quellen  
[inspiredminds/contao-glightbox](https://github.com/inspiredminds/contao-glightbox)  
[Glightbox Optionen](https://github.com/biati-digital/glightbox/blob/master/README.md#lightbox-options)


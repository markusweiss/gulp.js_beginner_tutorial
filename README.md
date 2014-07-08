# gulp.js Beginner Tutorial (deutsch/german)

Vorab das ganze wurde auf einem Mac ausgeführt auf einer Windows/Linux Umgebung kann das teilweise etwas anders aussehen.

Ich gehe davon aus das [node.js](http://nodejs.org/) installiert ist und schaut auch mal auf die [gulp.js](http://gulpjs.com/) Seite.

##Gulp.js zu einem Projekt hinzufügen:
<br>

`cd mein-projekt-ordner/`

####Ab jetzt seid Ihr im Projektordner und legt alles darin an:

Entweder eigene ***package.json*** anlegen

<br>
<pre>
{
  "name": "Mein Projektname",
  "version": "1.0.0",
  "devDependencies": {
  }
}
</pre>

oder


`npm init ` in der Konsole ausführen.

Hier müsst Ihr einige Fragen beantworten und das File wird erstellt.<br>
Ihr könnt das jederzeit manuell anpassen.

####So nun installiert Ihr gulp local in Euer Projektverzeichnis:
<br>

`npm install gulp --save-dev`
<br>

####Jetzt hab Ihr einen neuen Ordner in Eurem Projektverzeichnis:

**node_modules** mit dem Unterordner **gulp**

Eure ***package.json***

wurde jetzt um einen Eintrag erweitert:
<br>
*(In meinem Fall die 3.8.5 Version)*

<br>
<pre>
"devDependencies": {
    "gulp": "^3.8.5"
  }
</pre>
  
####So jetzt müssen wir überlegen welche Plugins wir installieren wollen.

Ich nehme jetzt erstmal eins, später können wir alle die wir brauchen aufeinmal installieren.

Da wir oft Files zusammenführen wollen installieren wir erstmal **gulp-concat**.


`npm install gulp-concat --save-dev`


So jetzt schaut mal wieder in Eure ***package.json***

Die Datei wurde wieder um 1 Eintrag erweitert:

<br>
<pre>
    "gulp-concat": "^2.2.0"
</pre>

Schaut auch bitte in Eurem **node_modules** Ordner nach:

zu dem **gulp** Ordner ist jetzt 1 neuer Ordner hinzugekommen:

**gulp-concat**

####Nun die Datei ***gulpfile.js*** im Projektordner anlegen:
<br>
<pre>
// Include gulp
var gulp = require('gulp'); 

// Include Plugins
var concat = require('gulp-concat');

// Task zum zusammenpacken der Dateien im Ordner js
gulp.task('scripts', function() {
    return gulp.src('js/*.js')
        .pipe(concat('alle.js'))
        .pipe(gulp.dest('js_gepackt'))
});

// Default Task
gulp.task('default', ['scripts']);
</pre>


`gulp` in der Konsole ausführen.

Jetzt wurden alle Dateien im Ordner **js** zusammengepackt und in den Ordner **js_gepackt** kopiert.

###Nun wollen wir den Ordner js überwachen

Wir fügen folgende Zeilen in die Datei ***gulpfile.js*** ein.

<br>
<pre>
// den Task scripts überwachen
gulp.task('watch', function() {
    gulp.watch('js/*.js', ['scripts']);
});
</pre>

Mit `gulp watch` überwacht Ihr den Ordner **js**. 
Ändert Ihr darin eine Datei werden wieder alle Dateien zusammengefasst in der Datei ***alle.js*** abgespeichert.

###Fortsetzung und weiter Infos folgen noch.
Details auf Anfrage ich werde das ganze noch erweitern!
<br><br>
8. Juli 2014
<br><br>







    
    

 
  
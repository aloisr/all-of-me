
.. _virtuelle-maschine-erzeugen:

Virtuelle Maschine erzeugen
===========================

Das ``leoclient2-init``-Script bereitet eine virtuelle Machine (VM) vor, die später mit dem Programm ``leovirtstarter2`` gestartet werden kann. Es muss mit root-Rechten gestartet werden:

.. code-block:: console

   # sudo leoclient2-init
   [sudo] Passwort für linuxadmin:

   Geben Sie den Namen der neuen virtuellen Maschine ein
   (Keine Leerzeichen - bestätigen mit der Enter-Taste):
   winxp
   ...
   Soll die virtuelle Maschine jetzt erzeugt und VirtualBox gestartet werden?
   (j/n - Bestätigen mit der Enter-Taste):
   j

   Virtual machine 'winxp' is created and registered.
   UUID: d96f7ee1-3c82-4bef-aa04-c9d39140cede
   Settings file: '/virtual/winxp/winxp.vbox'
   0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
   Medium created. UUID: 4da77206-3edf-41d6-84ec-1509cfb92441


Es werden folgende Parameter abgefragt und auf Nachfrage VirtualBox gestartet.

- der MASCHINENNAME für die VM (keine Leerzeichen verwenden)
- der PFAD für den Speicherort der VM (Standardpfad ``/var/virtual/``)
- die Größe der virtuellen Festplatte für die VM in MB

..
   Damit werden folgende Aktionen vom Script ausgeführt:

   - das Verzeichnis ``/PFAD/MASCHINENNAME`` angelegt,
   - die virtuelle Festplatte ``/PFAD/MASCHINENNAME/MASCHINENNAME.vdi`` erzeugt
   - die Konfigurationsdatei für die VM ``/etc/leoclient2/machines/MASCHINENNAME.conf`` mit dem ``/PFAD/MASCHINENNAME`` als Inhalt erzeugt
   - anschließend wird die Konfiguration für die VM eingestellt und VirtualBox damit gestartet


Man kann unter VirtualBox die Konfiguration der VM noch an die eigenen
Bedürfnisse anpassen (Die Arbeitsspeichergröße für die VM wird beim
Starten an die Gegebenheiten der vorhandenen Maschine angepasst).

Betriebsystem
-------------

Der Typ und die Version des Betriebssystems sollten von "Other" auf
das jeweilig Gewünschte geändert werden.


DVD-Laufwerk
------------

Ein CD-/DVD-Laufwerk kann man ebenso einbinden wie iso-Dateien (→
CD-/DVD-Laufwerk hinzufügen → kein Medium (Laufwerk) → über das
CD-Symbol rechts das Laufwerk auswählen bzw. → CD-/DVD-Laufwerk
hinzufügen → Medium auswählen (iso-Datei) ).

USB verwenden
-------------

Sollte man, wie voreingestellt, USB2 verwenden wollen, muss man das
zur Version von VirtualBox passende Extension Pack installieren. Unter
Ubuntu 16.04 kann man das Paket ``virtualbox-ext-pack`` passend zur
installierten Version von VirtualBox nachinstallieren.

In anderen Linux-Distributionen muss man eventuell das richtige
Extension Pack manuell herunterladen
(https://virtualbox.org/wiki/Download_Old_Builds) und installieren (→
Datei → Globale Einstellungen … → Zusatzpakete → Rechtsklick auf
rechtes Feld → Paket hinzufügen → auswählen → installieren →
OK). 

Netzwerk offline
----------------

Eine Netzwerkkarte ist in der Standardkonfiguration nicht aktiviert,
dadurch bietet die VM keine Angriffsfläche und man kann auf
zeitraubende Updates verzichten.  Trotzdem ist es möglich auf die
Netzlaufwerke auf dem Server zuzugreifen und Netzwerkdrucker zu
verwenden.

Betriebssystem installieren
---------------------------

Sind die Einstellungen wunschgemäß, startet man die VM und installiert
das Betriebssystem über eine verbundene Installations-CD-/DVD oder
eine entsprechende iso-Datei.

Ist die Installation abgeschlossen, fährt man die VM herunter.  Bevor
VirtualBox beendet wird, sollte man eventuell verbundene
CD-/DVD-Laufwerke trennen.

Nach Beenden von Virtualbox wird die VM für den Start mit dem Programm
``leovirtstarter2`` fertiggestellt.

.. code-block:: console

   ...
   Für diese Maschine wird ein Sicherungspunkt erzeugt.
   0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
   Snapshot taken. UUID: 3df3f4f2-38e8-4747-9934-533648e60d3f
   ...
   Die Konfiguationsdateien und der Snapshot wurden gesichert.
   Die Rechte der Dateien wurden angepasst.
   Die virtuelle Maschine kann nun mit dem Snapshotstarter benutzt werden.
   
   Wenn Sie die Basis für die virtuelle Maschine und den Snapshot neu
   erzeugen wollen, starten Sie das Script 'leoclient2-base-snapshot-renew'.
   
   Wenn Sie die vollständige virtuelle Maschine in ein anderes Verzeichnis
   umziehen wollen, starten Sie das Script 'leoclient2-vm-move'.
						

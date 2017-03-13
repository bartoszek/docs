RoyalRender
===========

.. image:: /images/royalrender.png
  :scale: 100 %
  
Serveur
.......

le serveur royal render s'apelle royal (192.168.32.35)

le serveur est lance au boot dans le fichier /etc/kde4/kdm/Xsetup

.. code:: tcsh

  su - render -c '/shared/apps/royal-render/bin/lx64/rrServerconsole &'

pour voir les logs du serveur : tail -f /shared/apps/royal-render/sub/log/server_Royal.txt

Client
......

le client est lance au boot dans le fichier /etc/kde4/kdm/Xsetup

.. code:: tcsh

  su - render -c '/shared/apps/royal-render/bin/lx64/rrClientconsole &'
  su - render -c '/shared/apps/royal-render/bin/lx64/rrClientwatch &'
  
les dossiers locaux sont aussi crees par Xsetup : /usr/local/RR_localdata

Configs
.......

le fichier principal se trouve dans /shared/apps/royal-render/sub/cfg_global/clients.ini

pour rajouter une Render Application : dans rrClientWatch -> Restore UI puis dans l'UI -> Options/Configuration

les configs generales se font dans rrConfig

Misc
....

If you set Sequence Divide Min to 0, then the sequence is not divided.All frames are send at once to one client.

Nuke
....

dans /shared/apps/nuke/Nuke7.0v9/plugins/menu.py : cree un menu et fait le lien avec le script

.. code:: tcsh

  m =  menubar.addMenu("RRender");
  m.addCommand("Submit Comp", "nuke.load('rrSubmit_Nuke_5'), rrSubmit_Nuke_5()")
  
le script est /shared/apps/nuke/Nuke7.0v9/plugins/rrSubmit_Nuke_5.py copie depuis
royal-render/render_apps/_submitplugins/rrSubmit_Nuke_5.py

Houdini
.......

(13.0.582 par ex) dans /shared/apps/houdini/hsite/houdini13.0/MainMenuCommon.xml

.. code:: tcsh

  ....
  <addScriptItem id="h.royalrender">
        <parent>render_menu</parent>
        <label>Submit Royal Render</label>
                <scriptPath>menu/lmSubmitToRoyalRender.py</scriptPath>
        <scriptArgs></scriptArgs>
        <insertAfter/>
  </addScriptItem>
  .....
  
le script se trouve dans /shared/apps/houdini/hsite/houdini_multiple_versions/scripts/menu/lmSubmitToRoyalRender.py

le dossier se trouve dans la variable d'environnement 

.. code:: tcsh

  HOUDINI_PATH=/shared/apps/houdini/hsite/houdini13.0:/groups/3d/houdini/hsite/houdini13.0:/shared/apps/houdini/hsite/houdini_multiple_versions;&

cette variable est sete dans /shared/bin/_houdini_version.sh

Mecanisme de submission
.......................

le script de submit (lance dans l'application) cree un fichier .xml (par ex houdini cree /tmp/tmp_file_for_houdini_submission_to_rr.xml)

dans ce fichier sont tous les parametres des jobs/layers etc

.. code:: tcsh

  ......
  <Job>

                <Layer> /obj/ropnet1/mantra1 </Layer>
                <ImageExtension> .exr </ImageExtension>
                <ImageDir> /work/cgi/Perso/lulu/rr_test/houdini/linetests </ImageDir>
                <SeqStart> 1.0 </SeqStart>
                <OutputPath> /work/cgi/Perso/lulu/rr_test/houdini/linetests </OutputPath>
                <SeqEnd> 240.0 </SeqEnd>
                <ImageFilename> w1. </ImageFilename>
                <SceneName> /work/cgi/Perso/lulu/rr_test/houdini/w1.hip </SceneName>
                <SceneDatabaseDir> /work/cgi/Perso/lulu/rr_test/houdini </SceneDatabaseDir>
                <ImageFileNameVariables> /work/cgi/Perso/lulu/rr_test/houdini/w1.hip </ImageFileNameVariables>
                etc
  ....
  
puis est lance la commande /shared/apps/royal-render/lx__rrSubmitter.sh tmp_file_for_houdini_submission_to_rr.xml qui va tout envoyer au serveur
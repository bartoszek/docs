RoyalRender
===========

Web Reference
.............

http://www.royalrender.de/help7/index.html

Submitter
.........

create a submit.xml file and launch submitter

http://www.royalrender.de/help7/index.html?rrJobsubmitxmlfile.html

.. code:: tcsh

  #!/usr/bin/perl
  open (XML,">","submit.xml");
  print XML "<rrJob_submitFile syntax_version=\"6.0\">\n";
  print XML "<DeleteXML>1</DeleteXML>\n";
  print XML "<Job>\n";
  print XML "  <IsActive> true </IsActive>\n";
  print XML "  <SceneName> $SCENENAME/NEURAL.conf </SceneName>\n";
  print XML "  <SceneDatabaseDir> $SCENENAME </SceneDatabaseDir>\n";
  print XML "  <Software> Neural </Software>\n";
  print XML "  <SeqStart> 1 </SeqStart>\n";
  print XML "  <SeqEnd> 100 </SeqEnd>\n";
  print XML "  <Layer> $STYLE </Layer>\n";
  print XML "  <ImageDir> $ANIMOUTPUTDIR/ </ImageDir>\n";
  print XML "  <ImageFilename> $OUTPUT </ImageFilename>\n";
  print XML "  <ImageExtension> .jpg </ImageExtension>\n";
  print XML "  <ImageFramePadding> 4 </ImageFramePadding>\n";
  print XML "</Job>\n";
  print XML "</rrJob_submitFile>\n";
  $cmd="/shared/apps/royal-render/lx__rrSubmitter.sh submit.xml";
  print $cmd;
  system $cmd;
  
Render config
.............

http://www.royalrender.de/help7/index.html?Addnewrenderapp.html

/royal-render/render_apps/_config/N01__Neural.cfg

.. code:: tcsh

  ################################## Identify Render Application ################################## 
  Name= Neural
  rendererName= 
  Version=1
  Version_Minor=0
  Type=3D
  ##################################  Commandlines Linux ##################################
  CommandLine_Lx=
	  <SetEnvGlobal>
  CommandLine_Lx=
	  <SetEnvSoft>
  CommandLine_Lx=
	  <ResetExitCode> 
  CommandLine_Lx=  
	  "/shared/Code/bin/neural_jcj.pl"
	  <SeqStart> <SeqEnd>
	  "<PD/<Scene>>"
  CommandLine_Lx=
	  <CheckExitCode> <FN>
  ################################## Submitter Settings ################################## 
  SequenceDivide= 1~1
  SeqDivMIN=1~2
  SeqDivMAX=1~2
  RenderPreviewFirst=1~0
  ################################## Client Settings ################################## 
  
add environment file
....................

render_apps/_setenv/lx/_globals.sh

render_apps/_setenv/lx/autocolor.sh (lowercase only !!!)

.. code:: tcsh

  setenv PYTHONPATH "/home/render/caffe/python"
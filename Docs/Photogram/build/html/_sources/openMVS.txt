OpenMVS
=======

Web references
..............

http://cdcseacave.github.io/openMVS/

https://github.com/cdcseacave/openMVS/wiki/Building

Use openMVS
...........

https://github.com/cdcseacave/openMVS/wiki/Usage

.. code:: tcsh

  InterfaceOpenMVG -i ./MVG/reconstruction_sequential/sfm_data.json -o scene.mvs
  DensifyPointCloud --estimate-colors 1 --estimate-normals 1 -i scene.mvs -o scene_dense.mvs
  ReconstructMesh scene_dense.mvs
  ReconstructMesh scene_dense.mvs (default)
  ReconstructMesh --remove-spurious 5 scene_dense.mvs
  RefineMesh scene_dense_mesh.mvs
  TextureMesh scene_dense_mesh_refine.mvs
  
build OpenMVS
.............

sur vXXX utiliser -march=native pour desactiver l'utilisation d'AVX ?

.. code:: tcsh

  export CXXFLAGS="$CXXFLAGS -march=native"

.. code:: tcsh

  git clone https://github.com/cdcseacave/openMVS.git
  main_path=`pwd`
  mkdir openMVS_Build
  cd openMVS_Build
  cmake . ../openMVS -DCMAKE_BUILD_TYPE=RELEASE 
  -DVCG_DIR="$main_path/vcglib" 
  -DCERES_DIR="/usr/local/share/Ceres" 
  -DOpenCV_CAN_BREAK_BINARY_COMPATIBILITY=OFF
  -DOpenMVG_DIR:STRING="$main_path/openMVG_Build/openMVG_install/share/openMVG/cmake/"
  make
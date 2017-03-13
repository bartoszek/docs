Deflickr
========

https://github.com/nbonneel/blindconsistency

http://liris.cnrs.fr/%7Enbonneel/consistency/

https://www.youtube.com/watch?v=reiT2SJh96U&feature=youtu.be

Linux compile:
..............

modifier #include "patchmatch\nn.h" en #include "patchmatch/nn.h"

dans OptFlowPatchMatch.h

ajouter

#include "CImg.h"

using namespace cimg_library;

dans regularisation.h

rajouter 

#include <stdint.h>

dans CImg.h

et remplacer __int64 par int64_t
et unsigned __int64 par uint64_t


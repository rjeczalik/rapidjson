# Copyright (c) 2011 Milo Yip (miloyip@gmail.com)
# Copyright (c) 2013 Rafal Jeczalik (rjeczalik@gmail.com)
# Distributed under the MIT License (see license.txt file)

foreach(it condense pretty prettyauto serialize tutorial)
  add_executable(${it} ${it}/${it}.cpp)
endforeach()

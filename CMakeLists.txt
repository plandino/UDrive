
#Establezco una minima version de CMake para correr
cmake_minimum_required (VERSION 2.8)

#Activo los test
#enable_testing()

#Le doy un nombre al proyecto
project (logger)

#Incluyo las librerias de headers
include_directories(include/)

#Agrego todos los archivos de SOURCE
file(GLOB SOURCE "src/*.cpp")

#Creo el ejecutable "UDrive", a partir de los archivos de SOURCE
add_executable(logger ${SOURCE})


#Macro que crea los test
	#arg es el argumento que se le pasa al ejecutable UDrive (En esta prueba HolaMundo no necesita ejecutable)
	#result es el resultado esperado que devulva el ejecutable UDrive
	#Si HolaMundo${arg} es igual a ${result}, la prueba es exitosa

macro (do_test arg result)

  #Crea el test
  add_test (HolaMundo${arg} UDrive ${arg})

  #Verifica el test
  set_tests_properties (HolaMundo${arg} PROPERTIES PASS_REGULAR_EXPRESSION ${result})
endmacro (do_test)
 
# Hago los tests
do_test (Good "Hola Mundo!!")
do_test (Fail "Tristan Suarez")
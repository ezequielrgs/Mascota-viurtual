import random

"""
mascota:
    nombre:str,
    trucos:int | str,
    dueño & estado: function (dict),
    {
    feliz:bool | int
    triste: bool | int
    hambriento: bool | int
    } <- podemos llevar a cabo los comportamientos.
    
    
    +----------------------------+
    |        Usuario             |
    +----------------------------+
    |           -Nombre          |
    |           -Mascota         |
    |           -LogrosMascota   |
    +----------------------------+
    |           -Premiar         |
    |           -Alimentar       |
    |           -Jugar           |
    +----------------------------+



    +----------------------------+
    |          Mascota           |
    +----------------------------+
    |           -Nombre          |
    |           -Estado          |
    |           -Trucos          |
    |           -Dueño           |
    +----------------------------+
    |        -Alimentar          |
    |        -Jugar              |
    |        -Dormir             |
    +----------------------------+

    +----------------------------+
    |          Estado            |
    +----------------------------+
    |                            |
    |           -Hambre          |
    |           -Sueño           |
    |           -Sed             |
    |           -Felicidad       |
    +----------------------------+
    |                            |
    |        -Alimentar          |
    |        -Jugar              |
    +----------------------------+
"""


def mascota(estados, dueno):
    nombre = {"nombre" : "Pepa"}
    
    atributos = {
       "nombre" : nombre["nombre"],
       "estado" : estados["atributos"],
       "trucos" : "trucos",
       "duenio" : dueno["nombre"]
   }
    
    acciones = {
        "ac" : "alimentar",
        "ac1" : "jugar",
        "ac2" : "dormir"  
    }
    
    objeto_mascota = {
        "nombre" : nombre,
        "atributos" : atributos,
        "acciones" : acciones
    }
    
    return objeto_mascota
   
#-----------------------------------------------------------------------

def estado()-> dict:
    nombre = {"nombre" : "Estados"}
    
    atributos = {
       "hambre" : "hambre",
       "sueno" : "sueno",
       "sed" : "sed",
       "mejora" : "felicidad"
   }
    
    acciones = {
        "ac" : "alimentar",
        "ac1" : "jugar",
    }
    
    objeto_estado = {
        "nombre" : nombre,
        "atributos" : atributos,
        "acciones" : acciones
    }
    
    return objeto_estado

#------------------------------------------------------------------------

def dueno(mascota)-> dict:
    nombre = {"nombre" : "Jose"}
    
    atributos = {
       "nombre mascota" : mascota["nombre"]["nombre"],
       "nombre" : nombre["nombre"],
       "logros" : 0
   }
    
    acciones = {
        "ac" : "premiar",
        "ac1" : "alimentar",
        "ac2" : "jugar"  
    }
    
    objeto_dueno = {
        "nombre" : nombre,
        "atributos" : atributos,
        "acciones" : acciones
    }
    
    return objeto_dueno

#------------------------------------------------------------------------

def seleccionar_estado(estado):
    estado_momentaneo = random.randint(1, len(estado))
    return estado_momentaneo
    
def trucos():
    pass

def estado_actual(accion, estado, usuario, nuevo_estado):
    if nuevo_estado == estado["hambre"]:
        if accion == "alimentar":
            estado_mascota = estado["mejora"]
        else:
            estado_mascota = "Insadisfecho"
            
    elif nuevo_estado == estado["sueno"]:
        if accion == "acostar":
            estado_mascota = estado["mejora"]
        else:
            estado_mascota = "Insadisfecho"
            
    elif nuevo_estado == estado["sed"]:
        if accion == "darle de tomar":
            estado_mascota = estado["mejora"]
        else:
            estado_mascota = "Insadisfecho"
            
    elif nuevo_estado == estado["mejora"]:
        estado_mascota = estado["mejora"]
    
    return estado_mascota

def main():
    mascotas = mascota(usuario, estados)
    usuario = dueno(mascotas)
    estados = estado()
    logros = usuario["logros"]
    ncecidad = input("quieres empezar: ")
    while ncecidad == "si":
        print()
        nuevo_estado = seleccionar_estado(estados["atributos"])
        print(f"El estado del bicho es este: {nuevo_estado}")
        accion = input("Ingrese la accion: ")
        estado_de_mascota = estado_actual(accion, usuario, estados["atributos"], nuevo_estado)
        print(f"El estado de tu mascota es: {estado_de_mascota}")
        if estado_de_mascota == estados["atributos"]:
            logros = logros + 1
            print("conseguiste un logro")
        ncecidad = input("Quieres continuar: ")
        
main()

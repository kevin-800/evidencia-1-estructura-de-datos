##importación de librerias
from collections import namedtuple
import re
import os
import datetime
import time


separador = ("-" * 20) + "\n"

repetidor = True
#Creacion de diccionario vacio
objecto_registrado = {}
#Diccionario = ("objectos", {"folio", "fecha", "descripcion","cantidad","precio", "total"})
objecto = namedtuple("objectos", {"folio", "fecha", "descripcion","cantidad","precio", "total"})


while repetidor:
    print("********MENU REGISTRO DE PERSONAS********")
    print("1: Agregar un registro ")
    print("2: Ver datos de los registros")
    print("3: Salir")
    respuesta = input("Ingrese una opción: ")
    print(separador)

    if respuesta == "1":
        #recorrido del diccionario 
        #Agregar contenido a la lista de los productos que se venderan
        folio = input("Marque su folio por favor: ")
        if not folio in objecto_registrado.keys():
            fecha = input("Dime una fecha: ")
            procesado = datetime.datetime.strptime(fecha, "%d/%m/%Y").date()
            
            otro_registro="S"
            #Opcion para registrar otros datos
            while otro_registro.upper()=="S":
                descripcion = input("Marque el producto que desea llevarse: ")
                cantidad = int(input("La cantidad del producto que desea llevar: "))
                precio = int(input("El precio de sus productos: "))
                total = {cantidad * precio * 0.16}

                ##Las Listas de refacciones folio, fecha, descripcion, cantidad, precio, total
                registrado = objecto(folio, fecha, descripcion, cantidad, precio, total )
                
                print("¿Desea Hacer otro registro?  [S/N]")
                otro_registro=input()
                
                
            
            objecto_registrado[folio] = registrado
            
                
            print("Registro completado")
            print(separador)
        else:
            print(f"Este folio ya fue registrado. Intente otra vez")
            
                  
    elif respuesta == "2":
          #Si en el diccionario no esta la clave te dara la opcion de folio no registrado
        folios_registrados = input("Ingrese el folio con el cual hizo su registro ")
        if folios_registrados in objecto_registrado.keys():
            print(f"Su folio es: {folio} ")
            print(f"La fecha de su registro fue el: {objecto_registrado[folio].fecha}")
            print(f"El Producto que se llevara son: {objecto_registrado[folio].descripcion}")
            print(f"El precio del producto: {objecto_registrado[folio].cantidad}")
            print(f"El precio de sus productos es: {cantidad * precio} todo y su total de iva seria: {total}")
            print(separador)
        else:
            print("folio no registrado. ")
            
    elif respuesta == "3":
        
        for folio in objecto_registrado.keys():
            #Mostrar los datos que fueron agrgados
            print(f"Su folio es: {folio} ")
            print(f"La fecha de su registro fue el: {objecto_registrado[folio].fecha}")
            print(f"El Producto que se llevara sonf: {objecto_registrado[folio].descripcion}")
            print(f"El precio del producto: {objecto_registrado[folio].cantidad}")
            print(f"El precio de sus productos es: {cantidad * precio} todo y su total de iva seria: {total}")
            print(separador)
            print("Saldrás del sistema!")
            
        repetidor = False
    else:
        print("Esa opción no es válida")


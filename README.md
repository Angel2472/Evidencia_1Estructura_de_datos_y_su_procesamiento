

from collections import namedtuple
import datetime
switch = True
lista = {}
articulo = namedtuple('articulo','descripcion, piezas, precio, fecha')
fecha_actual = datetime.date.today()

while True:
    print("")
    print('** MENU **')
    print('Registrar una venta [1]')
    print('Consultar datos [2]')
    print('Consultar una venta [3]')
    print('Salir[4]')
    print("")
    op = input('¿Que desea hacer?: ')
    print("")
    
    if op == '1':
         while True:
           clave = input('Introduzca la clave: ')
           if clave in lista:
               print('Esa clave ya existe, intente con otra')
           else:
                descripcion = input('Introduzca la descripcion del articulo: ')
                piezas = int(input('Introduzca la cantidad de piezas vendidas: '))
                precio = float(input('Introduzca el precio de venta: '))
                datos = articulo(descripcion,piezas,precio,fecha_actual)
                lista[clave] = datos
                
                total_venta = piezas * precio
                suma= (total_venta + total_venta)
                iva= float(suma * .16)
                total_con_iva = (suma + iva)
                
                resp = input('Desea seguir agregando [S/N]: ')
                if resp == 'N':
                    print("--------------------------------")
                    print("SUBTOTAL $", suma)
                    print("IVA(16%) $", iva)
                    print("TOTAL $", total_con_iva)
                    print("--------------------------------")
                    print("Volviendo al menu principal...")
                    print("")
                    break     
    elif op == '2':
       for clave in lista.keys():
           print(f'Clave del articulo: {clave}' )
           print(f'Descripcion del articulo: {lista[clave].descripcion} ')
           print(f'Cantidad de piezas vendidas: {lista[clave].piezas} ')
           print(f'Precio de venta: {lista[clave].precio} ')
           print(f'Fecha de venta: {lista[clave].fecha_actual} ')
           print("")
    elif op == '3':
        code = input('Introduzca la clave a buscar: ')
        if code in lista.keys():
            print(f'Descripcion del articulo: {lista[code].descripcion} ')
            print(f'Cantidad de piezas vendidas: {lista[code].piezas} ')
            print(f'Precio de venta: {lista[code].precio} ')
            print(f'Fecha de venta: {lista[code].fecha} ')
        else:
            print("")
            print('** NO ESTA **')
            print("")
    elif op == '6':
        print('Has salido del sistema')
        break
    


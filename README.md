# frank2007
tres en raya
from typing import Match
from colores.colors import green,cyan,bold,rest
from sys import stdout

Tablero=[]
Tablero_fila=3
TABLER_columnas=3 #nuesstro tasdythsac

for i in range(9):
   Tablero.append('')
   
def numero(literal, inferior, superior):
     while True:
      Valor=input(literal)
      while(not Valor.isnumeric()):
        print("solo se admiten numeros entre {0} y {1}".format(inferior,superior))
        Valor=input(literal)
      coor=int(Valor)
      if(coor >=inferior and coor <=superior):
        return coor

      else:
          print("El valor indicado es incorrecto, introduzca un numero valido entre {0}y{1}".format(inferior,superior))

def colocarficha():
    print("dame la posicion de una ficha ")
    while True:
      fila=numero("fila entre [1y3]:",1,3)-1
      columna =numero("columna entre [1y3]:",1,3)-1
      #como mi table1ro 3*3
      casilla=fila*TABLER_columnas+columna
      if(Tablero[casilla]!=''):
        # b
        print("la casilla esta ocuapda")
      else:
       Tablero[casilla]=ficha 
      return casilla

def colores (colores):
    colores = "colores
    type (cadena)
    <class cadena >  

def colocarfichamaquina(ficha):
      
    for casilla,valorCasilla in enumerate(Tablero): 
      if(valorCasilla==" "): 
        Tablero[casilla]=ficha
        return casilla

def pintarTablero(ficha):
      pos=0 
      print(("-"*18))
      for fila in range(3):
          for columna in range(3):
             print("| ",Tablero[pos]," ", end= ' ') 
             pos+=1
          print("|\n",("-"*18))    



def numerohermanos(casilla, h, v):
    f=Match.floor (casilla/TABLER_columnas)
    c=casilla % TABLER_columnas
    fila_nueva=f+v
    if(fila_nueva<0 or fila_nueva>Tablero_fila):
       return 0
    columna_nueva=c+h
    if(columna_nueva<0 or columna_nueva>=TABLER_columnas):
      return 0
    
    
    pos=(fila_nueva*TABLER_columnas+columna_nueva)
    if(Tablero[pos]!=ficha):#sdi
       return 0
    else:
        return 1+numerohermanos(pos,ficha,v,h)


def hemosGanado(casilla,ficha):
 hermanos=numerohermanos(casilla,-1,-1)+numerohermanos(casilla,ficha-1,1)
 if(hermanos==2): 
   return True
 hermanos=numerohermanos(casilla,1,-1)+numerohermanos(casilla,ficha-1,1)
 if(hermanos==2):
  return True
 hermanos=numerohermanos(casilla,-1,0)+numerohermanos(casilla,ficha,1,0)
 if(hermanos==2):
  return True
 hermanos=numerohermanos(casilla,0,-1)+numerohermanos(casilla,ficha,0,1)
 if(hermanos==2):
  return True
            
    
jugadores=[]
numerojugadores=numero("numero de jugadores:",0,2)
for i in range(numerojugadores):  
   jugadores.append({"nombre":input("nombre de el jugador"+str(i+1)+":"),"tipo":"h"})
for i in range(2-numerojugadores):
  jugadores.append({"nombre":"maquina"+str(i+1),"tipo":"m"})

print("\n empezamos la partida con los jugadores")
for jugador in jugadores:
    print("\t",jugador["nombre"])
continuar = True
fichaEntablero=0
while continuar:
 pintarTablero()
 numjugador=(fichaEntablero&1)
ficha='x' if numjugador==1 else 'o'
if(jugadores[numjugador]["tipo"]=="h"): 
     casilla=colocarficha(ficha)
else:
    casilla=colocarfichamaquina(ficha,ficha='x' if numjugador==1 else 'o')
if(hemosGanado(casilla,ficha)):
      contiunuar=False
      print(jugadores[numjugador]["nombre"],"has ganado")
fichaEntablero+=1 
if(fichaEntablero==9):
  continuar=False
pintarTablero()    

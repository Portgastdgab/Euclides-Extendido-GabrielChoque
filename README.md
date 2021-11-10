# Algebra-Abstracta-Gabriel-Choque

El algoritmo extendido de Euclides nos ayuda a hallar el inverso de un numero en base a otro.
En cryptografia es muy importante poder hallar el inverso dentro de un cuerpo.
Este nos ayuda a generar claves publicas y privadas en sistemas de cifra asimetrica, entre estos se encuentra el conocido RSA.
Forma en la que realice el algoritmo en C++:

    Hacer (g0, g1, u0, u1, v0, v1, i) = (B, A, 1, 0, 0, 1, 1)

    Mientras g[i] =! 0 hacer:
      Hacer y[i+1] = parte entera(g[i+1]/g[i]
      Hacer g[i+1] = g[i-1] - y[i+1] * g[i]
      Hacer u[i+1] = u[i-1] - y[i+1] * u[i]
      Hacer v[i+1] = v[i-1] - y[i+1] * v[i]
      Haver i = i+1

    Si ( v[i-1] < 0)
      Hacer v[i-1] = v[i-1] + B

     Hacer x = v[i-1]
    
Ejemplo:

      x = Euclid_extended(A, B)
      x = Euclid_extended(9, 275)    //El inverso existe porque el mcd de 9 y 275 = 1; 9 = 3^2; 275 = (5^2) * 11

      Reemplazando en el pseudocodigo quedaria:
      i     y[i]     g[i]     u[i]     v[i]
      0     -        275      1        0
      1     -        9        0        1
      2     30       5        1        -30
      3     1        4        -1       31
      4     1        1        2        -61
      5     4        0        -9       275 
  
  El proceso se repite hasta que g[i] = 0; y el inverso de (9, 275) = -61 + 275 = 214
  
  x = 214, pues 214 * 9 = 1926; 1926mod275 = 1
  
  ¿Que tan rapido es el algoritmo de Euclides?
  Es muy rapido, por lo general llega a la solucion en muy pocos pasos, por ejemplo encontrar el mcd dentro de un cuerpo de
  2048 bits es instantaneo.

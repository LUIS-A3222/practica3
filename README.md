// Ejercicio 1
/01 Referencias e inmutabilidad de String
 - Indica qué imprime cada instrucción y qué variables comparten un objeto.
System.out.println(a == b);		 -- false
System.out.println(a == c);		 -- true
System.out.println(a == d);		 -- false
System.out.println(a.equals(d));	 -- true
b = b.concat(" 21");            	 -- Une la cadena b con el 21
System.out.println(a);			 -- Imprime la cadena a
System.out.println(b)			 -- Imprime la cadena b concatenado con el 21

STRING POOL; Lo que hace es compara algun objeto que ya halla sido creado con el nuevo objeto, al saber que ya existe, entonces no lo crea, solo lo referencia
(==); Compara 2 valores de variables 
equals(); Compara el contenido del objeto

//Ejercicio 2
/02 Operaciones e índices en StringBuilder
 - Determina la salida exacta y el contenido tras cada modificación. 
Al final de la ejecucion solo saldra A-E
sb.delete(1, 4);	 -- Esto elminina los terminos de la posicion 1 hasta 1 antes de la posicion 4
sb.insert(1, "xyz"); 	 -- Despues de la posicion 1 agrega los terminos xyz
sb.reverse();		 -- Invierte el orden de la cadena
sb.replace(1, 4, "-");	 -- Remplaza los elementos de la posicion 1 a 1 antes del 4 con u '-'

-  Explica por qué delete(1, 4) no significa eliminar cuatro caracteres. Diferencia length() de capacity().
delete					 -- Indica de donde empieza pero acabara solo 1 antes de la posicion final
Diferencia length() de capacity().	 -- La primera nos dice el tamaño de la cadena y la segunda nos la capacidad del Builder


// Ejrcicio 3
03 Referencias compartidas
 - Escribe todas las salidas y explica cómo afecta cada modificación a las variables.
System.out.println(a);			-- Imprime Hola
System.out.println(b);			-- Imprime b, que como es igual a 'a' es Hola
System.out.println(c);			-- Imprime Hola
System.out.println(a == b);		-- Imprime true por que b ya es igual a 'a'
System.out.println(a.equals(b));	-- Imprime true por que solo se cambia la funcion de '==' por un equals
System.out.println(a.equals(c));	-- Imprime true ya que compara 2 objeto iguales
 
 - Dibuja un esquema de memoria con las variables, los objetos y sus referencias.

// 04 Compresión de caracteres consecutivos
 - Sustituye cada grupo de caracteres iguales y consecutivos por el carácter seguido de su número de repeticiones. Incluye el contador aunque el carácter aparezca una sola vez.


public class Prueba{

    //Metodos
private static char normalizar(char c){

    String origen =  "ABCDEFGHIJKLMNÑOPQRSTUVWXYZÁÉÍÓÚÜáéíóú";
    String destino = "abcdefghijklmnñopqrstuvwxyzaeiouüaeiou";
    int posicion = origen.indexOf(c);
    return posicion < 0 ? c : destino.charAt(posicion);
    }

private static boolean esSignificativo(char c){
    return (c >= 'a' && c <= 'z' ) || ( c >= '0' && c <= '9' ) || (c == 'ñ') || (c == 'ü' );
}

// Ejercicio 4

public static String comprimir(String cadena){  

    if(cadena.length() == 0) return "";
    StringBuilder resultado = new StringBuilder();
    char grupo = cadena.charAt(0);
    int rep = 1;

for (int i =  1; i < cadena.length(); i++){
      char  actual = cadena.charAt(i);
      if(actual == grupo ){
        rep++;
      }else {
        resultado.append(grupo).append(rep);
        grupo = actual;
        rep = 1;}
      }
resultado.append(grupo).append(rep);
return resultado.toString();
      
        }

//Ejercicio 5

public static boolean esPalindromo(String texto){
    
    int min = 0;
    int max = texto.length()-1;
    char left = texto.charAt(min);
    char right = texto.charAt(max);

    while ( min < max ){

           
        for (; min < max && !esSignificativo(texto.charAt(min)); min++) {
        }        
        for (; min < max && !esSignificativo(texto.charAt(max)); max--) {
        }
         left = normalizar(texto.charAt(min));
         right = normalizar(texto.charAt(max));
            if (left != right) {
            return false;
        }
        min++;
        max--;
    }
    return true;
}
        
// Ejercicio 6
    public static String eliminarDuplicados(String texto){
        
        StringBuilder resultado = new StringBuilder();

       
        for (int i = 0; i < texto.length(); i++) {
        char actual = texto.charAt(i);

    if (resultado.indexOf(String.valueOf(actual)) == -1) {
        resultado.append(actual);
        }
            }
            return resultado.toString();
        }   
    // Se uso deacuerdo a las instrucciones solo string o StringBuilder, despues con ayuda de un for y un indexOf() es que se logra encontrar los caracteres repetidos dando solo 1 vuelta a la cadena

//Ejercicio 7
    public static String reemplazar(String texto, String buscar, String reemplazo){

        StringBuilder nueva_cadena = new StringBuilder();
       
        int i = 0;
        if (buscar.isEmpty()) {
            return texto;
        }else{
                while (i < texto.length()){

                    if (texto.startsWith(buscar, i)) {
                        nueva_cadena.append(reemplazo);
                        i += buscar.length();
                         
                        }else {
                            nueva_cadena.append(texto.charAt(i));
                            i++;}
            }
        }      
            return nueva_cadena.toString();
    }

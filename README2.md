Tarea No3

//Ejercicio No.11

public static void arreglos(int[] numeros) {
        int suma = 0;
        int mayor = numeros[0];

        for (int i = 0; i < numeros.length; i++) {
            suma += numeros[i];

            if (numeros[i] > mayor) {
                mayor = numeros[i];
            }
        }

        double promedio = (double) suma / numeros.length;

        System.out.println("Suma = " + suma);
        System.out.println("Promedio = " + promedio);
        System.out.println("Mayor = " + mayor);
    }

    public static void main(String[] args) {
        int[] numeros = {8, 3, 10, 5, 4};

        arreglos(numeros);
    }

//Ejercicio No. 12


 public String addBinary(String a, String b) {
    char[] b1 = a.toCharArray();
    char[] b2 = b.toCharArray();

    StringBuilder resultado = new StringBuilder();

    int i = b1.length - 1;
    int j = b2.length - 1;
    int acarreo = 0;

    while (i >= 0 || j >= 0 || acarreo != 0) {
        int suma = acarreo;

        if (i >= 0) { suma += b1[i] - '0'; i--; }

        if (j >= 0) { suma += b2[j] - '0'; j--; }

        resultado.append(suma % 2);
        acarreo = suma / 2;
    }

    return resultado.reverse().toString();
}

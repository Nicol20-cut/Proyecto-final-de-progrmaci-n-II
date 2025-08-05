# Proyecto-final-de-progrmaci-n-II



public class CuentaBancaria {
    private double saldo;

    public CuentaBancaria(double saldoInicial) {
        this.saldo = saldoInicial;
    }

    public void consignar(double monto) {
        if (monto > 0) {
            saldo += monto;
            System.out.println("Consignación exitosa. Nuevo saldo: " + saldo);
        } else {
            System.out.println("Error: El monto a consignar debe ser positivo.");
        }
    }

    public void retirar(double monto) {
        if (monto > 0 && monto <= saldo) {
            saldo -= monto;
            System.out.println("Retiro exitoso. Nuevo saldo: " + saldo);
        } else if (monto > saldo) {
            System.out.println("Error: Saldo insuficiente. Saldo actual: " + saldo);
        } else {
            System.out.println("Error: El monto a retirar debe ser positivo.");
        }
    }

    public double consultar_saldo() {
        return saldo;
    }
}
public class Main {
    public static void main(String[] args) {
        // Inicializar la cuenta con un saldo de 1000
        CuentaBancaria miCuenta = new CuentaBancaria(1000);
        System.out.println("Saldo inicial: " + miCuenta.consultar_saldo());

        // --- Pruebas unitarias ---
        System.out.println("\n--- Realizando pruebas ---");

        // 1. Prueba de consignar: agregar una cantidad positiva
        System.out.println("Prueba 1: Consignar 500...");
        miCuenta.consignar(500);
        System.out.println("---");

        // 2. Prueba de retirar: monto menor al saldo
        System.out.println("Prueba 2: Retirar 200...");
        miCuenta.retirar(200);
        System.out.println("---");

        // 3. Prueba de retirar: monto mayor al saldo (saldo insuficiente)
        System.out.println("Prueba 3: Intentar retirar 2000...");
        miCuenta.retirar(2000);
        System.out.println("Saldo después del intento de retiro: " + miCuenta.consultar_saldo());
        System.out.println("---");

        // 4. Prueba de retirar: monto cero o negativo
        System.out.println("Prueba 4: Intentar retirar -100...");
        miCuenta.retirar(-100);
        System.out.println("Saldo después del intento de retiro: " + miCuenta.consultar_saldo());
        System.out.println("---");
    }
}

# Proyecto-Programacion
Elaboracion del codigo de programacion para el proyecto
//clases
// Enemigo.java
public abstract class Enemigo {
    protected String nombre; // Nombre del enemigo
    protected int salud; // Salud del enemigo

    // Constructor que inicializa el nombre y la salud del enemigo
    public Enemigo(String nombre, int salud) {
        this.nombre = nombre;
        this.salud = salud;
    }

    // Método abstracto que cada tipo de enemigo debe implementar
    public abstract void atacar();

    // Método para que el enemigo reciba daño
    public void recibirDanio(int danio) {
        salud -= danio; // Reduce la salud en la cantidad de daño recibido
        System.out.println(nombre + " ha recibido " + danio + " puntos de daño. Salud restante: " + salud);
    }

    // Método para verificar si el enemigo está vivo
    public boolean estaVivo() {
        return salud > 0; // Retorna true si la salud es mayor a 0
    }
}
////////////////////////////////////////////////////////
/ Arquero.java
public class Arquero extends Enemigo {

    // Constructor que llama al constructor de la clase base
    public Arquero(String nombre, int salud) {
        super(nombre, salud);
    }

    // Implementación del método atacar para el Arquero
    @Override
    public void atacar() {
        System.out.println(nombre + " dispara una flecha!");
    }
}
////////////////////////////////////////////////////////
// Sopista.java
public class Sopista extends Enemigo {

    // Constructor que llama al constructor de la clase base
    public Sopista(String nombre, int salud) {
        super(nombre, salud);
    }

    // Implementación del método atacar para el Sopista
    @Override
    public void atacar() {
        System.out.println(nombre + " lanza un hechizo de fuego!");
    }
}
////////////////////////////////////////////////////////
// Espadero.java
public class Espadero extends Enemigo {

    // Constructor que llama al constructor de la clase base
    public Espadero(String nombre, int salud) {
        super(nombre, salud);
    }

    // Implementación del método atacar para el Espadero
    @Override
    public void atacar() {
        System.out.println(nombre + " ataca con su espada!");
    }
}
////////////////////////////////////////////////////////
// Laudero.java
public class Laudero extends Enemigo {

    // Constructor que llama al constructor de la clase base
    public Laudero(String nombre, int salud) {
        super(nombre, salud);
    }

    // Implementación del método atacar para el Laudero
    @Override
    public void atacar() {
        System.out.println(nombre + " toca una melodía mágica!");
    }
}
////////////////////////////////////////////////////////
// Alma.java
public class Alma extends Enemigo {

    // Constructor que llama al constructor de la clase base
    public Alma(String nombre, int salud) {
        super(nombre, salud);
    }

    // Implementación del método atacar para el Alma
    @Override
    public void atacar() {
        System.out.println(nombre + " lanza una maldición!");
    }
}
////////////////////////////////////////////////////////Main
// Main.java
public class Main {
    public static void main(String[] args) {
        // Crear un array de enemigos
        Enemigo[] enemigos = new Enemigo[5];
        enemigos[0] = new Arquero("Arquero Oscuro", 100); // Arquero
        enemigos[1] = new Sopista("Sopista Fantasma", 80); // Sopista
        enemigos[2] = new Espadero("Espadero Maldito", 120); // Espadero
        enemigos[3] = new Laudero("Laudero Enigmático", 90); // Laudero
        enemigos[4] = new Alma("Alma Errante", 70); // Alma

        // Iterar sobre cada enemigo para mostrar sus acciones
        for (Enemigo enemigo : enemigos) {
            enemigo.atacar(); // Cada enemigo ataca
            enemigo.recibirDanio(20); // Cada enemigo recibe 20 puntos de daño
            System.out.println("¿Está vivo? " + enemigo.estaVivo()); // Verificar si el enemigo está vivo
            System.out.println(); // Espacio entre enemigos
        }
    }
}

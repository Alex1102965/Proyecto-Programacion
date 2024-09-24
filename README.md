# Proyecto-Programacion
Elaboracion del codigo de programacion para el proyecto
Package rpg;
//librerías 
Import rpg.entities.Player;
Import rpg.entities.Enemy;
Import java.util.Scanner;
//clase
Public class Game {
 Private Player player;
 Private Enemy enemy;
 Public Game() {
//elección de personajes 
 This.player = new Player(“Hero”);
 This.enemy = new Enemy(“Goblin”);
 }
//comentario a él usuario 
 Public void startGame() {
 System.out.println(“¡El combate ha comenzado entre “ + player.getName() + “ 
y “ + enemy.getName() + “!”);
//ciclo while para aparición del enemigo 
 While (player.isAlive() && enemy.isAlive()) {
 playerTurn();
 if (enemy.isAlive()) {
 enemyTurn();
 }
 }
 displayResult();
 }
// opciones para el usuario contra el enemigo 
 Private void playerTurn() {
 System.out.println(“\nTurno de “ + player.getName());
 System.out.println(“1. Atacar”);
 System.out.println(“2. Defenderse”);
 System.out.println(“3. Usar poción”);
 System.out.print(“Elige una opción: “);
//uso de switch case para casos en el combate 
 Int option = getPlayerOption();
 Switch (option) {
 Case 1:
 Player.attack(enemy); // Atacar al enemigo
 Break;
 Case 2:
 Player.prepareDefense(); // Prepararse para defenderse
 Break;
 Case 3:
 System.out.println(player.getName() + “ usa una poción.”); // Lógica para 
usar poción
 Break;
 Default:
 System.out.println(“Opción inválida. Se pierde el turno.”);
 Break;
 }
 }
//función para el ataque al enemigo 
 Private void enemyTurn() {
 System.out.println(“\nTurno de “ + enemy.getName());
 Enemy.attack(player); // El enemigo ataca al jugador
 }
//lectura de scanner en interaccion 
 Private int getPlayerOption() {
 Scanner scanner = new Scanner(System.in);
 Int option = 0;
 If (scanner.hasNextInt()) {
 Option = scanner.nextInt();
 } else {
 System.out.println(“Entrada inválida. Se pierde el turno.”);
 Scanner.next(); // Limpiar entrada no válida
 }
 Return option;
 }
//derrota de el enemigo o el jugador 
 Private void displayResult() {
 If (player.isAlive()) {
 System.out.println(“¡Has derrotado al enemigo “ + enemy.getName() + “!”);
 } else {
 System.out.println(“Juego terminado. Fuiste derrotado por “ + 
enemy.getName() + “.”);
 }
 }
}
Package rpg.entities;
Import rpg.enums.Stats;
Import java.util.HashMap;
//clase y selección de atributos del enemigo 
Public class Enemy {
 Private String name;
 Private HashMap<Stats, Integer> stats;
 Public Enemy(String name) {
 This.name = name;
 This.stats = new HashMap<>();
 This.stats.put(Stats.MAX_HP, 50);
 This.stats.put(Stats.HP, 50);
 This.stats.put(Stats.ATTACK, 5);
 This.stats.put(Stats.DEFENSE, 2);
 }
 Public String getName() {
 Return this.name;
 }
 Public HashMap<Stats, Integer> getStats() {
 Return this.stats;
 }
 Public boolean isAlive() {
 Return this.stats.get(Stats.HP) > 0;
 }
//función de acción del jugador 
 Public void attack(Player player) {
 Int attackPower = this.stats.get(Stats.ATTACK);
 Int playerDefense = player.getStats().get(Stats.DEFENSE);
 Int damage = Math.max(attackPower – playerDefense, 0); // Asegúrate de que 
el daño no sea negativo
//if – else para ataque al enemigo 
 If (damage > 0) {
 Player.getStats().put(Stats.HP, player.getStats().get(Stats.HP) – damage);
 System.out.println(this.name + “ ataca a “ + player.getName() + “ por “ + 
damage + “ de daño!”);
 } else {
 System.out.println(this.name + “ ataca a “ + player.getName() + “ pero no 
causa daño!”);
 }
 }
}

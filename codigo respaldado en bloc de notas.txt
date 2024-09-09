#include <iostream> // aqui llamamos la libreria "IOSTREAM" para las funciones de entrada y salida.
#include <string> // aqui llamamos a la libreria "STRING"para almacenar un conjunto de caracteres como un objeto.
using namespace std;
//aqui asignamos declaramos la cantidad de jugadores y lanzamientos.
const int NUM_PLAYERS = 5;
const int NUM_RELEASES = 3;

// Esta función registra los puntos de cada jugador en cada lanzamiento Los puntos se almacenan en la matriz "POINTS"
void REGISTER_POINTS(int POINTS[NUM_PLAYERS][NUM_RELEASES]) {
    for (int i = 0; i < NUM_PLAYERS; ++i) {
        cout << "player " << i + 1 << ":" << endl;
        for (int j = 0; j < NUM_RELEASES; ++j) {
            cout << " LAUNCH " << j + 1 << ": ";
            cin >> POINTS[i][j];
        }
    }
}

// Esta función calcula los puntos totales de cada jugador sumando sus puntos en cada lanzamiento, Los resultados se almacenan en el arreglo "TOTAL_POINTS"
void CALCULATE_TOTAL_POINTS(int POINTS[NUM_PLAYERS][NUM_RELEASES], int TOTAL_POINTS[NUM_PLAYERS]) {
    for (int i = 0; i < NUM_PLAYERS; ++i) {
        TOTAL_POINTS[i] = 0;
        for (int j = 0; j < NUM_RELEASES; ++j) {
            TOTAL_POINTS[i] += POINTS[i][j];
        }
    }
}

// esta funcion Esta función muestra los resultados de cada jugador y determina el ganador, Utiliza un bucle "FOR" para recorrer los puntos totales de cada jugador y encuentra el jugador con el puntaje más alto y lo declara ganador.

void SHOW_RESULTS(int TOTAL_POINTS[NUM_PLAYERS]) {
    int MAX_POINTS = -1;
    int WINNER = -1;
    for (int i = 0; i < NUM_PLAYERS; ++i) {
        cout << "player " << i + 1 << " - TOTAL POINTS: " << to_string(TOTAL_POINTS[i]) << endl;
        if (TOTAL_POINTS[i] > MAX_POINTS) {
            MAX_POINTS = TOTAL_POINTS[i];
           WINNER = i;
        }
    }
    cout << "THE WINNER IS THE PLAYER " << WINNER + 1 << " WITH A SCORE " << to_string(MAX_POINTS) << "!" << endl;
}
//La función "MAIN" es el punto de entrada del programa, esta Declara las matrices "POINTS" y "TOTAL_POINTS" y Llama a las funciones, "REGISTER_POINTS", "CALCULATE_TOTAL_POINTS","SHOW_RESULTS" siguiendo ese mismo orden para ejecutar el programa.

int main() {
    int POINTS[NUM_PLAYERS][NUM_RELEASES];
    int TOTAL_POINTS[NUM_PLAYERS];

    REGISTER_POINTS(POINTS);
    CALCULATE_TOTAL_POINTS(POINTS, TOTAL_POINTS);
    SHOW_RESULTS(TOTAL_POINTS);

    return 0;
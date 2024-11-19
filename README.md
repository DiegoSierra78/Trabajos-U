#include <iostream>
#include <stack>
#include <string>

using namespace std;

// Estructura que representa un vehículo
struct Vehiculo {
    string placa;
    string modelo;
};

// Función para agregar un vehículo al parqueadero
bool agregarVehiculo(stack<Vehiculo>& parqueadero, const Vehiculo& vehiculo, int capacidad) {
    if (parqueadero.size() < capacidad) {
        parqueadero.push(vehiculo);
        cout << "Vehículo agregado: " << vehiculo.placa << " - " << vehiculo.modelo << endl;
        return true;
    } else {
        cout << "Parqueadero lleno. No se puede agregar el vehículo: " << vehiculo.placa << " - " << vehiculo.modelo << endl;
        return false;
    }
}

// Función para sacar un vehículo del parqueadero
Vehiculo sacarVehiculo(stack<Vehiculo>& parqueadero) {
    if (!parqueadero.empty()) {
        Vehiculo vehiculo = parqueadero.top();
        parqueadero.pop();
        cout << "Vehículo sacado: " << vehiculo.placa << " - " << vehiculo.modelo << endl;
        return vehiculo;
    } else {
        cout << "No hay vehículos en el parqueadero." << endl;
        return {"", ""}; // Retorna un vehículo vacío
    }
}

// Función para mostrar el estado actual del parqueadero
void mostrarEstado(const stack<Vehiculo>& parqueadero) {
    if (parqueadero.empty()) {
        cout << "El parqueadero está vacío." << endl;
    } else {
        cout << "Vehículos en el parqueadero (LIFO):" << endl;
        stack<Vehiculo> temp = parqueadero; // Copia la pila para no modificar la original
        while (!temp.empty()) {
            Vehiculo v = temp.top();
            cout << v.placa << " - " << v.modelo << endl;
            temp.pop();
        }
    }
}

int main() {
    const int capacidad = 5; // Capacidad del parqueadero
    stack<Vehiculo> parqueadero; // Pila para almacenar los vehículos

    // Crear vehículos
    Vehiculo v1 = {"ABC123", "Toyota Corolla"};
    Vehiculo v2 = {"XYZ456", "Honda Civic"};
    Vehiculo v3 = {"LMN789", "Ford Focus"};
    Vehiculo v4 = {"OPQ012", "Chevrolet Spark"};
    Vehiculo v5 = {"RST345", "Nissan Sentra"};
    Vehiculo v6 = {"UVW678", "Hyundai Elantra"};

    // Agregar vehículos al parqueadero
    agregarVehiculo(parqueadero, v1, capacidad);
    agregarVehiculo(parqueadero, v2, capacidad);
    agregarVehiculo(parqueadero, v3, capacidad);
    agregarVehiculo(parqueadero, v4, capacidad);
    agregarVehiculo(parqueadero, v5, capacidad);
    agregarVehiculo(parqueadero, v6, capacidad); // Este no se agregará porque el parqueadero está lleno

    // Mostrar estado del parqueadero
    mostrarEstado(parqueadero);

    // Sacar vehículos del parqueadero
    sacarVehiculo(parqueadero);
    sacarVehiculo(parqueadero);

    // Mostrar estado del parqueadero después de sacar vehículos
    mostrarEstado(parqueadero);

    return 0;
}

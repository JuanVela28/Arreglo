# Ejercicio - Crea un programa en python que maneje arreglos que me permitan guardar
# las calificaciones de 10 alumnos, de 10 materias.

import numpy as np

class GestorCalificaciones:
    def __init__(self, alumnos, materias):
        self.alumnos = alumnos
        self.materias = materias
        self.calificaciones = np.zeros((len(alumnos), len(materias)))

    def ingresar_calificaciones(self):
        for i, alumno in enumerate(self.alumnos):
            print(f"Ingrese las calificaciones para el alumno {alumno}:")
            for j, materia in enumerate(self.materias):
                calificacion = float(input(f"Calificación de {materia}: "))
                self.calificaciones[i, j] = calificacion

    def mostrar_calificaciones(self):
        calificaciones_transpuestas = self.calificaciones.T
        print("\t", end="")
        for alumno in self.alumnos:
            print(f"{alumno}\t", end="")
        print()
        for i, materia in enumerate(self.materias):
            print(f"{materia}\t", end="")
            for j in range(len(self.alumnos)):
                print(f"{calificaciones_transpuestas[i, j]}\t", end="")
            print()


def main():
    materias = []
    for i in range(5):
        nombre_materia = input(f"Ingrese el nombre de la materia {i+1}: ")
        materias.append(nombre_materia)

    alumnos = []
    for i in range(10):
        nombre_alumno = input(f"Ingrese el nombre del alumno {i+1}: ")
        alumnos.append(nombre_alumno)

    gestor = GestorCalificaciones(alumnos, materias)
    gestor.ingresar_calificaciones()
    gestor.mostrar_calificaciones()


if __name__ == "__main__":
    main()

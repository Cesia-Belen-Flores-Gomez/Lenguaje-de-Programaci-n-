Practica Calificada

import streamlit as st
import pandas as pd

class Matriz:
    def __init__(self, nombre_archivo):
        self.__datos = pd.DataFrame(pd.read_csv(nombre_archivo, header=None).values)

    def mostrar_matriz(self):
        st.write("Matriz:")
        st.write(self.__datos)

    def calcular_media(self):
        st.write("Media de cada columna:")
        st.write(self.__datos.mean())

def main():
    st.title("Aplicación Matricial")

    nombre_archivo = st.sidebar.file_uploader("Cargar archivo CSV", type=["csv"])

    if nombre_archivo is not None:
        matriz = Matriz(nombre_archivo)

        st.sidebar.subheader("Operaciones")
        operacion = st.sidebar.selectbox("Selecciona una operación", ["Mostrar Matriz", "Calcular Media"])

        if operacion == "Mostrar Matriz":
            matriz.mostrar_matriz()
        elif operacion == "Calcular Media":
            matriz.calcular_media()

if __name__ == "__main__":
    main()

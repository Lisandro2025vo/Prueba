# Prueba
## Actividad 1
obtener el nombre de todos los usuarios mayores a 20 años de los siguientes paises: España, Francia y turkia. Cuanto son masculinos y cuanto son femeninis, hacer un grafico con matt lib
## ACtividad 2
obtener todos los usuarios entre las edades de 45 y 60. Cuantos son masculinos y cuantos son femeninos, hacer un grafico con mattlib
```python
import pandas as pd
import matplotlib.pyplot as plt

# Cargar el archivo CSV
df = pd.read_csv('users.csv')

# Filtrar usuarios mayores de 20 años de España, Francia y Turquía
paises = ["Spain", "France", "Turkey"]
filtro = (df['edad'] > 20) & (df['pais'].isin(paises))
usuarios_filtrados = df[filtro]

# Mostrar nombres
nombres = usuarios_filtrados['nombre'].tolist()
print("Usuarios mayores de 20 años (España, Francia, Turquía):")
for nombre in nombres:
    print("-", nombre)
print(f"\nTotal: {len(nombres)} usuarios\n")

# Contar género
conteo_genero = usuarios_filtrados['genero'].value_counts()

# Graficar
plt.figure(figsize=(6, 4))
conteo_genero.plot(kind='bar', color=['skyblue', 'lightpink'])
plt.title('Usuarios > 20 años (España, Francia, Turquía)')
plt.ylabel('Cantidad')
plt.xticks(rotation=0)
plt.grid(axis='y', linestyle='--', alpha=0.6)
plt.tight_layout()
plt.show()
```
```python
import pandas as pd
import matplotlib.pyplot as plt

# Cargar el archivo CSV
df = pd.read_csv('users.csv')

# Filtrar usuarios entre 45 y 60 años
filtro = (df['edad'] >= 45) & (df['edad'] <= 60)
usuarios_filtrados = df[filtro]

# Contar género
conteo_genero = usuarios_filtrados['genero'].value_counts()
print("Usuarios entre 45 y 60 años:")
print(conteo_genero)
print(f"\nTotal: {usuarios_filtrados.shape[0]} usuarios\n")

# Graficar
plt.figure(figsize=(6, 4))
conteo_genero.plot(kind='bar', color=['skyblue', 'lightpink'])
plt.title('Usuarios entre 45 y 60 años')
plt.ylabel('Cantidad')
plt.xticks(rotation=0)
plt.grid(axis='y', linestyle='--', alpha=0.6)
plt.tight_layout()
plt.show()
```

# Proyecto_EDA

#Iniciamos mostrando los datos con un display(df.head()) nos mostrara una tabla de 5 x 81 columnas

Vamos con mostrar columnas  que es un print(df.info) esto nos mostrara las columnas que estan asi como el tipo
Vamos con lo siguiente que es print(df.corr(numeric_only=True)) que mostrará únicamente las correlaciones entre las columnas numéricas
mostramos SalePrice con un boxplot.
luego sacamos la informacion de el.
Usamos msno para determinar la cantidad de nulos que por lo visto fueron bastante
Despues sacamos la informacion de las variables de tipo objeto, esto nos entrega una tabla con esos datos.
Para checar los datos por curiosidad saque una grafica.
y otra solo de salePrice solo de sus correlaciones
con eso podemos ver las correlaciones que tiene lo puse para que muestre las 11 primeras correlaciones con ella.
Sacamos unos Diagramas de dispersión entre 'SalePrice' y sus variables correladas
Luego lo que hacemos un mapa de calor de correlaciones lo que hace es calcular, visualizar y mostrar las correlaciones entre todas las características (columnas numéricas) y la variable objetivo 'SalePrice'y imprime las correlaciones ordenadas en orden descendente para identificar las características más influyentes en la variable objetivo.
Luego genramos gráficos de caja para las variables numéricas y gráficos de conteo para las variables categóricas en el DataFrame, eso nos sirve para una visión rápida de la distribución y la variabilidad de las variables en los datos.
Mas adelante hacemos diagramas que esten fuertemente relacionadas con SalePrice, sus columnas.
Pasamos a tratar los datos.
Primero hacemos que nos muestre los nulos, luego creamos un limite, normalmente se haria con el 5% pero por la cantidad de datos vacios la ampliamos a 25 lo cual nos dice que el limite es de 365
luego decimos ponemos que nos muestre las columnas que superan ese limite.
Pasamos a elimiar las columnas que estan bajo el limite dicho.
Imprimimos una lista con los nulos que nos quedan que son los que superan el limite
Ahora pasamos con  non_null_counts = df_limpio.notnull().sum()
filtered_columns = non_null_counts[(non_null_counts >= 551 ) & (non_null_counts <= 1450)].index
df_filtered = df_limpio[filtered_columns]
print(df_filtered.isna().sum().sort_values(ascending=False)) esto que hace que desde el 551 de nulos hasta 1450 esas columnas se elminen, y luego imprima nuevamente todas las columnas para mostrar que no hay ningun nulo.
Por si acaso nomas vamos a hacer un moda.
nuevamente imprimimos para estar seguros y en efecto no hay nulos.
Imprimos los datos unicos para revisarlos antes de avanzar.
Vuelo a usar el boxplot de SalePrice y comparo con el de el inicio y verifico los cambios.
e igualmente uso msno.matrix.
Mostramos los graficos de las columnas numericas antes de hacer el rango intercuantilico
hacemos el rango intercuartilico para tartarlos
MOstramos los graficos y comparamos
Volvemos a imprimir los datos unicos, pero nos aparece que no hay ninguno para categorizar pero ese fue un error mio, lo hice con df_filtra que contienen los datos numericos, por que cuando estaba sacando el rango intercuantilico hice que solo en ese estuvieran esos tipos de datos, pero bueno retroocedo con el df_filtered para que ahora si me muestre los datos tipo "object" son bastantes.
Creo un ciclo para categorizaar las columnas asi mas facil.
Checo si hay inconsistencias.
Checo las correlaciones con un mapa de calor, son las correlaciones con SalePrice, con los datos categoricos, repito y hago lo mismo con los datos numericos.
uso un heatmap para de igual manera checar las correlaciones pero de mas cerca, lo vuelvo a hacer con los numericos y categoricos.
Luego como termine con dos DataFrame y por que quiero checar los datos y compararlos, entonces haciendo esto: "df_concatenado = pd.concat([df_filtra, df_filtered], axis=0)" uso los dos e imprimo un mapa de calor de ambos tipos.
Contesto preguntas-----
#1. ¿Con las variables numéricas que se tienen es suficiente para predecir la variable objetivo?
# Depende de las correlaciones que existan entre ellas, hay algunas positivas significativas, pero
#no es suficiente, se necesitaria de las variables categoricas.
#2. ¿Alguna de las variables categóricas servirá realmente para determinar la variable objetivo?
# Igualmente que con las variables numericas, se necesitan de ambas para poder predecir
---Termino con las preguntas---
Esta parte despues de las preguntas lo que hace es convertir las columnas en el DataFrame df_filtered a variables numéricas utilizando el "one-hot encoding" y luego combina estas nuevas variables codificadas con el DataFrame original df.
Se imprimen las correlaciones nuevamente pero ahora con los datos alterados por el one-hot enconding
Usamos un mapa de correlaciones para verificar.
luego pasamos a hacer uso del MultiColumnnLabelEnconder,
Luego mostramos el dataframe numerico, sin nulos asi que lo checamos con df_filtered = df_filtered.dropna()
df_filtered.info()
y tambien los demas datos
con df_filtered.info()
print("\nValores nulos por columna:")
print(df_filtered.isnull().sum())
tipos_de_datos = df_filtered.dtypes
print("\nTipos de datos por columna:")
print(tipos_de_datos)
correlaciones_con_saleprice = correlaciones['SalePrice'].sort_values(ascending=False)
top_10_correlaciones = correlaciones_con_saleprice[1:11]  
print("\nLas 10 variables más correlacionadas con SalePrice:")
print(top_10_correlaciones).
Fin..
Conclusiones, si bien el dataset tenia una gran cantidad de datos nulos, la eliminacion no perjudico en medida el resultado, si bien fue dificil saber como resolverlo puesto que hubo momentos en que me perdi o ya no sirvio y tuve que reiniciar, fue satisfactorio terminarlo, el uso de la moda tal vez se pregunte por que, bueno fue por que pense que seria lo mas correcto en caso de que sobrara pocos nulos, Tal vez no uso muy bien las estadisticas por ejemplo podria usar otro tipo para checar los datos o tambien tengo duda si la manera en la que categorize fue la correcta, en este momento creo que si por que al hacerlo en ciclo acortamos el tiempo para hacerlo uno por uno, tambien al inicio pense en no categorizar por que no me salian los datos tipo object, pero pues al final fue mi confucion, por que aunque se creara un df nuevo para ese tipo que solo tuviera numericos tambien cree el otro que contiene object, al final las imprimi juntas para comparar los datos de igual manera, y con eso tambien podria contestar una pregunta  de que si se puede predecir puesto que ya tienen los dos tipos de datos.
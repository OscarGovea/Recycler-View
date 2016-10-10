# Recycler View 
------------------
Un RecyclerView es un contenedor de elementos en forma de lista al igual que la clase ListView. Aunque ambos tienen la misma función, este nuevo elemento permite “reciclar” los ítems que ya no son visibles por el usuario debido al scrolling. Por lo que es ideal para proyectos que manejan grandes volúmenes de ítems que se actualizan constantemente, limitando la visibilidad de elementos.
Adicionalmente permite configurar una serie de animaciones para la eliminación, desplazamiento y creación de nuevos elementos en tiempo real.

La creación y administración de un RecyclerView es similar a la de un ListView. Se necesita una fuente de datos que provea la información lógica de cada elemento y un adaptador que los lea, interprete e infle. Pero también es necesario un nuevo elemento llamado LayoutManager.

El LayoutManager es el encargado de añadir y reusar los views en el recycler. Su función es calcular las posiciones fuera del foco del usuario y así reemplazar el contenido de un ítem fuera del volumen visual por el contenido de otro. Esto reduce los tiempos de ejecución, ya que el número de infladas es menor.

### Como usarlo
1. Para usar el RecyclerView en tus proyectos Android Studio es necesario añadir la siguiente dependencia al sistema de construcción Gradle. Esto es debido a que este widget hace parte de la librería soporte v7 para manejar la compatibilidad:
```
compile 'com.android.support:recyclerview-v7:21.0.+'
```

2. Seguidamente definiremos nuestro RecyclerView en el layout donde lo queremos incluir:
```
<android.support.v7.widget.RecyclerView
        android:id="@+id/recycler_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
```
3. Creamos otro layout que definirá la interfaz de los elementos de la lista, en nuestro caso un simple TextView:
```
<RelativeLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <TextView
            android:id="@+id/title"
            android:layout_width="match_parent"
            android:layout_height="20dp" />
</RelativeLayout>
```
### ¿Contras?
Aunque tiene la ventaja de soportar multitud de animaciones muy eficientes para cuando creamos, editamos y eliminamos un elemento, carece de otras funcionalidades básicas, como lo son:
> - No tiene un método para implementar empty views o lo que es lo mismo, imágenes/texto para cuando no hay ningún elemento en la lista. 
> - No dispone de un método que recoja la pulsación del elemento. Lo que antes era el OnItemClick(), por lo que deberemos implementar esta funcionalidad por nuestra cuenta en los Adapters. 
> - Es un poco más tedioso de implementar y trabajar que con otras views. 
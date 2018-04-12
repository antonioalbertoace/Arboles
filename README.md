package arbol;

public class Arbol { private NodoArbol raiz;

public Arbol() { raiz = null; }

public void insertarNodo( int valorInsertar ) { if ( raiz == null ) raiz = new NodoArbol( valorInsertar ); else raiz.insertar( valorInsertar ); } public void recorridoPreorden() { ayudantePreorden( raiz ); } // fin del método recorridoPreorden // método recursivo para realizar el recorrido preorden private void ayudantePreorden( NodoArbol nodo ) { if ( nodo == null ) return; 
System.out.printf( "%d ", nodo.datos ); ayudantePreorden( nodo.nodoIzq ); ayudantePreorden( nodo.nodoDer ); }

public void recorridoInorden() { ayudanteInorden( raiz ); } private void ayudanteInorden( NodoArbol nodo ) { if ( nodo == null ) return; ayudanteInorden( nodo.nodoIzq ); System.out.printf( "%d ", nodo.datos ); ayudanteInorden( nodo.nodoDer ); }

public void recorridoPostorden() { ayudantePostorden( raiz ); } private void ayudantePostorden( NodoArbol nodo ) { if ( nodo == null ) return; ayudantePostorden( nodo.nodoIzq ); ayudantePostorden( nodo.nodoDer ); System.out.printf( "%d ", nodo.datos ); } }

class NodoArbol {

NodoArbol nodoIzq; int datos; NodoArbol nodoDer;

public NodoArbol( int datosNodo ) { datos = datosNodo; nodoIzq = nodoDer = null; }

public void insertar( int valorInsertar ){

if ( valorInsertar < datos ) {
if ( nodoIzq == null ){

nodoIzq = new NodoArbol( valorInsertar ); nodoIzq.insertar( valorInsertar ); } else if ( valorInsertar > datos ) { // inserta nuevo NodoArbol if ( nodoDer == null ) nodoDer = new NodoArbol( valorInsertar ); else nodoDer.insertar( valorInsertar ); } }
} }

import java.util.Random;

public class PruebaArbol { public static void main( String args[] ) { Arbol arbol = new Arbol(); int valor; Random numeroAleatorio = new Random();

System.out.println( "Insertando los siguientes valores: " );

// inserta 10 enteros aleatorios de 0 a 99 en arbol for ( int i = 1; i <= 9; i++ ) { valor = numeroAleatorio.nextInt( 100 ); System.out.print( valor + " " ); arbol.insertarNodo( valor ); } // fin de for

System.out.println ( "\n\nRecorrido preorden" ); arbol.recorridoPreorden(); // realiza recorrido preorden de arbol

System.out.println ( "\n\nRecorrido inorden" ); arbol.recorridoInorden(); // realiza recorrido inorden de arbol

System.out.println ( "\n\nRecorrido postorden" ); arbol.recorridoPostorden(); // realiza recorrido postorden de arbol System.out.println(); } // fin de main } // fin de la clase PruebaArbol

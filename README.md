import java.util.ArrayList;
import java.util.List;

class NodoGeneral<T> {
    private T dato;
    private List<NodoGeneral<T>> hijos;

    public NodoGeneral(T dato) {
        this.dato = dato;
        this.hijos = new ArrayList<>();
    }

    public void agregarHijo(NodoGeneral<T> hijo) {
        this.hijos.add(hijo);
    }

    public T getDato() {
        return dato;
    }

    public List<NodoGeneral<T>> getHijos() {
        return hijos;
    }

    // Método auxiliar para imprimir el árbol en formato jerárquico por consola
    public void imprimirArbol(String prefijo) {
        System.out.println(prefijo + "└── " + dato);
        for (NodoGeneral<T> hijo : hijos) {
            hijo.imprimirArbol(prefijo + "    ");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        // Nivel 0 (Raíz) - Nodo 1
        NodoGeneral<String> raiz = new NodoGeneral<>("Empresa");

        // Nivel 1 - Nodos 2 y 3
        NodoGeneral<String> tec = new NodoGeneral<>("Tecnología");
        NodoGeneral<String> fin = new NodoGeneral<>("Finanzas");

        raiz.agregarHijo(tec);
        raiz.agregarHijo(fin);

        // Nivel 2 - Nodos 4, 5, 6 y 7
        NodoGeneral<String> devOps = new NodoGeneral<>("DevOps");
        NodoGeneral<String> backend = new NodoGeneral<>("Backend");
        NodoGeneral<String> frontend = new NodoGeneral<>("Frontend");
        NodoGeneral<String> contabilidad = new NodoGeneral<>("Contabilidad");

        tec.agregarHijo(devOps);
        tec.agregarHijo(backend);
        tec.agregarHijo(frontend);
        fin.agregarHijo(contabilidad);

        // Nivel 3 - Nodos 8 y 9 (Supera el mínimo de 8 nodos y 3 niveles requeridos)
        NodoGeneral<String> reactSpec = new NodoGeneral<>("Especialista React");
        NodoGeneral<String> auditoria = new NodoGeneral<>("Auditoría Interna");

        frontend.agregarHijo(reactSpec);
        contabilidad.agregarHijo(auditoria);

        // Visualización por consola
        System.out.println("Estructura Jerárquica del Árbol General:\n");
        raiz.imprimirArbol("");
    }
}

# Código 1
---

    class A
     {
        public int a;

        public A()

        {
            a = 10;
        }

        public virtual string Display()

        {
            return a.ToString();
        }
    }

    class B : A

    {
        public int b;

        public B() : base()

        {
            b = 15;
        }
        public override string Display()
        {
            return b.ToString();
        }
    }
    class Program
    {
        static void Main(string[] args)
        {           
                A objA = new A();

                B objB = new B();

                Console.WriteLine(objA.Display()); 

                Console.WriteLine(objB.Display());   
            Console.ReadLine();
        }
    }



> En los valores que se imprimen al final, se miran las variables A y B, los cuales se le agregaron los números 10 y 15 respectivamente. 
> Una vez redefinido el método Display con virtual, el resultado que imprime es el mismo. Por lo cual una buena forma de agregar la palabra que hace falta en `public _______ string Display()` es virtual.


#Código dos.
---
    abstract class Musico
     {
        public string nombre;
        public Musico(string n)
        {
            nombre = n;
        }
        public abstract void Afina(); 

        public string Display()
        {
            return nombre;
        }
     }
     class Bajista: Musico

     {
        public string instrumento;        

        public Bajista(string n, string i) : base(n)
        {
            instrumento = i;
        }
        public override void Afina()
        {
            Console.WriteLine("Hola soy bajista uso un {0} y me llamo {1}", instrumento, nombre);
        }
        public string display ()
        {
            return instrumento;
        }
     }

    class Guitarrista : Musico
    {
        public string instrumento;
        public Guitarrista(string n, string j) : base(n)
        {
            instrumento = j;
        }
        public override void Afina()
        {
            Console.WriteLine("Hola soy Guitarrista uso una {0} y me llamo {1}", instrumento, nombre);
        }
        public string display ()
        {
            return instrumento;
        }
    }
    class Program
    {
    static void Main(string[] args)

    {
        Bajista b = new Bajista("Flea", "bajo");
            b.Afina();
        Guitarrista g = new Guitarrista("Santana","Guitarra");
            g.Afina();

            List<Musico> musicos = new List<Musico>();
            musicos.Add(b);
             musicos.Add(g); 
            foreach (Musico mi in musicos)
            {
                Console.WriteLine(mi.Display());
            }
         Console.ReadKey();

> El la letra "B" hay un error, porque no puedes ingresar una instancia en una clase abstracta.
> 
> En todas las clases hijas que hereden de una clase abstracta, deben de implementar obligatoriamente los métodos que aquella clase padre contrae.
> 
> Cuando creas una clase abstracta, no lleva llaves más que un punto y coma, por que es obligación de las clases hijas implementar todos los métodos de la clase abstracta padre.
> 
> Si al método `Afina()` se le agrega virtual en lugar de la abstrac, todas las demás clases que hereden de ella y tengas el método `Afina()` se le debe de agregar override para que cuando la manden a llamar salga con el método de dicha clase.  

##Código con la interfaz `IAfina()`

    interface IAfina
    {
         void Afina();
    }
    abstract class Musico

    {
        public string nombre;

        public Musico(string n)

        {

            nombre = n;

        }


        public string Display()
        {
            return nombre;
        }

    }

    class Bajista : Musico, IAfina

    {

        public string instrumento;

        public Bajista(string n, string i) : base(n)
        {
            instrumento = i;
        }
        public void Afina()
        {
            Console.WriteLine("Hola soy bajista uso un {0} y me llamo {1}", instrumento, nombre);
        }
        public string display()
        {
            return instrumento;
        }

    }

    class Guitarrista : Musico, IAfina
    {
        public string instrumento;
        public Guitarrista(string n, string j) : base(n)
        {
            instrumento = j;
        }
        public void Afina()
        {
            Console.WriteLine("Hola soy Guitarrista uso una {0} y me llamo {1}", instrumento, nombre);
        }
        public string display()
        {
            return instrumento;
        }
    }
    class Program
    {
        static void Main(string[] args)

        {
            Bajista b = new Bajista("Flea", "bajo");
            b.Afina();
            Guitarrista g = new Guitarrista("Santana", "Guitarra");
            g.Afina();

            List<Musico> musicos = new List<Musico>();
            musicos.Add(g);
            musicos.Add(b);            
            foreach (Musico mi in musicos)
            {
                Console.WriteLine(mi.Display());
                Console.WriteLine("---------------------------");
                (mi as IAfina).Afina();
            }
            Console.ReadKey();
        }

    }

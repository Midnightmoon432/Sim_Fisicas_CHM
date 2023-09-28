# Hola Mundo

![Mundo](D:\obsidian\hola_mundo\gravedadsimulacion.jpg)
## Código


```c
#include <iostream>  
#include <Box2d/Box2d.h>  
  
int main() {  
    //Creacion del mundo y de la gravedad  
    b2Vec2 gravity(0.0f, -9.81f);  
    b2World world(gravity);  
  
    //Caracteristicas del cuerpo  
    b2BodyDef groundBodyDef;  
    groundBodyDef.position.Set(0.0f, -10.0f);  
    //Creamos el cuerpo  
    b2Body * groundBody = world.CreateBody(&groundBodyDef);  
  
    //Crear la forma  
    b2PolygonShape groundBox;  
    groundBox.SetAsBox(50.0f,1.0f);  
  
    groundBody ->CreateFixture(&groundBox, 0.0f);  
  
    b2BodyDef bodyDef;  
    bodyDef.type = b2_dynamicBody;  
    bodyDef.position.Set(0.0f, 20.f);  
    b2Body * body = world.CreateBody(&bodyDef);  
    b2PolygonShape dynamicBox;  
    dynamicBox.SetAsBox(1.0f,1.0f);  
    b2FixtureDef fixtureDef;  
    fixtureDef.shape = &dynamicBox;  
    fixtureDef.density = 1.0f;  
    fixtureDef.friction = 0.3f;  
  
    body ->CreateFixture(&fixtureDef);  
  
    float timeStep = 1.0f/60.0f;  
    int32 velocityIterations = 6;  
    int32 positionIterations = 2;  
  
    for (int32 i = 0; i < 60; ++i)  
    {  
        world.Step(timeStep, velocityIterations, positionIterations);  
        b2Vec2 position = body->GetPosition();  
        float angle = body->GetAngle();  
        printf("%4.2f %4.2f %4.2f\n", position.x, position.y, angle);  
  
  
    }  
}

````
```c
```
``
## Explicación

1. En el código lo primero que hacemos es crear la gravedad que es vital para que la simulación funcione, la agregamos como un vector 2 de b2 ya que es una fuerza y establecemos la fuerza en el vector y como negativa pues va hacia abajo, después hacemos el mundo con b2 world y le agregamos la gravedad
2. Después definimos las características de un suelo para la simulación, primero la posición [.position.Set(0.0f, -10.0f);] y después le damos una forma que es de caja [.SetAsBox(50.0f,1.0f);]
3. Luego necesitamos un objeto para hacer la simulación, entonces primero se define que va a ser un cuerpo dinámico,  para eso se pone [bodyDef.type = b2_dynamicBody;], tenemos que definir su posición en el mundo con [.position.Set(0.0f, 20.f)] y después tenemos que definir su forma que igual es de caja. Para que la simulación sea mas realista tenemos que definir las propiedades del objeto, en este caso definimos 2 propiedades principales, la primera es la densidad y la segunda es la fricción y las definimos con [.density = 1.0f;] y [.friction = 0.3f;] y al final le asignamos estas características al objeto dinámico
4. Por ultimo necesitamos que la simulación funcione, para eso agregamos el tiempo que funciona por iteraciones, en este caso es de 1 a 60, cada iteración se llama al mundo para avanzar en la simulación y se da la posición del objeto de la simulación

## Lógica del mundo

**<font color="pink">Gravedad</font>
La gravedad es un fenómeno en el que los objetos que tienen masa se atraen, se mide en newtons, es mas notorio el efecto en cuerpos muy grandes con mucha masa como son los planetas

**<font color="green">Densidad</font>
La densidad es la relacion entre la masa y el volumen de los objetos

**<font color="yellow">Friccion</font>
Es la fuerza existente entre dos superficies que se encuentren en contacto, y tiene dirección contraria al movimiento.

**<font color="orange">Iteracion</font>
Una iteración es una repetición de un proceso, en este caso lo usamos para simular el tiempo

## Elementos para el código

**<font color="red">Cmake</font>**
cmake es un software libre que sirve para la construcción de software y para facilitar la compilación de programas en diferentes plataformas y entornos, cuenta con múltiples herramientas para ayudar a todo eso.

**<font color="blue">Box2D</font>
Box2D es una biblioteca de código abierto que se utiliza para las simulaciones de físicas, se centra ne objetos rigidos.

**<font color="purple">CLion</font>
Clion es un entorno de desarrollo integrado que esta bastante completo.
# Hola Luna

![Luna](D:\obsidian\hola_mundo\hola_luna\luna.jpg)
## Código


```c
#include <iostream>  
#include <Box2d/Box2d.h>  
  
int main() {  
    //Creacion del mundo y de la gravedad  
    b2Vec2 gravity(0.0f, -1.623f);  
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
    fixtureDef.friction = 0;  
  
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

## Explicación

**<font color="yellow">Cambios</font>
Los cambios en hola luna con respecto a hola mundo son únicamente la gravedad del mundo puesto que en la luna la gravedad es de -1.623 mientras que en la tierra es de -9.81 y la friccion en la que le puse 0.
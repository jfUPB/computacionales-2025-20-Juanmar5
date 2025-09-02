# Evidencias para la unidad 4

## Código

Código para ofApp.h:

``` cpp
ofApp.h
#pragma once
#include "ofMain.h"

// Nodo de la cola
struct Node {
    float x, y;
    float radius;
    ofColor color;
    float opacity;
    Node* next;

    Node(float _x, float _y, float _radius, ofColor _color, float _opacity)
        : x(_x), y(_y), radius(_radius), color(_color), opacity(_opacity), next(nullptr) {
    }
};

// Implementación manual de una cola (FIFO)
class BrushQueue {
public:
    Node* front;
    Node* rear;
    int size;
    int maxSize;

    BrushQueue(int _maxSize);
    ~BrushQueue();

    void enqueue(float x, float y, float radius, ofColor color, float opacity);
    void dequeue();
    void clear();
    bool isEmpty();
};

//--------------------------------------------------------------
// Constructor
BrushQueue::BrushQueue(int _maxSize) : front(nullptr), rear(nullptr), size(0), maxSize(_maxSize) {}

// Destructor
BrushQueue::~BrushQueue() {
    clear();
}

// Enqueue (agregar al final)
void BrushQueue::enqueue(float x, float y, float radius, ofColor color, float opacity) {
    Node* newNode = new Node(x, y, radius, color, opacity);

    if (rear == nullptr) { // cola vacía
        front = rear = newNode;
    } else {
        rear->next = newNode;
        rear = newNode;
    }
    size++;

    if (size > maxSize) {
        dequeue();
    }
}

// Dequeue (eliminar el más antiguo = frente de la cola)
void BrushQueue::dequeue() {
    if (front == nullptr) return;

    Node* temp = front;
    front = front->next;
    if (front == nullptr) { // si ya no queda nada
        rear = nullptr;
    }
    delete temp;
    size--;
}

// Clear (vaciar cola)
void BrushQueue::clear() {
    while (front != nullptr) {
        dequeue();
    }
}

// Cola vacía
bool BrushQueue::isEmpty() {
    return size == 0;
}


//--------------------------------------------------------------
class ofApp : public ofBaseApp {
public:
    BrushQueue strokes; // Cola de trazos
    float backgroundHue = 0;
    int currentMaxSize = 50;

    ofApp() : strokes(50) {} // Tamaño máximo inicial de la cola

    void setup();
    void update();
    void draw();
    void keyPressed(int key);
};
```

Código para ofApp.cpp:

``` cpp
ofApp.cpp
#include "ofApp.h"

//--------------------------------------------------------------
void ofApp::setup() {
    ofBackground(0);
    ofSetFrameRate(60);
}

//--------------------------------------------------------------
void ofApp::update() {
    backgroundHue += 0.2;
    if (backgroundHue > 255) backgroundHue = 0;

    // Si el mouse está presionado, añadir un nuevo trazo
    if (ofGetMousePressed()) {
        float x = ofGetMouseX();
        float y = ofGetMouseY();
        float radius = ofRandom(5, 20);
        ofColor color;
        color.setHsb(ofRandom(255), 200, 255);
        float opacity = ofRandom(50, 255);

        strokes.enqueue(x, y, radius, color, opacity);
    }
}

//--------------------------------------------------------------
void ofApp::draw() {
    // Fondo con gradiente dinámico
    ofColor color1, color2;
    color1.setHsb(backgroundHue, 150, 240);
    color2.setHsb(fmod(backgroundHue + 128, 255), 150, 240);
    ofBackgroundGradient(color1, color2, OF_GRADIENT_LINEAR);

    // Dibujar trazos en la cola
    Node* current = strokes.front;
    while (current != nullptr) {
        ofSetColor(current->color, current->opacity);
        ofDrawCircle(current->x, current->y, current->radius);
        current = current->next;
    }
}

//--------------------------------------------------------------
void ofApp::keyPressed(int key) {
    if (key == 'c') {
        strokes.clear();
    }
    else if (key == 'a') {
        // Alternar entre 50 y 100
        currentMaxSize = (currentMaxSize == 50) ? 100 : 50;
        strokes.maxSize = currentMaxSize;
        ofLogNotice() << "maxSize = " << currentMaxSize;
    }
    else if (key == 's') {
        ofSaveFrame();
    }
}
```

Código para main.cpp:
``` cpp
main.cpp
#include "ofMain.h"
#include "ofApp.h"

//========================================================================
int main() {
    ofSetupOpenGL(1024, 768, OF_WINDOW);
    ofRunApp(new ofApp());
}
```

## Demostración:

[Aquí está el video demostrativo de mi aplicación]([url del video no listado en youtube](https://youtu.be/vAlmbpqwiv8)



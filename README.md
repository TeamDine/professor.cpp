# professor.cpp
//Clase maestra de los datos professor
#include "professor.h"

Professor::Professor(){
    formacion = -1;
    produccion = -1;
    docencia = -1;
    tutoria = -1;
}

/******************************** DATOS PERSONALES ****************************************/
void Professor::setData(PersonalData& p) {
    data = p;
    }

PersonalData Professor::getData() {
    return data;
    }

/******************************** FORMACION ACADEMICA ****************************************/
bool Professor::emptyFormation() {
    return formacion == -1;
    }

bool Professor::fullFormation() {
    return formacion == 10;
    }

void Professor::insertFormation(int& p, Formation& f) {
    if(fullFormation()) {
        throw ListException ("\t\t\tDesbordamiento de datos\n\t\t***ERROR: EN INSERCION DE DATOS (FORMACION ACADEMICA)***");
        }
    schoolarship[p+1] = f;
    formacion++;
    }

void Professor::deleteFormation(int& p) {
    if(emptyFormation()){
        throw ListException ("Desbordamiento de datos\n\t\t***ERROR: EN ELIMINACION DE DATOS (FORMACION ACADEMICA)***");
    }
    int i = p;
    while( i < formacion ) {
        schoolarship[i] = schoolarship[i+1];
        i++;
        }
    formacion--;
    }

int Professor::getLastFormation() {
    if(emptyFormation()){
        return -1;
    }
    return formacion;
    }

int Professor::getFirstFormation() {
    if(emptyFormation()){
        return -1;
    }
    return 0;
    }

Formation Professor::returnFormation(const int& p) {
    if(emptyFormation() or p < 0 or p > formacion){
        throw ListException ("Desbordamiento de datos\n\t\t***ERROR: EN BUSQUEDA DE DATOS (FORMACION ACADEMICA)***");
    }
    return schoolarship[p];
    }

bool Professor::findFormation(std::string& id) {
    for (int i = 0; i < formacion; i++){
        if (id == schoolarship[i].getIdCard()){
            return true;
        }
    }
    return false;
}

std::string Professor::toStringFormation() {
    std::string result;

    for(int i = 0; i <= formacion; i++){
        result += "Grado: ";
        result += schoolarship[i].getGrade();
        result += "Carrera: ";
        result += schoolarship[i].getGradeName();
        result += "Institucion: ";
        result += schoolarship[i].getInstitution();
        result += "Fecha ingreso: ";
        result += schoolarship[i].getBeginDate().toString();
        result += "Fecha egreso: ";
        result += schoolarship[i].getFinishDate().toString();
        result += "Fecha Titulo: ";
        result += schoolarship[i].getDegreeDate().toString();
        result += "ID: ";
        result += schoolarship[i].getIdCard();
        result += "\n";
    }
    return result;
    }

/******************************** PRODUCCION ACADEMICA ****************************************/


bool Professor::emptyProduction() {
    return produccion == -1;
    }

bool Professor::fullProduction() {
    return produccion == 10;
    }

void Professor::insertProduction(int& p, AcademicProduction& a) {
    if(fullProduction()) {
        throw ListException ("\t\t\tDesbordamiento de datos\n\t\t***ERROR: EN INSERCION DE DATOS (PRODUCCION ACADEMICA)***");
        }
    perfomance[p+1] = a;
    produccion++;
    }

void Professor::deleteProduction(int& p) {
    if(emptyProduction()){
        throw ListException ("Desbordamiento de datos\n\t\t***ERROR: EN ELIMINACION DE DATOS (PRODUCCION ACADEMICA)***");
    }
    int i = p;
    while( i < produccion ) {
        perfomance[i] = perfomance[i+1];
        i++;
        }
    produccion--;
    }

int Professor::getLastProduction() {
    if(emptyProduction()){
        return -1;
    }
    return produccion;
    }

int Professor::getFirstProduction() {
    if(emptyProduction()){
        return -1;
    }
    return 0;
    }

AcademicProduction Professor::returnProduction(const int& p) {
    if(emptyProduction() or p < 0 or p > produccion){
        throw ListException ("Desbordamiento de datos\n\t\t***ERROR: EN BUSQUEDA DE DATOS (PRODUCCION ACADEMICA)***");
    }
    return perfomance[p];
    }

bool Professor::findProduction(std::string& id) {
    for(int i = 0; i < produccion; i++){
        if (id == perfomance[i].getId()){
            return true;
        }
    }
    return false;
}

std::string Professor::toStringProduction() {
    std::string result;

    for(int i = 0; i <= produccion; i++){
        result += "Nombre: ";
        result += perfomance[i].getName();
        result += "Tipo: ";
        result += perfomance[i].getType();
        result += "Fecha: ";
        result += perfomance[i].getElaborationDate().toString();
        result += "Co-Autor: ";
        result += perfomance[i].getAuthor().toString();
        result += "ID: ";
        result += perfomance[i].getId();
        result += "Status: ";
        result += perfomance[i].getStatus();
        result += "\n";
    }
    return result;
    }


bool Professor::emptyCourses() {
    return docencia == -1;
    }

bool Professor::fullCourses() {
    return docencia == 10;
    }

void Professor::insertCourses(int& p, Courses& c) {
    if(fullCourses()) {
        throw ListException ("\t\t\tDesbordamiento de datos\n\t\t***ERROR: EN INSERCION DE DATOS (DOCENCIA)***");
        }
    courses[p+1] = c;
    docencia++;
    }

void Professor::deleteCourses(int& p) {
    if(emptyCourses()){
        throw ListException ("Desbordamiento de datos\n\t\t***ERROR: EN ELIMINACION DE DATOS (DOCENCIA)***");
    }
    int i = p;
    while( i < docencia ) {
        courses[i] = courses[i+1];
        i++;
        }
    docencia--;
    }

int Professor::getLastCourses() {
    if(emptyCourses()){
        return -1;
    }
    return docencia;
    }

int Professor::getFirstCourses() {
    if(emptyCourses()){
        return -1;
    }
    return 0;
    }

Courses Professor::returnCourse(const int& p) {
    if(emptyCourses() or p < 0 or p > docencia){
        throw ListException ("Desbordamiento de datos\n\t\t***ERROR: EN BUSQUEDA DE DATOS (DOCENCIA)***");
    }
    return courses[p];
    }

bool Professor::findCourses(std::string& n) {
    for (int i = 0; i < docencia; i++){
        if (n == courses[i].getName()){
            return true;
        }
    }
    return false;
    }

std::string Professor::toStringCourses() {
    std::string result;
    
    for( int i = 0; i <= docencia; i++){
        result += courses[i].toString();
        result += "\n";
    }
    
    return result;

bool Professor::emptyTutorial() {
    return tutoria == -1;
    }

bool Professor::fullTutorial() {
    return tutoria == 10;
    }

void Professor::insertTutorial(int& p, Tutorial& t) {
    if(fullTutorial()) {
        throw ListException ("\t\t\tDesbordamiento de datos\n\t\t***ERROR: EN INSERCION DE DATOS (TUTORIAS)***");
        }
    student[p+1] = a;
    tutoria++;
    }

void Professor::deleteTutorial(int& p) {
    if(emptyTutorial()){
        throw ListException ("Desbordamiento de datos\n\t\t***ERROR: EN ELIMINACION DE DATOS (TUTORIAS)***");
    }
    int i = p;
    while( i < tutoria ) {
        student[i] = student[i+1];
        i++;
        }
    tutoria--;
    }

int Professor::getLastTutorial() {
    if(emptyTutorial()){
        return -1;
    }
    return tutoria;
    }

int Professor::getFirstTutorial() {
    if(emptyTutorial()){
        return -1;
    }
    return 0;
    }

Tutorial Professor::returnTutorial(const int& p) {
    if(emptyTutorial() or p < 0 or p > tutoria){
        throw ListException ("Desbordamiento de datos\n\t\t***ERROR: EN BUSQUEDA DE DATOS (TUTORIAS)***");
    }
    return student[p];
    }

bool Professor::findTutorial(Name& n) {
    for(int i = 0; i < tutoria; i++){
        if (n.toString() == student[i].toString()){
            return true;
        }
    }
    return false;
    }

std::string Professor::toStringTutorial() {
    std::string result;
    
    for( int i = 0; i <= tutoria; i++){
        result += student[i].toString();
        result += "\n";
    }
    
    return result;
    }

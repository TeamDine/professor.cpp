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

    }

bool Professor::fullCourses() {

    }

void Professor::insertCourses(int&, Courses&) {

    }

void Professor::deleteCourses(int&) {

    }

int Professor::getLastCourses() {

    }

int Professor::getFirstCourses() {

    }

Courses Professor::returnCourse(const int&) {

    }

bool Professor::findCourses(std::string&) {

    }

std::string Professor::toStringCourses() {

    }
/***
bool Professor::emptyTutorial() {

    }

bool Professor::fullTutorial() {

    }

void Professor::insertTutorial(int&, Tutorial&) {

    }

void Professor::deleteTutorial(int&) {

    }

int Professor::getLastTutorial() {

    }

int Professor::getFirstTutorial() {

    }

Tutorial Professor::returnTutorial(const int&) {

    }

bool Professor::findTutorial(std::string&) {

    }

std::string Professor::toStringTutorial() {

    }
**/

# Angular-steps
## TypeScript:
https://www.tutorialspoint.com/typescript/
```
let animal = "chien";

console.log(animal);
console.log (typeof animal);

/** *************************** */

let chiffre = 21;
let letter = '21';

console.log(typeof chiffre);
console.log(typeof letter);
console.log(chiffre == letter);
console.log(chiffre === letter);

/***** */

enum Jobs {
  ING = "Ingénieur",
  POLICE = "police",
  MEDCIN = "medcin",
};

 const job:string = Jobs.POLICE
 console.log(job)

/** *************************** */


class Animal{
  name:string;
  age:number;

  constructor(name:string, age:number){
    this.name= name;
    this.age =age;
  }
}

const chien:Animal = new Animal('chien', 2);
console.log(chien);
console.log(typeof chien);

/** *************************** */

interface Objet{
    name:string;
    taille?:number;
}

var Objet:Objet = {name:'table'}
console.log(Objet);
console.log(typeof Objet);

/** *************************** */

function getLine(animal:Animal):string{
   return `ce ${animal.name} a ${animal.age} ans`;
}

let getAge = (animal:Animal):string => {
  return `${animal.age} ans`;
}

console.log(getLine(chien));
console.log(getAge(chien));

/** *************************** */

let tab:Array<string> =['Alex', 'John', 'David'];
let numbersTab:number[] =[20,150,100,2,69,45,30];

tab.forEach((elm:string) =>  console.log(elm));
let shnapSot = tab.map((elm:string) =>  {
  if(elm==="Alex"){
    return "Stephane"
  }
  return elm
});
let filtredTab = numbersTab.filter((elm:number) => elm >= 50);

console.log(shnapSot);
console.log(filtredTab);


/************************
 * Exercice: 
 *   On a une liste des développeurs, chacun a comme paramètres :
 *     - name: son nom,
 *     - age: son âge,
 *     - titre: son titre qu'est soit Junior, Confirmé ou Sénior,
 *     - nbExp: le nombre d'expérience,
 *     - salaire: son salaire, un chiffre en euros,
 *     - spectialite: sa spécialité soit qu'est Back, font ou Fullstack.
 *   On a 5 développeurs :
 *    - Alex, 28 ans, 4 ans d'expérience et il est back.
 *    - David, 32 ans, 8 ans d'expérience et il est fullStack.
 *    - John, 26 ans, 2 ans d'expérience et il est front.
 *    - Stéphane, 35 ans, 12 ans d'expérience et il est fullStack.
 *    - kathy, 27 ans, 3 années d'expérience et elle est back.
 *   Pour affecter les salaires on a 3 règles :
 *    1/ entre 0 et 3 ans d'exp, le développeur est Junior et son salaire est 38k.
 *    2/ entre 4 et 6 ans d'exp, le développeur est Confirmé est son salaire est 45k.
 *    3/ plus que 6 ans d'exp, le développeur est sénior et son salaire est 60k.
 *   Notre objectif est de :
 *   1/ Coder une fonction pour créer la liste des développeurs.
 *   2/ Coder une fonction qui affiche les développeurs par spécialité choisie.
 *   3/ Coder une fonction qui affiche les développeurs choisis par n'importe quel paramètre.
 */
enum Speciality {
  BACK='Backend',
  FRONT='Frontend',
  FULLSTACK='FullStack',
}

enum Title {
  JUNIOR='Junior',
  CONFIRME='Confirmé',
  SERNIOR='Sénior',
}

enum Salary {
  JUNIOR= 38,
  CONFIRME= 45,
  SERNIOR= 60,
}

interface InitDeveloper {
  name:string;
  age:number;
  nbExp: number;
  speciality: string;  
}

class Developer {
  name: string;
  age:number;
  title:string;
  nbExp:number;
  salary:number;
  speciality:string;

  constructor(name: string, age:number, title:string, nbExp:number, salary:number, speciality:string){
    this.name = name;
    this.age = age;
    this.title = title;
    this.nbExp = nbExp;
    this.salary = salary;
    this.speciality = speciality;
  }
}

const devDataBase: InitDeveloper[] =[
  {name:'Alex', age:28, nbExp:4, speciality:Speciality.BACK},
  {name:'David', age:32, nbExp:8, speciality:Speciality.FULLSTACK},
  {name:'John', age:26, nbExp:2, speciality:Speciality.FRONT},
  {name:'Stéphane', age:35, nbExp:12, speciality:Speciality.FULLSTACK},
  {name:'kathy', age:27, nbExp:3, speciality:Speciality.BACK},
]

let developers: Developer[] =[];

function getTitle(nbExp:number):string{
   let title:string = '';
   if(0 <= nbExp && nbExp <= 3){
     title = Title.JUNIOR;
   }else if(4 <= nbExp && nbExp <= 6){
     title = Title.CONFIRME;
   } else {
     title = Title.SERNIOR;
   }
   return title;
}

function getSalary(nbExp:number):number{
   let salary:number = 0;
   if(0 <= nbExp && nbExp <= 3){
     salary = Salary.JUNIOR;
   }else if(4 <= nbExp && nbExp <= 6){
     salary = Salary.CONFIRME;
   } else {
     salary = Salary.SERNIOR;
   }
   return salary;
}

function InsertDevs () {
  let tabDev: Developer[] =[];

   devDataBase.forEach((dev:InitDeveloper) => {
     tabDev.push(new Developer(dev.name, dev.age,getTitle(dev.nbExp),dev.nbExp,getSalary(dev.nbExp), dev.speciality ))
   })

   return tabDev;
}

developers = InsertDevs();

function getDevBySpeciality (speciality:string):Array<Developer>{
  let filtredDevs:Array<Developer> = [];
  filtredDevs = developers.filter((dev:Developer) => dev.speciality === speciality);
  return filtredDevs;
}

function getDevByParam (param:string, value:string|number):Array<Developer>{
  let filtredDevs:Array<Developer> = [];
  filtredDevs = developers.filter((dev:Developer) => dev[param] === value);
  return filtredDevs;
}

console.log(getDevByParam("speciality",Speciality.FRONT));
```

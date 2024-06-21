<div align="center">
  <h1> 30 Günde React: Array-leri map-lemek </h1>
  <a class="header-badge" target="_blank" href="https://www.linkedin.com/in/asabeneh/">
  <img src="https://img.shields.io/badge/style--5eba00.svg?label=LinkedIn&logo=linkedin&style=social">
  </a>
  <a class="header-badge" target="_blank" href="https://twitter.com/Asabeneh">
  <img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/asabeneh?style=social">
  </a>

<sub>Awtor:
<a href="https://www.linkedin.com/in/asabeneh/" target="_blank">Asabeneh Yetayeh</a><br>
<small> Oktýabr, 2020</small>
</sub>

</div>

[<< Gün 5](./../05_Day_Props/05_props.md) | [Gün 7 >>](../07_Day_Class_Components/07_class_components.md)

![30 Günde React banner](../images/30_days_of_react_banner_day_6.jpg)

- [Array-leri map-lemek](#mapping-arrays)
  - [Array-leri map-lemek we render etmek (ekrana çykarmak)](#mapping-and-rendering-arrays)
    - [San saklaýan array-leri map-lemek](#mapping-array-of-numbers)
    - [Array saklaýan array-leri map-lemek](#mapping-array-of-arrays)
    - [Obýekt saklaýan array-leri map-lemek](#mapping-array-of-objects)
    - [Array map-lenende key-ler](#key-in-mapping-arrays)
- [Praktika](#exercises)
  - [Praktika: Dereje 1](#exercises-level-1)
  - [Praktika: Dereje 2](#exercises-level-2)
  - [Praktika: Dereje 3](#exercises-level-3)

# Array-leri map-lemek

Bir array, köp sanly meseläni çözmek üçin iň köp ulanylýan maglumat gurluşydyr. React-da bir array-iň  her bir elementine belli bir HTML elementini goşup, bir array-i  JSX elementine öwürmek üçin map ulanýarys.

## Array-leri map-lemenk we render etmek (ekrana çykarmak)

Köplenç maglumatlar bir array-iň içinde ýa-da array-iň içindäki obýektde gelýändir. Biz bu array-leri ýa-da array-iň içindäki obýektleri render etmek (brauzeriň ekranyna çykarmak) üçin _map_ ulanýarys. Geçen gezekki sapagymyzda biz  **techs**  diýen array-i map ulanyp render edipdik. A bu gezek bolsa bu tema barada has köp ekzamplýar göreris.

Aşakdaky meselemde, san saklaýan, setir ululyk (string) saklaýan, ýurtlary saklaýan (countries) we ukyplary saklaýan (skills)  array-leri nädip browser-e çykarmalydygyny görersiňiz. Ýagny nädip render etmelidigini.

```js
import React from 'react'
import ReactDOM from 'react-dom'
const App = () => {
  return (
    <div className='container'>
      <div>
        <h1>Numbers List</h1>
        {[1, 2, 3, 4, 5]}
      </div>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

Brauzeriňizi barlap görseňiz sanlaryň hemmesi bir setirde çykandygyny görersiňiz. Munuň öňüni almak üçin bir bu array-iň her bir elementini JSX-e öwüreris. Aşakdaky ekzamplýarda  array-iň elementleriniň JSX-e öwrülen halyny görüp bilersiňiz.

### San saklaýan array-leri map-lemek

```js
import React from 'react'
import ReactDOM from 'react-dom'

const Numbers = ({ numbers }) => {
  // modifying array to array of li JSX
  const list = numbers.map((number) => <li>{number}</li>)
  return list
}

// App component

const App = () => {
  const numbers = [1, 2, 3, 4, 5]

  return (
    <div className='container'>
      <div>
        <h1>Numbers List</h1>
        <ul>
          <Numbers numbers={numbers} />
        </ul>
      </div>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### Array saklaýan array-leri map-lemek

Aşakda munuň nädip edilendigi görkezilendir.

```js
import React from 'react'
import ReactDOM from 'react-dom'

const skills = [
  ['HTML', 10],
  ['CSS', 7],
  ['JavaScript', 9],
  ['React', 8],
]

// Skill Component
const Skill = ({ skill: [tech, level] }) => (
  <li>
    {tech} {level}
  </li>
)

// Skills Component
const Skills = ({ skills }) => {
  const skillsList = skills.map((skill) => <Skill skill={skill} />)
  console.log(skillsList)
  return <ul>{skillsList}</ul>
}

const App = () => {
  return (
    <div className='container'>
      <div>
        <h1>Skills Level</h1>
        <Skills skills={skills} />
      </div>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### Obýekt saklaýan array-leri map-lemek

Array-iň içindäki obýektleri render etmek.

```js
import React from 'react'
import ReactDOM from 'react-dom'

const countries = [
  { name: 'Finland', city: 'Helsinki' },
  { name: 'Sweden', city: 'Stockholm' },
  { name: 'Denmark', city: 'Copenhagen' },
  { name: 'Norway', city: 'Oslo' },
  { name: 'Iceland', city: 'Reykjavík' },
]

// Country component
const Country = ({ country: { name, city } }) => {
  return (
    <div>
      <h1>{name}</h1>
      <small>{city}</small>
    </div>
  )
}

// countries component
const Countries = ({ countries }) => {
  const countryList = countries.map((country) => <Country country={country} />)
  return <div>{countryList}</div>
}
// App component
const App = () => (
  <div className='container'>
    <div>
      <h1>Countries List</h1>
      <Countries countries={countries} />
    </div>
  </div>
)

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

### Array map-lenende key-ler

Key-ler React-a bir elementiň uýtgäp üýtgemänligini, goşulyp goşulmanlygyny ýa-da aýrylyp aýrylmanlygyny kesgitlemäge kömek edýär. Her bir elemente gaýtalanmaýan (unique) bir ID (pasport diýip pikir edäýiň) bermek üçin  array map-lenende olara key berlip gidilýär. Her bir elemente berilýän key şol array-de gaýtalanmal däldir, ýagny ýeketäk bolmalydyr. Köplenç maglumatlar bir id bilen gelýär we biz hem şol id-ny key hökmünde berip goýberýäris. Eger biz key bermesek onda React bize brauzerde duýduryş berer. Verinin bir kimliği yoksa, eşlerken her öğe için benzersiz bir tanımlayıcı oluşturmanın bir yolunu bulmamız gerekir. Eger array-iň içinde size gelýän maglumatyň id-sy ýok bolsa, onda key-e gaýtalanmaýan maglumat bermegiň bir ýoluny tapmaly bolarsyňyz. Aşakdaky meseleme serediň ( bu ýerde key hökmünde array-iň elementiniň özi berlip gidilendir ):

```js
import React from 'react'
import ReactDOM from 'react-dom'

const Numbers = ({ numbers }) => {
  // modifying array to array of li JSX
  const list = numbers.map((num) => <li key={num}>{num}</li>)
  return list
}

const App = () => {
  const numbers = [1, 2, 3, 4, 5]

  return (
    <div className='container'>
      <div>
        <h1>Numbers List</h1>
        <ul>
          <Numbers numbers={numbers} />
        </ul>
      </div>
    </div>
  )
}

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

Ýurtlary render eden meselemimizede key goşalyň.

```js
import React from 'react'
import ReactDOM from 'react-dom'

const countries = [
  { name: 'Finland', city: 'Helsinki' },
  { name: 'Sweden', city: 'Stockholm' },
  { name: 'Denmark', city: 'Copenhagen' },
  { name: 'Norway', city: 'Oslo' },
  { name: 'Iceland', city: 'Reykjavík' },
]

// Country component
const Country = ({ country: { name, city } }) => {
  return (
    <div>
      <h1>{name}</h1>
      <small>{city}</small>
    </div>
  )
}

// countries component
const Countries = ({ countries }) => {
  const countryList = countries.map((country) => (
    <Country key={country.name} country={country} />
  ))
  return <div>{countryList}</div>
}
const App = () => (
  <div className='container'>
    <div>
      <h1>Countries List</h1>
      <Countries countries={countries} />
    </div>
  </div>
)

const rootElement = document.getElementById('root')
ReactDOM.render(<App />, rootElement)
```

# Praktika

## Praktika: Dereje 1

1. Bize array-i map-lemek nämä gerek ?
2. Biz array-i map-länimizde näme üçin oňa key berýäris ?
3. Siz näme üçin prop-lary destructure edip alýaňyz ?
4. Destructure etmek koduňyzy arassa kod edýämi ýa-da kody okamagy ýeňilleşdirýämi ?

## Praktika: Dereje 2

1. Aşakdaky praktikany edeniňizde jübüt sanlara ýaşyl, täk sanlara sary we ýonekeý sanlara gyzyl reňk beriň. Bu praktikany React component-lerini ulanyp ediň.

![Number Generator](../images/day_6_number_generater_exercise.png)

2. React komponentalary ulanyp aşakdaky hex kod proýektini ediň.

![Number Generator](../images/day_6_hexadecimal_colors_exercise.png)

## Praktika: Dereje 3

1.Şu [data](../06_Day_Map_List_Keys/06_map_list_keys_boilerplate/src/data/ten_most_highest_populations.js) maglumatlary ulanyp aşakdaky kiçijik proýekti ediň.

![Ten most highest populations](../images/day_6_ten_highest_populations_exercise.png)

🎉 GUTLAÝARYS ! 🎉

[<< Gün 5](./../05_Day_Props/05_props.md) | [Gün 7 >>](../07_Day_Class_Components/07_class_components.md)

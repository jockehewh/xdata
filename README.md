# XDatajs
````
const xd = require('./xdata.js')

//first load the DB in memory

let xdata = xd.get()
let temp, usableData;
xdata.on('data', (data)=>{
    if(temp === undefined){
        temp = data
    }else{
        temp += data
    }
})
xdata.on('end', ()=>{
    usableData = JSON.parse(temp)
})
// use the data
console.log(usableData)
// add some data
var myobject = {name: "Xavier", city: "Paris", favoriteFood: 'burger'}
count = 0
usableData.forEach(element=>{
    if(Object.values(element)[0] === myobject.name){
        count++
        return
    }
})
if(count === 0){
    console.log('pushing object:', myobject)
    xd.set(myobject)
}else{
    console.log('error: an object with the same name already exist. please modify your element to make it unique before adding it to the memory')
    count = 0
    return
}

````

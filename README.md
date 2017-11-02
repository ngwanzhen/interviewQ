![alt text](imgs/1.png?raw=true 'start')
ans: B
![alt text](imgs/2.png?raw=true 'start')
ans: A
![alt text](imgs/3.png?raw=true 'start')
ans: D
![alt text](imgs/4.png?raw=true 'start')
ans: A
![alt text](imgs/5.png?raw=true 'start')
ans: A
![alt text](imgs/6.png?raw=true 'start')
ans: A
![alt text](imgs/7.png?raw=true 'start')
ans: A
![alt text](imgs/8.png?raw=true 'start')
ans: A
![alt text](imgs/9.png?raw=true 'start')
ans: A
![alt text](imgs/10.png?raw=true 'start')
ans: A
![alt text](imgs/11.png?raw=true 'start')
ans: B
![alt text](imgs/12.png?raw=true 'start')
ans: A
![alt text](imgs/13.png?raw=true 'start')
ans: D
![alt text](imgs/14.png?raw=true 'start')
ans: B
![alt text](imgs/15.png?raw=true 'start')
ans: C

![alt text](imgs/16.png?raw=true 'start')
<br />

ans: err ( but i'm not sure why err is first, is it because if code is synchronous, code may not reach error handling if callback is triggered first and code breaks at callback )

![alt text](imgs/17.png?raw=true 'start')

ans: break down using promises as promises are composable and hence can be triggered just using .then and .catch multiple times (Rather than re-wrting the callbacks again and again)

![alt text](imgs/18.png?raw=true 'start')

ans:
function test () {
  query("SELECT clientId FROM clients WHERE clientName='picanteverde';")
  .then((id) => {
    query('SELECT * FROM transactions WHERE clientId=' + id)
  })
  .then((transactions) => {
    transactions.each(function (transac) {
      query('UPDATE transactions SET value = ' + (transac.value * 0.1) + ' WHERE id=' + transac.id)
    })
    console.log('success!!')
  })
  .catch((err) => {
      console.log('error')
    })
}

![alt text](imgs/19.png?raw=true 'start')
ans: first, third, second

![alt text](imgs/20.png?raw=true 'start')

ans:
Promise.resolve(1)

.then((x)=>x+1) // 1 gets passed to then as x, so x+1 = 2, but nothing shown as no logging

.then((x)=>{ throw new Error('My Error')}) // throwing an error here and calling it my error

.catch((err)=>console.log(err)) // catching the error here logs the previous error provided to it 'My Error'

.then((x)=>x+1) // chaining then like that, I don't think the resolved value 1 gets passed on to the x like that, so nothing happens?

.then((x)=>console.log(x)) // nothing to log?

.catch(console.error) // no new errors have been provided here, so nothing to log again.

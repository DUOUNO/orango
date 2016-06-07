# orango
poc orm for ArangoDB


#### document

action\flag | saved | deleted
 ---------- | ----- | --- 
save        | 0 ->1 | == 0 
update      |       | == 0
replace     | == 1  | == 0
delete      |   -   | == 0, 0 -> 1


##### save
* deleted(1) -> no calls
* saved(0) -> api call to save -> set saved to 1
* saved(1) -> no api call may throw error

##### update
* deleted(1) -> no calls
* saved(0) -> no api call may throw error
* saved(1) -> api call to update

##### replace
* deleted(1) -> no calls
* saved(0) -> no api call may throw error
* saved(1) -> api call to replace

##### delete
* deleted(1) -> no calls
* saved(0) -> no api call, set deleted to 1
* saved(1) -> api call to delete -> set deleted to 1


```es6
const testCol = new testCollection();

let [doc, headers, status] = await testCol.document('1337');
await doc.update({updated:});
```

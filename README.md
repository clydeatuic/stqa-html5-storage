# stqa-html5-storage
> Activity 080417

## Code

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	Name:
	<input type="text" id="txtName" >
	<button onclick="addName()">Add to Local Storage</button>
	<table border="1">
		<thead>
			<tr>
				<th>Names</th>
				<th>Gender</th>
			</tr>
		</thead>
		<tbody id="tblNames">

		</tbody>
	</table>

	<script>
	
	function sample1(){
		let msg = "Hello World";
		console.log(msg);		
		localStorage.setItem('msg','Hello');
		sessionStorage.setItem('msg','World');

		let str1 = localStorage.getItem('msg');
		let str2 = sessionStorage.getItem('msg');
		let str3 = str1 + str2;
		console.log(str3);

		//localStorage.removeItem('msg');
		localStorage.clear();
		sessionStorage.clear();
	}

	function addName1(){
		let name = document.querySelector('#txtName').value;
		console.log(name);
		localStorage.setItem('name',name);
		sessionStorage.setItem('name',name);
	}

	let names = ['Clyde','Chester'];	
	function addName2(){
		let name = document.querySelector('#txtName').value;
		names.push(name);
		localStorage.setItem('names',names);
		let lsNames = localStorage.getItem('names');		
		let listOfNames = lsNames.split(',');
		console.log(listOfNames[0]);
	}

	let json_names = [{
		name: "Clyde",
		gender: "M"
	},{
		name: "Chester",
		gender: "F"
	}];
	function addName(){
		let name = document.querySelector('#txtName').value;
		let newName = {
			name: name,
			gender: "M"
		};
		json_names.push(newName);

		console.log(json_names);
		let jns = JSON.stringify(json_names);
		localStorage.setItem('json_names',jns);	

		let jns_retrieve = JSON.parse(localStorage.getItem('json_names'));
		console.log(jns_retrieve);

		console.log("Name is " + jns_retrieve[0].name);
		console.log("Gender is " + jns_retrieve[0].gender);

/*		let html = `
			<tr>
				<td>${jns_retrieve[0].name}</td>
				<td>${jns_retrieve[0].gender}</td>
			</tr>
			<tr>
				<td>${jns_retrieve[1].name}</td>
				<td>${jns_retrieve[1].gender}</td>
			</tr>
		`;*/

		let html = ``;

		jns_retrieve.map((name)=>{
/*			console.log(name.name);
			console.log(name.gender);
			console.log("---------");*/
			html += `
			<tr>
				<td>${name.name}</td>
				<td>${name.gender}</td>
			</tr>
			`;		
		});

		/*for(let i=0;i<jns_retrieve.length;i++){
			console.log(jns_retrieve[i].name);
			console.log(jns_retrieve[i].gender);
			console.log("************");
		}*/

		document.querySelector('#tblNames').innerHTML = html;
	}	

	</script>
</body>
</html>
```

## Assignment

Create a Login and Registration Pages that uses HTML5 Local or Session Storage.
* User Model

```javascript
user = {
	id: 1,
	name: "John",
	password: "1234"
}
```

* Registration Page Checklist

Function | Description
--- | ---
createUser() | This function should add a new user object
readUser() | This function should get all user in the storage
updateUser() | This function should modify a specific user object
deleteUser() | This function should remove a specific user in the storage

* Login Page Checklist

Function  | Description
--- | ---
isLogin() | This function returns true if the account is in the storage

* Due date : August 11

<table>

  <tr id="nameRows">
  </tr>

  <tr id="ageRows">
  </tr>

  <tr id="emailRows">
  </tr>
  <tr id="nationalityRows">
  </tr>

</table>


<script>

    function getPeople() {

        // Fetch data from API
        fetch('https://teamsports.nighthawkcoding.ml/api/person/')
        .then(response => response.json())
        .then(data => {
    
            peopleData = data;
            console.log(peopleData);
            
            // get row elements
            let nameRow = document.getElementById("nameRows");
            let ageRow = document.getElementById("ageRows");
            let emailRow = document.getElementById("emailRows");
            let nationalityRow = document.getElementById("nationalityRows");
            
            // clear table contents
            for (let j = 0; j < peopleData.length; j++){    

                nameRow.innerHTML = " ";
                ageRow.innerHTML = " ";
                emailRow.innerHTML = " ";
                nationalityRow.innerHTML = " ";

            }

            // add table contents
            for (let i = 0; i < peopleData.length; i++){  

                let header = document.createElement("th");
                header.setAttribute("id", i);
                header.innerHTML = peopleData[i].name;
                nameRow.appendChild(header);

                let newAgeRow = document.createElement("td");
                newAgeRow.setAttribute("id", i);
                newAgeRow.innerHTML = peopleData[i].age + " Years Old";
                ageRow.appendChild(newAgeRow);


                let newEmailRow = document.createElement("td");
                newEmailRow.setAttribute("id", i);
                newEmailRow.innerHTML = peopleData[i].email;
                emailRow.appendChild(newEmailRow);  

                let newNationalityRow = document.createElement("td");
                newNationalityRow.setAttribute("id", i);
                newNationalityRow.innerHTML = peopleData[i].nationality;
                nationalityRow.appendChild(newNationalityRow);  
            }

        });

}

function getInputId(){
    let input = document.getElementById("inputId").value;
    console.log(input);
    return input;
}

function getInputEmail(){
    let input = document.getElementById("inputEmail").value;
    console.log(input);
    return input;
}

function getInputPassword(){
    let input = document.getElementById("inputPassword").value;
    console.log(input);
    return input;
}

function getInputName(){
    let input = document.getElementById("inputName").value;
    console.log(input);
    return input;
}

function getInputDob(){
    let input = document.getElementById("inputDob").value;
    console.log(input);
    return input;
}

function getInputAge(){
    let input = document.getElementById("inputAge").value;
    console.log(input);
    return input;
}

function getInputNationality(){
    let input = document.getElementById("inputNationality").value;
    console.log(input);
    return input;
}


function addPeople(){
    
    const params = {
        email: getInputEmail(),
        password: getInputPassword(), 
        name: getInputName(),
        dob: getInputDob(),
        age: getInputAge(),
        nationality: getInputNationality(),

    };

    const options = {
        method: 'POST',
        body: JSON.stringify( params )  
    };

    fetch( 'https://teamsports.nighthawkcoding.ml/api/person/post/', options )
        .then(response => response.json())
        .then(data => {console.log(data);});

}

function getId(id) {
    idResult = document.getElementById("idResult");

    if(id < 35){
        idResult.innerHTML = "ID cannot be less than 35.";
    }
    // Fetch data from API
    fetch('https://teamsports.nighthawkcoding.ml/api/person/' + id)
    .then(response => response.json())
    .then(data => {
        console.log(data);
        idResult.innerHTML = "Person: " + data.name;
    })
}

</script>

<button onclick="getPeople()">Click To Update People Table</button>

<br>

### Get Person by ID

<p id="idResult"></p>

<input id="inputId" placeholder="Input Id">
    <button onclick="getId(getInputId())">Get Person by ID</button>

<br>

### Create New Person

<input id="inputEmail" placeholder="Input Email">


<input id="inputPassword" placeholder="Input Password">


<input id="inputName" placeholder="Input Name">


<input id="inputDob" placeholder="MM-dd-yyyy">


<input id="inputAge" placeholder="Input Age">


<input id="inputNationality" placeholder="Input Nationality">


<button onclick="addPeople()">Submit New Person</button>

    

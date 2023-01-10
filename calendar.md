<!--- This section is Cascading Style Sheet (CSS) and applies to HTML -->
<style>
/* "row style" is flexible size and aligns pictures in center */
.row {
  align-items: center;
  display: flex;
}

/* "column style" is one-third of the width with padding */
.column {
  flex: 33.33%;
  padding: 5px;
}
</style>

<p id="test"></p>
<script>
function numberOfLeapYears(year1, year2) {
    result = document.getElementById("numberOfLeapYearsResult");
    // Fetch data from API
    fetch('https://teamsports.nighthawkcoding.ml/api/calendar/numberOfLeapYears/' + year1 + "/" + year2)
    .then(response => response.json())
    .then(data => {
        console.log(data);
        result.innerHTML = "Leap Years between " + year1 + "and " + year2 + ": " + data.numberOfLeapYears;
    })
}
function getYear1(){
    let inputYear1 = document.getElementById("inputYear1").value;
    return inputYear1;
}
function getYear2(){
    let inputYear2 = document.getElementById("inputYear2").value;
    return inputYear2;
}

function getYear3(){
    let inputYear3 = document.getElementById("inputYear3").value;
    return inputYear3;
}

function getYear4(){
    let inputYear4 = document.getElementById("inputYear4").value;
    return inputYear4;
}

function getYear(){
    let inputYear = document.getElementById("inputYear").value;
    return inputYear;
}
function isLeapYear(yearparam) {
    result = document.getElementById("isLeapYearResult");
    // Fetch data from API
    fetch('https://teamsports.nighthawkcoding.ml/api/calendar/isLeapYear/' + yearparam)
    .then(response => response.json())
    .then(data => {
        console.log(data);
        result.innerHTML = "Is " + yearparam + " a leap year: " + data.isLeapYear;
    })
}
function firstDayOfYear(yearparam1) {
    result = document.getElementById("firstDayOfYearResult");
    // Fetch data from API
    fetch('https://teamsports.nighthawkcoding.ml/api/calendar/firstDayOfYear/' + yearparam1)
    .then(response => response.json())
    .then(data => {
        console.log(data);
        result.innerHTML = "First Day of " + yearparam1 + " is: " + data.firstDayOfYear;
    })
}
function dayOfYear(yearparam2) {
    result = document.getElementById("dayOfYearResult");
    // Fetch data from API
    fetch('https://teamsports.nighthawkcoding.ml/api/calendar/dayOfYear/' + yearparam2)
    .then(response => response.json())
    .then(data => {
        console.log(data);
        result.innerHTML = yearparam2 + " was " + "the: " + data.dayOfYear + " day of that year";
    })
}
</script>
Find Out if a Year is a Leap Year
<input id="inputYear" placeholder="Input a Year">
<button onclick="isLeapYear(getYear())">Submit</button>
<p id="isLeapYearResult"></p>

Check the Number of Leap Years in an Interval
<input id="inputYear1" placeholder="Input Starting Year">
    <input id="inputYear2" placeholder="Input Ending Year">
    <button onclick="numberOfLeapYears(getYear1(), getYear2())">Submit</button>
<p id="numberOfLeapYearsResult"></p>

First Day of a Certain Year
<input id="inputYear3" placeholder="Input a Year">
    <button onclick="firstDayOfYear(getYear3())">Submit</button>
<p id="firstDayOfYearResult"></p>

What Day of the Year it is (Enter a Date (MM/DD/YYYY):)
<input id="inputYear4" placeholder="Input a Year">
    <button onclick="dayOfYear(getYear4())">Submit</button>
<p id="dayOfYearResult"></p>

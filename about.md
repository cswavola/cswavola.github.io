---
layout: default
permalink: /test/
menu: main
---


<script>
function validateForm() {
  var x = document.forms["myForm"]["fname"].value;
  if (x == "") {
    alert("Name must be filled out");
    return false;
  }
}
</script>

<script>
function loadJSON (callback) {   

    var xobj = new XMLHttpRequest();
    xobj.overrideMimeType("application/json");
    xobj.open('GET', ({{site.baseurl}}/assets/test.json), true); // Replace 'my_data' with the path to your file
    xobj.onreadystatechange = function () {
        if (xobj.readyState == 4 && xobj.status == "200") {
            // Required use of an anonymous callback as .open will NOT return a value but simply returns undefined in asynchronous mode
            callback(xobj.responseText);
        }
    };
    xobj.send(null);  
}
</script>

### Demographics (pre populated)


<div class="form-inline">
  <label class="col-md-4 control-label" >Last Name</label>
    <div class="col-md-4 inputGroupContainer-inline">
    <div class="input-inline">
  <span class="input-group-addon"><i class="glyphicon glyphicon-user"></i></span>
  <input id="last_name" name="last_name" placeholder="Last Name" class="form-control"  type="text">
    </div>
  </div>
  <label class="col-md-4 control-label">First Name</label>  
  <div class="col-md-4 inputGroupContainer">
  <div class="input-inline">
  <input readonly id="first_name" name="first_name" placeholder="First Name" class="form-inline"  type="text">
    </div>
  </div>
<a href="#" onClick="fillFromJson(); return false;" >Populate</a>


<div class="form-inline">
  <label class="col-md-4 control-label">Gender</label>  
  <div class="col-md-4 inputGroupContainer">
    <div class="input-group">
     <span class="input-group-addon"><i class="glyphicon glyphicon-calendar"></i></span>
    <input readonly id="gender" name="gender" placeholder="Gender" class="form-control"  type="number">
    </div>
  </div>
</div>

<!-- Text input-->
      <div class="form-inline">
 <label class="col-md-4 control-label">Age</label>  
   <div class="col-md-4 inputGroupContainer">
   <div class="input-group">
   <input readonly id="age" name="age" placeholder="Age" class="form-control"  type="number">
   </div>
 </div>
</div>

<div class="form-inline">
<label class="col-md-4 control-label">PreOp</label>  
  <div class="col-md-4 inputGroupContainer">
    <div class="input-group">
    <textarea readonly rows="4" cols="50"  id="preop" name="preop" placeholder="PreOp Notes" class="form-control"  type="number"></textarea>
    </div>
  </div>
</div>


<script>
function showField() {
  var x = document.getElementById("PostOpForm");
  if (x.style.display === "none") {
    x.style.display = "block";
  } else {
    x.style.display = "none";
  }
}
</script>

<hr>
<br>
<button onclick="showField()">Enter PostOp Notes</button>

<form class="hidden" name="PostOpForm" id="PostOpForm" action="/action_page.php" method="post"  overflow-y: scroll type="hidden">
<textarea rows="4" cols="50" name = "PreOp" overflow-y: scroll >
"This is where the surgeon would write"
</textarea><br>
</form>


<button type="button" onclick="showTable()">Generate Codes</button>
<script>
function showTable() {
  var x = document.getElementById("resultsTable");
  if (x.style.display === "none") {
    x.style.display = "block";
  } else {
    x.style.display = "none";
  }
}
</script>
<script>
function addRow() {
  var x = document.getElementById("resultsTable");
  var newRow   = tableRef.insertRow(tableRef.rows.length);
}
</script>

<table style="width:100%" id="resultsTable" class="hidden">
  <tr>
    <th></th>
    <th>ICD9 No.</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><input type="checkbox" name="code1" value="Code1"></td>
    <td>10021</td>
    <td> Fine needle aspiration; without imaging guidance</td>
  </tr>
  <tr>
    <td><input type="checkbox" name="code1" value="Code1"></td>
    <td>10022</td>
    <td>Fine needle aspiration; with imaging guidance</td>
  </tr>
  <tr>
    <td><button type="button" onclick="addRow()">Check</button></td>
    <td><textarea rows="1" cols="10" name = "fname" ></textarea></td>
    <td>*to be populated*</td>
  </tr>
</table>



-----------------
<script>
var myObj, myJSON, text, obj;

// Storing data:
myObj = { name: fname, gender: fgender, height: "fheight" };
myJSON = JSON.stringify(myObj);
localStorage.setItem("testJSON", myJSON);

// Retrieving data:
text = localStorage.getItem("testJSON");
obj = JSON.parse(text);
document.getElementById("demo").innerHTML = obj.name;
</script>


<script>
function myFunction() {
 document.getElementById("demo").innerHTML = "Code Num XXXXX";
}
</script>
<br>

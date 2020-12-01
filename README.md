# dom-christ
<!DOCTYPE html>
<style>
    table,th,td
    {
     border:3px solid whitesmoke;
    }
    
    th,td{
        padding: 6px;
    }
    body {background-color: yellow;}
</style>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DOM</title>
</head>
<body>
    <h1>TECHOVID</h1>
    <button type="button" onclick="loadXML()">SHOW LIST</button>
    <br><br>
    <table id="demo"></table>
    <script>
        function loadXML()
        {
            var xhttp=new XMLHttpRequest();
            xhttp.onreadystatechange=function()
            {
                if(this.readyState==4&&this.status==200)
                {
                    myFunction(this);
                }
            };
            xhttp.open("GET","christ.xml",true);
            xhttp.send();
        }
        function myFunction(xml)
        {
            var i;
            var xmlDoc=xml.responseXML;
            var t="<tr><th>STUDENT NAME</th><th>STUDENT COLLEGE</th><th>STUDENT EMAIL</th><th>STUDENT BRANCH</th></tr>";
            var x=xmlDoc.getElementsByTagName("CHRIST");
            for(i=0;i<x.length;i++)
            {
                t +="<tr><td>" +
                x[i].getElementsByTagName("student name")[0].childNodes[0].nodeValue +
                "</td><td>" +
                x[i].getElementsByTagName("student college")[0].childNodes[0].nodeValue +
                "</td></tr>" +
                x[i].getElementsByTagName("student email")[0].childNodes[0].nodeValue +
                "</td></tr>" +
                x[i].getElementsByTagName("student branch")[0].childNodes[0].nodeValue +
                "</td></tr>";
            }
            document.getElementById("demo").innerHTML=t;
        }
    </script>
</body>
</html>

# First-Project
Project about my first program

                                                                                                  HTML CODE
<!DOCTYPE html>
<html>
<head>
    <meta name ="viewport" content ="width=device-width , intial-scale =1.0">
    <title>Weather App</title>
    <link rel ="stylesheet" href ="style.css">
</head>
<body>
<div class ="card">
    <div class = "search">
        <input type ="text" placeholder ="enter city name " 
        spellcheck = "false">
        <button><img src="search.png"></button>
    </div>
    <div class="error">
        <p>
            Invalid city name
        </p>
    </div>
    <div class="Weather">
    <img src="rain.png" class ="weather-icon">
    <h1 class="temp">22°c</h1>
    <h2 class="city"> NEW YORK</h2>
    <div class="details">
        <div class="col">
            <img src="humidity.png">
        </div>
        <p class="humdity">50%</p>
        <p>"Humidity"</p>
    <div class="col">
        <img src="wind.png">
    </div>
    <p class="Wind">15km/h</p>
    <p>Wind Speed</p>
</div>
</div>
</div>
</div>
<script>
const  apikey="d109579a74926443a9ae207b7833bca1";
const  apiurl="";
const searchBox= document.querySelector(".search input");
const searchbtn= document.querySelector(".search button ");
const weatherIcon = document.querySelector(".Weather-icon");
async function checkweather(city){
    const responce = await fetch(apiurl+city+`&appid=${ apikey}`);

    if(responce.status==404){
        document.querySelector(".error").style.display="block";
        document.querySelector(".weather").style.display="none";
    }else{
        var data = await responce .jeson();
    document.querySelector(".city").innerHTML = data.name;
    document.querySelector(".temp").innerHTML =  Math.round(data.main.temp)+"°C";
    document.querySelector(".humidity").innerHTML = data.main.humidity+"%";
    document.querySelector(".wind").innerHTML = data.wind.speed+"km/h";
    if(data.weather[0].main=="Clouds"){
        weatherIcon.src="clouds.png";
    }
    else if (data.weather[0].main=="clear"){
        weatherIcon.src="clear.png";
    }
    else if (data.weather[0].main=="rain"){
        weatherIcon.src="clear.png";
    }
    else if (data.weather[0].main=="Drizzle"){
        weatherIcon.src="Drizzle.png";
    }
    else if (data.weather[0].main=="mist"){
        weatherIcon.src="Mist.png";
    }
    document.querySelector("Weather").style.display="block";
    document.querySelector(".error").style.display="none";
    }
}
searchBtn.addEventListner("click",()=>{
    checkWeather(searchBox.value);
})
checkweather();
</script>
</body>
</html>

                                                                                                          CSS CODE

*{
    margin:0;
    padding:0;
    font-family :'Poppins ',sans-serif ;
    box-sizing: border-box;
}
body{
    background: #222;
}
.card{
    width: 90%;
    max-width : 470px;
    background: linear-gradient(135deg,#00feba,#5b548a);
    color:#fff;
    margin:100px auto 0;
    border-radius : 20px;
    padding:40px 35px;
    text-align: center;
}
.search{
    width : 100%;
    display : flex;
    align-items: center;
    justify-content :space-between;

}
.search input{
    border:0;
    outline:0;
    background:#ebfffc;
    color:#555;
    padding:10px 25px;
    height : 60px;
    border-radius:30px;
    flex:1;
    margin-right:30px;
    font-size:18px;
}
.search button{
    border:0;
    outline:0;
    background:#ebfffc;
    border-radius:50%;
    width:60px;
    height:60px;
    cursor:pointer;
}
.search button  img{
    width: 16px;
}
.weather-icon{
    width:170px;
    margin-top:30px;
}
.weather h1{
    font-size:80px;
    font-weight:500;
}
.weather h2{
    font-size:45px;
    font-weight: 400;
    margin-top:-10px ;
}
.details{
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 20px;
    margin-top: 50px;
}
.col{
    display: flex;
    align-items: center;
    text-align: left;
}
.col img{
    width: 40px;
    margin-right:10px;
}
.humidity,.wind{
    font-size:28px;
    margin-top:-6px;

}
.weather{
    display:none;
}
.error{
    text-align:left;
    margin-left: 10px;
    font-size: 14px;
    margin-top:10px;
    display:none;
}

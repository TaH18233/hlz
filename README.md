<!doctype html>
<html>
<head>
<meta charset="UTF-8">
<title>countdown</title>


</head>

<body>
<h1>Summer countdown</h1>
<div id="clockdiv">
    <div><span class="days"></span><div class="smalltext">Days</div></div>
    <div><span class="hours"></span><div class="smalltext">Hours</div></div>
    <div><span class="minutes"></span><div class="smalltext">Minutes</div></div>
    <div><span class="seconds"></span><div class="smalltext">Seconds</div></div>
</div>
<div id="gif">
    <img src="http://www.animaatjes.nl/plaatjes/h/hollands/animaatjes-hollands-17215.gif">
</div>

<style>
    body{
        text-align: center;
        background-image: url("images/molen.png");
        background-repeat: no-repeat;
        background-size: cover;
        font-family: sans-serif;
        font-weight: 100;
        margin: 0;
    }

    h1{
        color: #396;
        font-weight: 100;
        font-size: 40px;
        margin: 40px 0px 20px;
    }

    #gif{
        margin-top: 5%;
    }


    a{
        display: inline-block;
        color: #fff;
        font-size: 20px;
        padding: 20px;
        background: #265;
        border-radius: 10px;
        text-decoration: none;
    }

    a:hover{
        background: #487;
    }

    #clockdiv{
        font-family: sans-serif;
        color: #fff;
        display: inline-block;
        font-weight: 100;
        text-align: center;
        font-size: 30px;
    }


    #clockdiv > div{
        padding: 10px;
        border-radius: 3px;
        background: #00BF96;
        display: inline-block;
    }

    #clockdiv div > span{
        padding: 15px;
        border-radius: 3px;
        background: #00816A;
        display: inline-block;
    }

    .smalltext{
        padding-top: 5px;
        font-size: 16px;
    }
</style>

<script>
    var deadline = '2017-7-22';
    function time_remaining(endtime){
        var t = Date.parse(endtime) - Date.parse(new Date());
        var seconds = Math.floor( (t/1000) % 60 );
        var minutes = Math.floor( (t/1000/60) % 60 );
        var hours = Math.floor( (t/(1000*60*60)) % 24 );
        var days = Math.floor( t/(1000*60*60*24) );
        return {'total':t, 'days':days, 'hours':hours, 'minutes':minutes, 'seconds':seconds};
    }
    function run_clock(id,endtime){
        var clock = document.getElementById(id);

        // get spans where our clock numbers are held
        var days_span = clock.querySelector('.days');
        var hours_span = clock.querySelector('.hours');
        var minutes_span = clock.querySelector('.minutes');
        var seconds_span = clock.querySelector('.seconds');

        function update_clock(){
            var t = time_remaining(endtime);

            // update the numbers in each part of the clock
            days_span.innerHTML = t.days;
            hours_span.innerHTML = ('0' + t.hours).slice(-2);
            minutes_span.innerHTML = ('0' + t.minutes).slice(-2);
            seconds_span.innerHTML = ('0' + t.seconds).slice(-2);

            if(t.total<=0){ clearInterval(timeinterval); }
        }
        update_clock();
        var timeinterval = setInterval(update_clock,1000);
    }
    run_clock('clockdiv',deadline);
</script>

</body>
</html>

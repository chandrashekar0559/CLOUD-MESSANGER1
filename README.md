# CLOUD-MESSANGER1
This is a Node js Messanger app , we're going through deploy this in Cloud AWS with NGINX
model.testDetails1 ={testQuestion:model.testQuestion ,testAnswer: model.testAnswer , testOptionA:model.testOptionA , testOptionB:model.testOptionB,  testOptionC:model.testOptionC , testOptionD:model.testOptionD}




<!DOCTYPE html>
<html>
    <head>
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta.2/css/bootstrap.min.css">
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.6/umd/popper.min.js"></script>
        <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta.2/js/bootstrap.min.js"></script>
        <script src="http://ajax.googleapis.com/ajax/libs/angularjs/1.2.25/angular.min.js"></script>
        <script type="text/javascript">
                    angular.module('utms', [])
                    .controller('usrtsttakingContrl', ['$scope', function ($scope) {
                    var model = this;
                            model.acceptTest = function () {
                            model.testName = "Test1";
                                    console.log("Start Test");
                                    $('.close').click();
                                    $('#testForm').show();
                                    model.testTime = '1';
                                    var currentDate = new Date();
                                    var currentTime = currentDate.getMinutes() + " Mintues " + currentDate.getSeconds() + " Seconds";
                                    model.currentMinutes = currentDate.getMinutes();
                                    var minutes = parseInt(model.currentMinutes) + parseInt(model.testTime);
                                    model.targetTime = minutes + ":" + currentDate.getSeconds();
                                    console.log(currentTime);
                                    console.log("targetTime===" + model.targetTime);
                                    model.timmerMoving = '';
                                    var date = new Date();
                                    var sec = date.getSeconds();
                                    var min = date.getMinutes();
                                    var handler = function() {
                                    sec++;
                                            if (sec == 60) {
                                    sec = 0;
                                            min++;
                                            if (min == 60) min = 0;
                                    }
                                    model.timmerMoving = (min < 10 ? "0" + min : min) + ":" + (sec < 10 ? "0" + sec : sec);
//                                            console.log("timing---"+model.timmerMoving) ; 
                                            document.getElementById('timer').innerHTML = model.timmerMoving;
                                            if (model.timmerMoving == model.targetTime){
                                    alert("Time out")
                                            $("#submitTestResult").click();
                                    }
                                    };
                                    handler();
                                    setInterval(handler, 1000);
                                    $('#strtTest').hide();
                                    model.anSwr = '';
                                    model.anSwrTime = ' ';
                                    model.checkTime = function (obj){
                                    model.anSwr = obj.target.getAttribute("class");
                                            model.getID = obj.target.getAttribute("id");
                                            console.log(model.getID);
                                            model.anSwrTime = min + ":" + sec;
                                            if ($('.' + model.anSwr).is(':checked')) { console.log(model.anSwr + "it's checked");
                                            model.option = model.anSwr + "," + model.anSwrTime;
                                            $("#final" + model.getID).val(model.option);
                                    }
                                    }
                            model.testSubmit = function (){
                            model.testFinshTime = currentDate.getMinutes() + " (Min) " + currentDate.getSeconds() + " (Sec)";
                                    var marks = '0';
                                    var a = 'test1a', b = 'test2b'
                                    var aa = $("#finaltest1").val(); var bb = $("#finaltest2").val();
                                    console.log("val1-" + aa + "--val2--" + bb);
                                    if (a = aa){
                            marks++;
                                    console.log("marks" + marks);
                            } else  if (b = bb){
                            marks++;
                                    console.log("marks" + marks);
                            }
                            model.result = marks;
                                    console.log("Result--" + model.result + "--Test Name--" + model.testTime + "--Test Time--" + model.testTime + "--Finshed Time--" + model.testFinshTime + "--Num of correct Answers--" + model.result)
                            }
                            }

                    }]);</script>
        <style type="text/css">
            body {
                position: relative; 
            }
            .padding-left20{padding-left: 20px;}
            .padding-left50{padding-left: 50px;}
            .padding-left100{padding-left: 100px;}
            .margin-left25{margin-left: 25%;}
            .padding-top20{padding-top: 20px;}
        </style> 
    </head>
    <body data-spy="scroll" data-target=".navbar" data-offset="50" ng-clock ng-app="utms">
        <div  ng-controller="usrtsttakingContrl as uttsctl">
            <nav class="navbar navbar-expand-sm bg-dark navbar-dark fixed-top">  
                <ul class="navbar-nav">
                    <li class="nav-item" ng-click="uttsctl.createTest();">
                        <a class="nav-link btn btn btn-outline-success" >Create Test</a>
                    </li>
                    <li class="nav-item padding-left20"> 
                        <a class="nav-link btn btn btn-outline-info" href="#section2">View & Update Test</a>
                    </li>
                    <li class="nav-item padding-left20" >
                        <a class="nav-link btn btn-outline-danger" href="#section3">Delete Test</a>
                    </li>
                </ul>
            </nav>
            <div id="createSection" class="container-fluid bg-light" style="padding-top:100px;padding-bottom:100px;">
                <h1 class="text-center">Create Test</h1>
                <p class="">For Creating a test You must and should give all input values (EX:- you suppose to give Test Name and Test Time, 10 questions with respected options and Answer as well.)</p>
                <div class="text-center">  
                    <form id="testForm" style="display: none;"> <div>Time left = <div id="timer"> </div> &nbsp;&nbsp;&nbsp;  Target Time<div id="targetTime"></div> </div>
                        <div>
                            <label>1).</label><span>Questin1</span>
                            <div class="radio padding-top20 padding-left20 "><input type="text" id="finaltest1" value="" />
                                <label><input type="radio" name="test1" id="test1" class="test1a" ng-click="uttsctl.checkTime($event);"> <input id="test1a" type="text" value="oop11"  required /></label>

                                <label><input type="radio" name="test1" id="test1" class="test1b" ng-click="uttsctl.checkTime($event);"> <input id="test1b"  type="text" value="oop12"  required /> </label>

                                <label><input type="radio" name="test1" id="test1" class="test1c" ng-click="uttsctl.checkTime($event);"> <input id="test1c"  type="text" value="oop13"  required /> </label>

                                <label><input type="radio" name="test1" id="test1" class="test1d" ng-click="uttsctl.checkTime($event);"> <input id="test1d" type="text" value="oop14"  required /> </label>
                            </div>
                        </div>
                        <div>
                            <label>2).</label> <span>Questin2</span> 
                            <div class="radio padding-top20 padding-left20"><input type="text" id="finaltest2" value="" />
                                <label><input type="radio" name="test2" id="test2"  class="test2a" ng-click="uttsctl.checkTime($event);"><input id="test2a" type="text" value="oop21"  required /></label>

                                <label><input type="radio" name="test2" id="test2" class="test2b" ng-click="uttsctl.checkTime($event);"> <input id="test2b" type="text" value="oop22"  required /> </label>

                                <label><input type="radio" name="test2" id="test2" class="test2c" ng-click="uttsctl.checkTime($event);"> <input id="test2c"  type="text" value="oop23"  required /> </label>

                                <label><input type="radio" name="test2" id="test2" class="test2d" ng-click="uttsctl.checkTime($event);"> <input id="test2d" type="text" value="oop24"  required /> </label>
                            </div>
                        </div>  
                        <div class="clearfix"></div>
                        <div class="text-center padding-top20"><button type="submit" class="btn btn-primary" id="submitTestResult" data-toggle="modal" data-target="#submitTest" ng-click="uttsctl.testSubmit();">Submit</button></div>
                    </form>
                </div>
            </div>
            <div class="clearfix"></div>
            <div class="text-center"><button id='strtTest' class='btn btn-success' data-toggle="modal" data-target="#startTest">Start Test</button></div>
            <div id="startTest" class="modal fade" role="dialog">
                <div class="modal-dialog">
                    <!-- Modal content-->
                    <div class="modal-content">
                        <div class="modal-header">
                            <h4 class="modal-title"> Instructions For this Test</h4>
                            <button type="button" class="close" data-dismiss="modal">&times;</button>
                        </div>
                        <div class="modal-body">
                            <p>This Test has 10 questions.</p>
                            <p>You should complete the test as in time.</p>
                            <p>Once You click the Accept the button timer will start.</p>
                            <p>If you complete the test before the time and Submit the form.</p>
                            <p>If any case you are not completed the test as per in time limit , you are test submitted automatically. and marks counted for what you answered before the time.</p>
                            <div class="text-center">
                                <button class='btn btn-success' data-toggle="modal" ng-click="uttsctl.acceptTest();">Accept </button>     
                                <button class='btn btn-danger' data-toggle="modal" data-dismiss="modal">Reject</button>     
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="clearfix"></div>
            <div class="clearfix"></div>
            <div id="submitTest" class="modal fade" role="dialog">
                <div class="modal-dialog">
                    <!-- Modal content-->
                    <div class="modal-content">
                        <div class="modal-header">
                            <h4 class="modal-title text-center"> Result</h4>
                        </div>
                        <div class="modal-body">
                            <div class="">Test Name:  {{uttsctl.testName}}</div>
                            <div class="">Test Time:  {{uttsctl.testTime}} Mins..</div>
                            <div class="">Result: {{uttsctl.result}}</div>
                            <div class="">Finished Time: {{uttsctl.testFinshTime}}</div>
                            <div class="">Number Of Correct Answers: {{uttsctl.result}}</div>
                            <div class="">Congrats You are persentage marks to be added to you profile.</div>
                            <div class=""></div>
                            <div class="text-center padding-top20">
                                <button class='btn btn-success' data-toggle="modal" data-dismiss="modal">OKAY</button>     
                            </div>
                        </div>
                    </div>
                </div>
            </div>

        </div>
    </body>
</html>

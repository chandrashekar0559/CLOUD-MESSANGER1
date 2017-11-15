# CLOUD-MESSANGER1
This is a Node js Messanger app , we're going through deploy this in Cloud AWS with NGINX


<!DOCTYPE html>
<html>
    <head>
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta.2/css/bootstrap.min.css">
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.6/umd/popper.min.js"></script>
        <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta.2/js/bootstrap.min.js"></script>
        <script src="http://ajax.googleapis.com/ajax/libs/angularjs/1.2.25/angular.min.js"></script>
        <script src="adminEdit.js" type="text/javascript">
            angular.module('adminCon', [])
                    .controller('adminContrl', ['$scope', function ($scope) {
                            var model = this;
                            model.createTest = function () {
                                alert("Create Test");
                                $('#createSection').show();
                            };
                            model.readyToCreateTest = function () {
                                model.testName = $("#testName").val();
                                model.testTime = $("#testTime").val();
                                var testNameLength = ($("#testName").val()).length;
                                if (model.testName != '' && model.testTime != '' && model.testTime > 1 && model.testTime < 60 && testNameLength > 3 && testNameLength < 12) {
                                    console.log(model.testName + "---" + model.testTime + "---" + testNameLength);
                                    $('#createSection').hide();
                                    $('#editSection').show();
                                }
                            };
                            model.testQustionsSubmit = function (testName) {
                                console.log("comming:::testQustionsSubmit----" +testName);
                                model.testName = testName;
                                console.log("+=+=+="+model.testName);
                                for (i = 1; i <= 2; i++) {
                                    console.log("i--"+i);
                                    var getTestNames = model.testName+i;
                                    console.log($('#'+getTestNames).val());
                                    if($('form input[name='+ model.testName+i+']:checked')){
                                    var answ = $('form input[name='+ model.testName+i+']:checked').attr('class');
                                        model.testAnswer=$('#'+answ).val();
                                        console.log(model.testName+i+"--Answer checked value is--"+model.testAnswer);
                                    }
                                    for (j = 1; j <= 4; j++) {
                                         if(j=='1'){
                                        console.log($('#'+(model.testName)+i+'a').val());
                                         }else
                                         if(j=='2'){
                                        console.log($('#'+(model.testName)+i+'b').val());
                                         }else
                                         if(j=='3'){
                                        console.log($('#'+(model.testName)+i+'c').val());
                                         }else
                                         if(j=='4'){
                                        console.log($('#'+(model.testName)+i+'d').val());
                                         }
                                    }
                                }

                            };

                        }]);
        </script>
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
    <body data-spy="scroll" data-target=".navbar" data-offset="50" ng-clock ng-app="adminCon">
        <div  ng-controller="adminContrl as admnctl">
            <nav class="navbar navbar-expand-sm bg-dark navbar-dark fixed-top">  
                <ul class="navbar-nav">
                    <li class="nav-item" ng-click="admnctl.createTest();">
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
                    <form class="form-inline">
                        <div class="padding-left20">  <label for="testName">Test Name:</label></div>
                        <div class="padding-left20">  <input type="text" class="form-control" id="testName" required   max="10" min="4" maxlength="10" minlength='4' ></div>
                        <div class="padding-left20">  <label for="testTime">Test Time:</label></div>
                        <div class="padding-left20"> <input type="number" class="form-control" id="testTime" required   max="60" min="2" maxlength="60" minlength='2' ></div>
                        <div class="padding-left20"> <button type="submit" class="btn btn-primary" ng-click="admnctl.readyToCreateTest();">Submit</button></div>
                    </form>

                </div>
            </div>
            <div class="clearfix"></div>
            <div id="editSection" class="container-fluid bg-light" style="padding-top:100px;padding-bottom:100px;display: none;">
                <form id="{{admnctl.testName}}">
                    <div>
                        <label>1).</label><input   class="form-control" type="text" value="" placeholder="Please enter a Qustion Here" id="{{admnctl.testName}}1" required/>
                        <div class="radio padding-top20 padding-left20 ">
                            <label><input type="radio" name="{{admnctl.testName}}1" class="{{admnctl.testName}}1a"> <input id="{{admnctl.testName}}1a" type="text" value=""  required /></label>

                            <label><input type="radio" name="{{admnctl.testName}}1" class="{{admnctl.testName}}1b" > <input id="{{admnctl.testName}}1b"  type="text" value=""  required /> </label>

                            <label><input type="radio" name="{{admnctl.testName}}1" class="{{admnctl.testName}}1c" > <input id="{{admnctl.testName}}1c"  type="text" value=""  required /> </label>

                            <label><input type="radio" name="{{admnctl.testName}}1" class="{{admnctl.testName}}1d" > <input id="{{admnctl.testName}}1d" type="text" value=""  required /> </label>
                        </div>
                    </div>
                    <div>
                        <label>2).</label><input   class="form-control" type="text" value="" placeholder="Please enter a Qustion Here" id="{{admnctl.testName}}2" required/>
                        <div class="radio padding-top20 padding-left20">
                            <label><input type="radio" name="{{admnctl.testName}}2" class="{{admnctl.testName}}2a"><input id="{{admnctl.testName}}2a" type="text" value=""  required /></label>

                            <label><input type="radio" name="{{admnctl.testName}}2" class="{{admnctl.testName}}2b"> <input id="{{admnctl.testName}}2b" type="text" value=""  required /> </label>

                            <label><input type="radio" name="{{admnctl.testName}}2" class="{{admnctl.testName}}2c"> <input id="{{admnctl.testName}}2c"  type="text" value=""  required /> </label>

                            <label><input type="radio" name="{{admnctl.testName}}2" class="{{admnctl.testName}}2d"> <input id="{{admnctl.testName}}2d" type="text" value=""  required /> </label>
                        </div>
                    </div>
                    <div class="text-center padding-top20"><button type="submit" class="btn btn-primary" ng-click="admnctl.testQustionsSubmit(admnctl.testName);">Submit</button></div>
                </form>
            </div>
            <div class="">
                <div class="container">
                    <div class="row">
<!--                        <div class="col-md-6">
                            <div class="card ">
                                <div class="card-header">
                                    <h3>Bar Series</h3>
                                </div>
                                <div class="card-block">
                                    <div id="chart1"></div>
                                </div>
                            </div>
                        </div>-->
                        <div class="col-md-6">
                            <div class="card ">
                                <div class="card-header">
                                    <h3>Multiple Bar Series</h3>
                                </div>
                                <div id="chart2" class="card-block">
                                </div>
                            </div>
                        </div>
                    </div>   
                </div>

                <!-- you need to include the shieldui css and js assets in order for the charts to work -->
                <link rel="stylesheet" type="text/css" href="http://www.shieldui.com/shared/components/latest/css/light/all.min.css" />
                <script type="text/javascript" src="http://www.shieldui.com/shared/components/latest/js/shieldui-all.min.js"></script>

                <script type="text/javascript">
                                        jQuery(function ($) {
                                        var data1 = [12, 3, 4, 2, 12, 3, 4, 17, 22, 34, 54, 67];
                                                var data2 = [3, 9, 12, 14, 22, 32, 45, 12, 67, 45, 55, 7];
                                                var data3 = [23, 19, 11, 134, 242, 352, 435, 22, 637, 445, 555, 57];
//                                                $("#chart1").shieldChart({
//                                        exportOptions: {
//                                        image: false,
//                                                print: false
//                                        },
//                                                axisY: {
//                                                title: {
//                                                text: "Break-Down for selected quarter"
//                                                }
//                                                },
//                                                dataSeries: [{
//                                                seriesType: "bar",
//                                                        data: data1
//                                                }]
//                                        });
                                                $("#chart2").shieldChart({
                                        exportOptions: {
                                        image: false,
                                                print: false
                                        },
                                                axisY: {
                                                title: {
                                                text: "Break-Down for selected quarter"
                                                }
                                                },
                                                dataSeries: [{
                                                seriesType: "bar",
                                                        data: data2
                                                }, {
                                                seriesType: "bar",
                                                        data: data3
                                                }]
                                        });
                                        });                </script>
            </div>

            <div class="clearfix"></div>
        </div>
    </body>
</html>

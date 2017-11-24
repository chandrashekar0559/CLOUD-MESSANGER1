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
        <script  type="text/javascript">
                    angular.module('adminCon', [])
                    .controller('adminContrl', ['$scope', function ($scope) {
                    var model = this;
                            var chart = AmCharts.makeChart("chartdiv", {
                                    "theme": "light",
                                            "type": "serial",
                                            "dataProvider": [{
                                            "Tests": "No Of Tests",
                                                    "testsTaken": 3,
                                                    "totalNoOfTests": 10,
                                            }, {
                                            "Tests": "Average Score",
                                                    "YourMarks": 1.7,
                                                    "TotalAvgMarks": 20.1
                                            }, {
                                            "Tests": "Persentage Growth",
                                                    "year2004": 2.8,
                                                    "year2005": 2.9
                                            }],
                                            "startDuration": 1,
                                            "graphs": [{
                                            "balloonText": "Taken Tests [[category]]: <b>[[value]]</b>",
                                                    "fillAlphas": 0.9,
                                                    "lineAlpha": 0.2,
                                                    "title": "tests",
                                                    "type": "column",
                                                    "valueField": "testsTaken"
                                            }, {
                                            "balloonText": "No Of Conducted [[category]] : <b>[[value]]</b>",
                                                    "fillAlphas": 0.9,
                                                    "lineAlpha": 0.2,
                                                    "title": "tests",
                                                    "type": "column",
                                                    "valueField": "totalNoOfTests"
                                            },{
                                            "balloonText": "Your Marks [[category]]: <b>[[value]]</b>",
                                                    "fillAlphas": 0.9,
                                                    "lineAlpha": 0.2,
                                                    "title": "marks",
                                                    "type": "column",
                                                    "valueField": "YourMarks"
                                            }, {
                                            "balloonText": "Total Avg Marks [[category]] : <b>[[value]]</b>",
                                                    "fillAlphas": 0.9,
                                                    "lineAlpha": 0.2,
                                                    "title": "marks",
                                                    "type": "column",
                                                    "valueField": "TotalAvgMarks"
                                            }],
                                            "plotAreaFillAlphas": 0.6,
                                            "depth3D": 30,
                                            "angle": 50,
                                            "categoryField": "Tests",
                                            "categoryAxis": {
                                            "gridPosition": "start"
                                            },
                                            "export": {
                                            "enabled": true
                                            }
                                    });
                                    jQuery('.chart-input').off().on('input change', function() {
                            var property = jQuery(this).data('property');
                                    var target = chart;
                                    chart.startDuration = 0;
                                    if (property == 'topRadius') {
                            target = chart.graphs[0];
                                    if (this.value == 0) {
                            this.value = undefined;
                            }
                            }
                            target[property] = this.value;
                                    chart.validateNow();
                                    });
                    }]);        </script>
        <script src="https://www.amcharts.com/lib/3/amcharts.js"></script>
        <script src="https://www.amcharts.com/lib/3/serial.js"></script>
        <style type="text/css">
            body {
                position: relative; 
            }
            .padding-left20{padding-left: 20px;}
            .padding-left50{padding-left: 50px;}
            .padding-left100{padding-left: 100px;}
            .margin-left25{margin-left: 25%;}
            .padding-top20{padding-top: 20px;}
            #chartdiv {
  width: 100%;
  height: 500px;
}		.amcharts-chart-div a{display:  none !important;}
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
            <div class="">
                <div class="container">
                    <div class="row" style="padding-top: 100px">
                       <div id="chartdiv"></div>
                    </div>   
                </div>
            </div>
            <div class="clearfix"></div>
        </div>
    </body>
</html>

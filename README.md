<!DOCTYPE html>
<html>
<head>
 <title>To-Do List Application</title>
 <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.8.2/angular.min.js">
</script>
</head>
<body ng-app="myApp">
<div ng-controller="myController">
 <h2>To-Do List</h2>
 <ul>
 <li ng-repeat="task in tasks">
 {{ task.name }}
 <button ng-click="editTask(task)">Edit Task</button>
 <button ng-click="deleteTask(task)">DeleteTask</button>
 </li>
 </ul>
 <div>
 <label>New Task: </label>
 <input type="text" ng-model="newTaskName">
 <button ng-click="addTask()">Add Task</button>
 </div>
 <div ng-show="editingTask">
 <label>Edit Task: </label>
 <input type="text" ng-model="editedTaskName">
 <button ng-click="saveTask()">Save</button>
 <button ng-click="cancelEdit()">Cancel</button>
</div>
</div>
<script src="Program6.js"> </script> 
</body>
</html>
Program6.js
var app = angular.module('myApp', []);
app.controller('myController', function ($scope) {
 
// Default tasks
 $scope.tasks = [
 { name: 'Attend Class'},
 { name: 'Complete Assignment'},
 { name: 'Study for CIE'}
 ];
 $scope.newTaskName = ' ';
 $scope.editingTask = null;
 $scope.editedTaskName = ' ';
 $scope.addTask = function () {
 if ($scope.newTaskName) {
 $scope.tasks.push({ name: $scope.newTaskName });
 $scope.newTaskName = ' ';
 }
 };
 $scope.editTask = function (task) {
 $scope.editingTask = task;
 $scope.editedTaskName = task.name;
 };
 $scope.saveTask = function () {
 if ($scope.editingTask) {
 $scope.editingTask.name = $scope.editedTaskName;
 $scope.cancelEdit();
 }
 };
 $scope.cancelEdit = function () {
 $scope.editingTask = null;
 $scope.editedTaskName = '';
};
 $scope.deleteTask = function (task) {
 var index = $scope.tasks.indexOf(task);
 if (index !== -1) {
 $scope.tasks.splice(index, 1);
 }
 };
 });

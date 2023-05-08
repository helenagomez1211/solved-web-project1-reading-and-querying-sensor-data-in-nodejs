Download Link: https://assignmentchef.com/product/solved-web-project1-reading-and-querying-sensor-data-in-nodejs
<br>
The aims of this project are as follows:

<ul>

 <li>To ensure that you have set up your VM as speci ed in the Course VM and Github Setup</li>

 <li>To get you to write a simple but non-trivial JavaScript program.</li>

 <li>To allow you to familiarize yourself with the programming environment you will be using in this course.</li>

 <li>To make you design an in-memory indexing scheme.</li>

</ul>

<h1>1.2        Background</h1>

This project involves reading and querying sensor data. The data is organized in three levels:

<ol>

 <li>Sensor Types: A sensor type de nes the information for a model of a sensor. The information includes the manufacturer, modelNumber, the kind of quantity measured, the unit of measurement and the max and min limits of the measurement. Note that any reading outside these limits will necessarily be in error.</li>

</ol>

Each sensor type is assigned a unique id.

<ol start="2">

 <li>Sensors: These are the actual sensors. Each sensor has a speci ed sensor type. The information includes the model (the id of the corresponding sensor type), the period in seconds after which the sensor makes the next reading, and a max and min range of expected values. Note that any reading outside this expected range will constitute an outOfRange condition.</li>

</ol>

Note that the expected range of a sensor will be a sub-interval of the limits of the corresponding sensor type.

Each sensor is assigned a unique id.

<ol start="3">

 <li>Sensor Data A stream of the data readings from the sensors. Each reading consists of a timestamp’d value produced by a sensor identi ed by its sensorId.</li>

</ol>

Note that each reading can be classi ed as being in one of three states: error The value of the reading is outside the limits of the sensor model.

outOfRange The value of the reading is outside the range expected for the measuring sensor.

ok          The value of the reading is within the range of expected values.

It is guaranteed that the time between two readings from the same sensor will be an exact multiple of the sensor’s period.

The data model should become absolutely clear after looking at the provided data les.

<h1>1.3        Requirements</h1>

You must push a submit/prj1-sol directory to your github repository such that typing npm ci within that directory is su cient to run the project using ./index.js.

You are being provided with an index.js which provides the required commandline behavior. What you speci cally need to do is add code to the provided sensors.js source le as per the requirements in that le.

Additionally, your submit/prj1-sol must contain a vm.png image le to verify that you have set up your VM correctly. Speci cally, the image must show a x2go client window running on your VM. The captured x2go window must show a terminal window containing the output of the following commands:

$ hostname; hostname -I

$ ls ~/git-repos

$ ls ~/cs544

$ ls ~/i?44

$ crontab -l | tail -3

The behavior of the program is illustrated in this annotated log.

<h1>1.4        Provided Files</h1>

The prj1-sol directory contains a start for your project. It contains the following les:

sensors.js This skeleton le constitutes the guts of your project. You will need to esh out the skeleton, adding code as per the documentation. You should feel free to add any auxiliary function or method de nitions as required.

index.js This le provides the complete command-line behavior which is required by your program. It requires sensors.js. You must not modify this le; this ensures that your Sensors class meets its speci cations and facilitates automated testing by testing only the Sensors API.

README A README le which must be submitted along with your project. It contains an initial header which you must complete (replace the dummy entries with your name, B-number and email address at which you would like to receive project-related email). After the header you may include any content which you would like read during the grading of your project.

Additionally, the course data directory contains sensor data             les.

<h1>1.5       Hints</h1>

You should feel free to use any of the functions from the standard <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript">library;</a> in particular, functions provided by the <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array">Array,</a> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/">String,</a> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number">Number</a> and <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math">Math</a> objects useful. You should not need to use any nodejs library functions (except possibly for <a href="https://nodejs.org/dist/latest-v10.x/docs/api/assert.html#assert_assert_value_message">assert())</a> or additional npm packages.

The following steps are not prescriptive in that you may choose to ignore them as long as you meet all project requirements.

<ol>

 <li>Set up your course VM as per the instructions speci ed in the Course VM and Github</li>

 <li>Read the project requirements thoroughly. Look at the sample log to make sure you understand the necessary behavior.</li>

 <li>Look into debugging methods for your project. Possibilities include:

  <ul>

   <li>Logging debugging information onto the terminal using <a href="https://developer.mozilla.org/en-US/docs/Web/API/Console/log">log() </a>or <a href="https://developer.mozilla.org/en-US/docs/Web/API/Console/error">console.error().</a></li>

   <li>Use the chrome debugger as outlined in this</li>

  </ul></li>

 <li>Consider what kind of indexing structure you will need to track the sensor information. For each sensor, you will need to be able to access its sensor type and readings easily. Since each sensor is an instance of its sensor type, you can consider using inheritance to model that relationship.</li>

</ol>

When designing your indexing structure, you should rst think in terms of abstract <a href="https://en.wikipedia.org/wiki/Associative_array">associative arrays</a> and then consider possibilities for implementing these abstract associative arrays in JavaScript. Possibilities:

<ul>

 <li>Use standard JavaScript objects as associative arrays. Advantages include the ability to using simple []-based access and trivial JSON conversion for subsequent projects. Disadvantages include the lack of any de ned order for property keys and the overhead of all the machinery associated with Object’s like inheritance.</li>

 <li>Use the relatively new <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map">Map</a> addition to the standard library. An advantage of this approach is that it preserves insertion order. It may also be lighter than the Object alternative suggested above. Disadvantages include a clumsy API (get() and set()) and nontrivial work required for JSON conversion which may be useful for subsequent projects.</li>

</ul>

<ol start="5">

 <li>Start your project by creating a work/prj1-sol directory in the i444 or i544 directory corresponding to your github repository. Change into the newly created prj1-sol directory and initialize your project by running npm init -y. This will create a package.json le; this le should be committed to your repository.</li>

</ol>

Run npm install. This should create a package-lock.json. Be sure to commit this lock le to your github repository too.

<ol start="6">

 <li>Capture an image to validate that you have set up your course VM as instructed. Within a terminal window in your x2go client window, type in the following commands:</li>

</ol>

$ hostname; hostname -I

$ ls ~/git-repos

$ ls ~/cs544

$ ls ~/i?44

$ crontab -l | tail -3

Use an image capture program on your workstation to capture an image of your x2go client window into the le vm.png in your work/prj1-sol directory. The captured image should clearly shows the terminal window containing the output of the above commands.

<ol start="7">

 <li>Copy the provided les into your project directory:</li>

</ol>

$ cp -p $HOME/cs544/projects/prj1/prj1-sol/* .

This should copy the README template, the index.js and the sensors.js skeleton le into your project directory.

<ol start="8">

 <li>You should be able to run the project, but all commands will return without any results until you replace the @TODO sections with suitable code.</li>

</ol>

$ ./index.js #show usage message

$ DATA=$HOME/cs544/data/sensors

$ ./index.js $DATA

add              sensor-type|sensor|sensor-data NAME=VALUE…

clear clear all sensor data … load sensor-type|sensor|sensor-data JSON_FILE

&gt;&gt; find sensor-data sensorId=22

&gt;&gt;

<ol start="9">

 <li>Replace the XXX entries in the README template.</li>

 <li>Commit your project to github:</li>

</ol>

$ git add .

$ git commit -a -m ’started prj1’

<ol start="11">

 <li>Open the copy of the sensors.js le in your project directory. It contains (a) A strict declaration.

  <ul>

   <li>A skeleton Sensors class de nition with @TODO comments. The comments and FN_INFOS table at the end of the le specify the behavior of the methods you need to complete.</li>

  </ul></li>

</ol>

Note that the class syntax is a recent addition to JavaScript and is syntactic sugar around JavaScript’s more exible object model. Note that even though the use of this class syntax may make students with a background in class-based OOPL’s feel more comfortable, there are some di erences worth pointing out:

<ul>

 <li>No data members can be de ned within the class body. All “instance variables” must be referenced through the this pseudovariable in both constructor and methods. For example, if we want to initialize an instance variable sensorTypes in the constructor() we may have a statement like:</li>

</ul>

this.sensorTypes = {};

<ul>

 <li>There is no implicit this. If an instance method needs to call another instance method of the same object, the method must be called through this.</li>

 <li>There is no easy way to get private methods or data. Instead a convention which is often used is to pre x private names with something like a underscore and trust class clients to not misuse those names.</li>

</ul>

<ul>

 <li>An assignment of the Sensors class to module.exports. This makes Sensors the only declarations available outside the sensors¬ .js le; all other declarations are local to the le.</li>

 <li>Validation code. This code checks for required values, converts strings to numbers as necessary and inserts default values. The validation is driven by the FN_INFOS table towards the end of the le. Note that though this generic validation takes care of most of your validation needs, you will still need some additional validation.</li>

</ul>

Some points worth making about the provided code:

<ul>

 <li>All the methods have been declared async. This is not needed for this project, but will be necessary for subsequent projects. You can safely ignore the async declarations and write code normally.</li>

 <li>For error handling, the convention used is that all user errors should be thrown as lists of objects (for example, see the throw at the end of the validate() function). If you need to throw your own errors, be sure to wrap them in a list. Do so even for a single error:</li>

</ul>

if (!sensorTypes[model]) {

throw [ ‘no model ${model} sensor type‘ ];

}

This allows the calling code to distinguish between exceptions caused by intentional error reporting and those caused inadvertently, allowing the former to be reported as simple error messages whereas the latter will be reported with a full stack trace. This makes it much easier to debug your code when you get unintentional exceptions.

<ul>

 <li>The code should assume that the property values in the incoming info object which is the argument to the methods in Sensors can be String’s, even when the corresponding property is expected to be a number or integer. For example, a sensor reading may come in as:</li>

</ul>

{ … value: “123”, …

}

This assumption makes it easy to interface with dumb form interfaces (or a dumb cli program for this project).

Note that it is also permissible for incoming property values to be numbers as in:

{ … value: 123, …

}

Both of these possibilities are handled correctly by the provided validation code. In both cases, the validation code return value will contain the property as a Number.

<ul>

 <li>In contrast to the previous point, any number-valued properties in the return values of the Sensors methods should be JavaScript Number’s.</li>

</ul>

<ol start="12">

 <li>Add initialization code to your constructor(). It is possible that you will need to execute the same code in your clear() method; in that case, you can simply have your constructor call your clear() method (using this.clear()).</li>

 <li>Add any utility functions or methods which may be useful. One possiblity would be an inRange(value, range) method which returns truthy i range.min &lt;= value &lt;= range.max. This can be useful in classifying the status of a sensor reading.</li>

 <li>The add*() methods should be relatively trivial (YMMV depending on the details of your indexing structure). Implement the addSensorType() method. Test using the provided $DATA/sensor-types.json le. Using a debugger or console.log() verify that you have indeed captured the data. Check for error handling using $DATA/err-sensor-types.json.</li>

 <li>Implement the addSensor() method. You will need to validate that the sensor model is a valid sensor type id.</li>

 <li>Implement the addSensorData() method. You will need to validate that the id speci ed by the incoming sensorId is a valid sensor id.</li>

 <li>Start implementing the findSensorType() method. There are two cases to consider:

  <ul>

   <li>There is a truthy incoming id property. In this case, you should simply return the single matching sensor type or report some kind of not found error.</li>

   <li>There is no truthy incoming id property. After the default processing of the validate() function, its return value is guaranteed to have index and count properties. Ignoring possible lter parameters, simply extract sensor types for the speci ed index and count. Test.</li>

  </ul></li>

</ol>

Now add support for lter parameters. Test using lters like manufacturer or quantity.

<ol start="18">

 <li>Implement findSensor() along the lines of findSensorType(). There should be a lot of common functionality between the two; refactor your code so as to share the common functionality.</li>

 <li>Implement findSensorData(). This may be the hardest part of this project, but you should have already thought this through when you designed your indexing structure.</li>

 <li>Iterate until you meet all requirements.</li>

</ol>
Name: David Tu
Email: david.tu2@csu.fullerton.edu
Class: CPSC 486-02
Assignment: Final Project
Desciption: Program which renders a city
Controls:	
			UP ARROW: Forward
			DOWN ARROW: Backwards
			LEFT ARROW: Pan Left
			RIGHT ARROW: Pan Right
			W KEY: Ascend
			S KEY: Descend
			A KEY: Strafe Left
			D KEY: Strafe Right
			ESC KEY: End Game

The first thing the appilcation will do under the main() is create an instance of CityApp. Since CityApp inherits from GLFWApp, the next thing it does is run the first function from the sequence: begin(), render(), and end(). begin() will continue with the initialization proess of the program by calling initCamera(), initLights(), initShaders(), and initWorld(); following the commands: glClearColor() to set the background color, glEnable(GL_DEPTH_TEST) to inform the program that the it is a 3D program, and glDepthFunc(GL_LESS) to enable objects to be rendered in front of other objects.

When initCamera() was called, an instance of a camera is created, passing the initial position of the camera as a parameter. The next function that was called was initLights(). In initLights(), an instane of SpinningLight was created, passing the color, the position, and center position of the light. The center position is used to create a gaze vector within the SpinningLight's contructor. In the function, initShaders(), it actually uses two sets of shaders. The resulting Shader Program A is used for blinn phong lighting and texturing while Shader Program B is responsible for the skybox. In addition to loading the shaders, the fuction also sets up the uniform variables for those shader programs. Finally, in initWorld(), it simply creates a new instance of world that the user can fly in.

After begin() completes, the next function will be render(). Since, CityApp is also a GLFWApp, this function will run continuously until there is user input to end the program (thereby calling end()). This implies that the end of render() checks for user input. In addition to checking whether to end the program, it also checks for camera movement. By doing this every frame, a flying simulation can be achieved. Prior to checking for user input, render() also continuously calls glClear() (To clear the screen for a new drawing), activates uniforms and then draws. This is repeated for each shader program for the drawing of the city and the skybox. Prior to activating the uniforms, the uniform variables need to be updated first. They are the projection matrix, the model-view matrix, and the normal matrix. These need to be updated because of the camera movement - Based on the new position the camera will be, a recalculation of lights and textures are required.

Defects List (Things to consider for continuing this project):
1. Minor: Confirm that rotate up and down functions work as expected
2. Minor: rand() doesn't seem sufficient enough to truly randomize
3. Minor: Light is currently a driectional light. For the future, implement a point light
4. Minor: Cosmetically, textures could look better
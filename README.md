# Riot-Gmail

#### Take some time to think through the code.

- What’s new here? What do you understand is happening functionally?
    - Now the interface is more functional, and when you click on the button it actually activates an event. For example, when you click on the COMPOSE button, it opens the editor window, and when hit SEND, the data inputed is printed on the page. 
The interesting thing here is that even when the tags are independent, a function stated in one tag can be referenced and called from another tag, as long as they have a parent-child relationship.

- How is component based thinking working?
    - In this case it is clear how components are hierarchically organized and how they are related. Therefore, even when we can think of components as independent elements, they can be interrelated: some tags can contain other tags; functions called in a child tag (e.g. `parent.closeEditor`) can be defined in the parent tag; data inputted in a child tag can be printed in a sibling tag (e.g. `mail-item tag`). 

- How is Compose represented in a data state?
    - COMPOSE is presented in a false state, which means that the `mail-editor` tag will not appear until the user hits the COMPOSE button. This activates a function that toggles change the state from false to true. 

- How might you build out the functionality or change in state?
    - Just by changing the variable state and setting it to true. In tis case we have the conditional that says that `if={editor}` is true then the tag should show. But because the editor variable was initialized as false, it is not until the user hits the COMPOSE button,that the toggle function changes the value to true, therefore, making the `mail-editor` tag visile to the user.

- What is the state of the button initially? Why do you think that is?
    - The state of the button is true. It has to be true so the user knows what to do. In terms of user experience, the button indicates that when hit, something is going to change in the DOM. The button indicates interactivity to the user. Therefore is a cue that is needed. In its absence (if it was in a false state), the user wouldn't know what to do.

- Why are we using the parent property here?
    - Through the parent property we are calling the function defined in the parent tag. If we don't include the parent property, nothing happens. 

- Why is the closeEditor function in a different tag file?
    - Because it is changing the state of the `mail-editor` tag bak to false, and is using one of the variables defined in the parent tag. 

- Where is the function called from? How are we wiring different components together?
    - It is call from the button in the child tag. 

- How are we sending data from the smaller component (editor) to the larger mail app?
    - The larger mail tag contains the other 2 tags: mail-editor and mail-list. Because we are pushing the data inputed by the user to the array of objects `emailList`, this array is being updated with the user's input. Likewise, the `mail-list` was defined with a `each` RIOT loop that prints every object in the array, included those inputed by the user.

- How is riot’s way of getting specific references to elements different from regular JS?
    - `This` is the main form used. By referencing `this`, we are pointing to the current tag when console.logged globally or to a specific function, for example, when console.logged inside the particular function.

- How is the mail app component updating when the email is sent? Talk about it in terms of changes in state.
    - When the email is sent, there is a function called that is in charge of pushing that data into the array of object defined in the parent tag. And the closeEditor function is also called from inside that same function. Like it was stated before, the close function changes the state of the `mail-editor` tag from true to false, so the editor hides again. 

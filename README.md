# Next.js_with_Tailwind_Guide
This guide features the use of tailwind features for quick referencing during web development using next.js 13.1
# Creating vertical columns
1fr  - takes the leftover space 
auto - takes space required by the the comonents enclosed
```
 <div className="container min-h-screen grid grid-cols-[auto,1fr]">
 <div></div>
 <div></div>
 </div>
 ``` 
 
# Creating rows
1fr  - takes the leftover space 
auto - takes space required by the the comonents enclosed
```
 <div className="container min-h-screen grid grid-rows-[auto,1fr]">
 <div></div>
 <div></div>
 </div>
 ``` 
 
# Creating overflow components to stay on screen
        <div className="container min-h-screen grid grid-rows-[1fr,1fr,1fr,1fr,auto]">  
          // these divs are tobe repeated equal tp the number of screens your website has
          <div className=" h-screen ">
          </div>
          <div className=" h-screen ">
          </div>
          <div className=" h-screen ">
          </div>
        
          <div className=" h-screen  sticky bottom-0 px-1"> // change this property depending on where to stick your component relative to screen
          <div className="container min-h-screen grid grid-rows-[1fr,auto]">
          <div >
          </div>  
          <div >
          // main components here
          </div>
          </div>
          </div>
            
        </div> 

# Using next/Image component that adjusts itself on load to accupy available space

Use with caution Its only for case where you want to inherit parent width
```
    <Image
    src="/mainpic.svg" 
    alt="ico" 
    width={400} 
    height={30}   
    style={{
        maxWidth: '100%',
        height: 'auto',
    }}
    </Image>
```

# Hiding showing a section

## Create a control variable
Dont forget to add use client at top since this will usestate from react
```
'use client'
```
Then import useState (used for components that wil be changing there states)
```
import { useState } from "react"
```
In your function declare the variable you will be using 
Here 
showSection is name of variable we wil be using
setShowSection is name of the function that will be updating this variable
1 is the initial value this variable will be having
```
const [showSection, setShowSection] = useState(1);
```

Here is another example for a boolean variable
```
const [showAbout, setShowAbout] = useState(false);
```

## Make a function that will be changing this variable
This is the function you will be calling on event from your component in return of your function
```   
   function handleSectionClick(){
        setShowSection(showSection === 1 ? 2 : 1);
        //setShowAbout(!showAbout); // this is incase you want to toggle boolean
    };
```

## Call this function in your component on an event
```
<div  onClick={handleSectionClick}>
</div>
```

## Use this variable to show/hide components like this
```
{showSection === 1 && <div>
This component is visible when showSection is 1
</div>}
{showSection === 2 && <div>
This Component is visible when shoeSection is 2
</div>}

```

## Time based Show/Hide
Some times you might want a component to restore its state you can achieve this using setTimeout like this withing your function

```
    function handleSectionClick(){
        setShowSection(showSection === 1 ? 2 : 1);
        setShowAbout(!showAbout);
        setTimeout(()=>{setShowAbout(false);setShowSection(1)},10000);
    };
```

# Using Google fonts
You no more need to make external calls to **google/fonts** library now we have **next/font/google**here are the steps to using fonts internally

## Import your font
Here font Alata is being imported
```
import { Alata } from "next/font/google";
```

## Create a const object with subsets and weight
```
const alata=Alata({
    subsets:['latin'],
    weight:"400"
})
```

## Assign it to the components className
Note tht here we added div instead of directly assigning it to h1 classname thats because we might want to use h1 classname for other CSS settings of our text
```
<div className={alata.className}>   
<h1>SAMPLE TEXT</h1>
</div>
```

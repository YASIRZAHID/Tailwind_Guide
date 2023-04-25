# Tailwind_Guide
this guide features the use of tailwind features for quick referencing during web development using next.js 13.1
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

# Using image component that adjusts itself on load to accupy available space

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
```

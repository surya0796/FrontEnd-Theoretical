Let's start with explaining the folder structure followed in this project:-

src folder
|
|-- Components {this folder contains all small components used in any page}
|
|-- Layouts {this folder contains the all basic components that are commo for any design template normally header,
|   footer, side nav type of common component and an <Outlet/> for the content is placed}
|
|-- Pages {consider it as one more layer in which you write the component which replaces above <Outlet/> component }
|
|-- Utility {this folder contains functions which are widely used across the code base. for example: api call function, debouncing
|   hook,setTimeout hook, localStorage hook }
|
|-- Context {make different contexts for different cases}
|
|-- Skeleton { creating skeletons for different templates }
|
|-- Routing { make separate route file inside it. }
|
|-- Assests {all the images, videos are put in this folder}




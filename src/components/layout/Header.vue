<template>
  <header>
    <pre id="title">

 __       _______.  ______    __          ___   .___________. __    ______   .__   __. 
|  |     /       | /  __  \  |  |        /   \  |           ||  |  /  __  \  |  \ |  | 
|  |    |   (----`|  |  |  | |  |       /  ^  \ `---|  |----`|  | |  |  |  | |   \|  | 
|  |     \   \    |  |  |  | |  |      /  /_\  \    |  |     |  | |  |  |  | |  . `  | 
|  | .----)   |   |  `--'  | |  `----./  _____  \   |  |     |  | |  `--'  | |  |\   | 
|__| |_______/     \______/  |_______/__/     \__\  |__|     |__|  \______/  |__| \__| 
                                                                                       
 </pre>
        <p>COMMANDS: north, south, east, west</p> 
  </header>
</template>
<script>
export default {
  name: "Header"
};
</script>
<style type="scss" scoped>
@media only screen and (max-width: 600px) {
  pre {
    font-size: 0.5em;
  }
}
 p {
    background-color:#000;
     width: 41%;
    padding:.5em;
    margin:1em auto;
    
  }
</style>



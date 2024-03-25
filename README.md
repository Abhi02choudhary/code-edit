<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CODE EDITOR</title>
  <style>
    body {
      width: 100%;
      height: 100%;
      display: flex;
      margin: 0; /* Remove default margin */
      overflow: hidden; /* Prevent scrollbars */
      background-color: rgb(56, 54, 52);
    }
    .leftPart {
      flex-basis: 50%; /* Let it grow to fill the space */
      background-color: rgb(139, 153, 141);
      height: 100vh;
      gap: 5px;
      display: flex;
      flex-direction: column;
      overflow: hidden; /* Prevent scrollbars */
    }
    .content {
      flex-grow: 1;
      background-color: rgb(178, 205, 145);
      overflow: hidden; /* Prevent scrollbars */
      display: flex;
      flex-direction: column;
      gap: 5px;
    }
    .rightPart {
      flex-basis: 50%;
      background-color: rgb(222, 218, 218);
      height: 100vh;
      overflow: hidden; /* Prevent scrollbars */
      color: black;
    }
    .leftPart .content textarea {
      width: 100%;
      height: 100%;
      background-color: black;
      color: white;
      outline: none;
      border: none;
      overflow: auto; /* Allow scrolling within textareas if needed */
    }
    
  </style>
</head>
<body>
  <div class="leftPart">
    <div class="content">
      <label>HTML</label>
      <textarea></textarea>
    </div>
    <div class="content">
      <label>CSS</label>
      <textarea></textarea>
    </div>
    <div class="content">
      <label>JS</label>
      <textarea></textarea>
    </div>
  </div>
  <div class="rightPart">
    <label>Output</label>
    <iframe id="Output" width="100%" height="80%"></iframe>
  </div>
</body>
<script>
  let Output=document.querySelector("#Output");
  let allInput=document.querySelectorAll(".leftPart textarea")

  let htmlCode,cssCode,jsCode='';
  allInput.forEach((el,index)=>{
    el.addEventListener("keyup",()=>{
      if(index==0){
           htmlCode=el.value;
      }
      if(index==1){
           cssCode=el.value;
      }
      if(index==2){
           jsCode=el.value;
      }
      Output.contentDocument.body.innerHTML=htmlCode;
      Output.contentDocument.head.innerHTML=`<style>${cssCode}</style>`;
      Output.contentWindow.eval(jsCode);
    })
  })
</script>

</html>


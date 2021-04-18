<script>
  let total =0;
  let console="";
  let state = null;
  function resolveState(){
      switch(state){
		  case "add":
		     total += parseFloat(console);
			 console = "0";
			 break;
		  case "substract":
			  total -= parseFloat(console);
			  console = "0";
			  break;
		  case "mul":
		     total *= parseFloat(console);
			 console = "0";
			 break;
		  case "divide":
		     total /= parseFloat(console);
			 console = "0";
			 break;
		  default:
		     total = parseFloat(console);
			 console = "0";
			 break;
	  }

  }

  function setOperation(operation){
    resolveState();
	state = operation;

  }

  function setValue(value){
      if(console.toString() == "0" || state == "equal"){
		  console = "";
	  }
	  if(state == "equal"){
		  state = null;
	  }
	  if(value == "C"){
		  total = 0;
		  state = null;
		  console ="";
		  return;
	  }
	  console = console + value;

  }
 
  function equal(){
      resolveState();
	  console= total;
	  state= "equal";
   
  }

</script>



<div class="calculator">
	<h1>Svelte calculator</h1>
	<input type="text" bind:value={console}/>
	<div class="buttons">
        <div class="operations">
			<button on:click={()=>{setOperation('add');}}>
              +
			</button>

			<button on:click={()=>{setOperation('substract');}}>
				-
			</button>

			<button on:click={()=>{setOperation('mul');}}>
				&times;
			</button>

			<button on:click={()=>{setOperation('divide');}}>
				&divide;
			</button>
		</div>
        <div class="numbers">
			<div>
				<button on:click={()=>{setValue(7);}}>
					7
				</button>
				<button on:click={()=>{setValue(8);}}>
					8
				</button>
				<button on:click={()=>{setValue(9);}}>
					9
				</button>
			</div>
			<div>
				<button on:click={()=>{setValue(4);}}>
					4
				</button>
				<button on:click={()=>{setValue(5);}}>
					5
				</button>
				<button on:click={()=>{setValue(6);}}>
					6
				</button>
			</div>
			<div>
				<button on:click={()=>{setValue(1);}}>
					1
				</button>
				<button on:click={()=>{setValue(2);}}>
					2
				</button>
				<button on:click={()=>{setValue(3);}}>
					3
				</button>
			</div>
			<div>
				<button on:click={()=>{setValue('.');}}>
					.
				</button>
				<button on:click={()=>{setValue(0);}}>
					0
				</button>
				<button on:click={()=>{setValue('C');}}>
					C
				</button>
			</div>
		</div>
		<div class = "equal">
			<button on:click={equal}>
               =
			</button>
		</div>
	</div>

</div>

<style>
    :global(body){
        background-color: lightseagreen;
        background-image: url("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQvt-X3P7pRvL-axAMG1js3r1WuLAEj5KGI_A&usqp=CAU");
		background-size: 100%;
    }
	h1{
		align-items: center;
		text-align: center;
	}
   .calculator{
	   position: absolute;
	   top: 50%;
	   left: 50%;
	   transform: translate(-50%,-50%);
	   width: 300px;
	   border: 1px solid #eee;
	   box-shadow: 2px 2px 5px 5px;
	   padding: 10px;
	   background-color: white;
   }
   .calculator input{
	   width: 100%;
	   padding: 20px;
	   outline: none;
	   text-align: right;
	   font-size: 20px ;
   }
   .calculator .buttons {
	   display: flex;
	   flex-wrap: wrap;
   }

   .calculator .buttons .operations{
	   display: flex;
	   justify-content: space-between;
	   width: 100%;
   }
   .calculator .buttons .operations button{
	   width: 24%;
   }

   .calculator .buttons .numbers {
      width: 75%;
   }
   .calculator .buttons .numbers > div{
	   display: flex;
	   justify-content: space-between;
   }
   .calculator .buttons .numbers > div button {
     width: 32%;
   }
   .calculator .equal {
	   flex: 1;
   }
   .calculator .equal button {
	   margin-left: 5%;
	   width: 95%;
	   height: 95%;
	   background: #00acee;
	   color: #eee;
   }

   .calculator button{
	   outline: none;
   }

</style>
<script>
  let input1;
  let input2;
  let k1;
  let k2;
  let cur1;
  let cur2;
  let selectValue1;
  let selectValue2;

  function changeInput(){
    if(cur1 !== undefined){
      let sum = input1 * cur1;
      input2 = (sum / cur2).toFixed(3);
    } else {
      input2 = (Number(input1) * Number(k2)).toFixed(3);
    }
  }

  function changeOutput(){
    if(cur2 !== undefined){
      let sum = input2 * cur2;
      input1 = (sum / cur1).toFixed(3);
    } else {
      input1 = (Number(input2) / Number(k2)).toFixed(3);
    }
  }

  function similarInputs(){
    [selectValue1, selectValue2] = [selectValue2, selectValue1];
    if(input1 ||input2){
      [input1, input2] = [input2, input1];
    }
  };

  let rates = {};
  let arrKeys = [];
  const getCurrency = async () => {
    const result = await fetch('https://open.er-api.com/v6/latest/USD');
    const resultResponce = await result.json();
    const data = await resultResponce;
    rates = data.rates;
    arrKeys = Object.keys(rates);
  }
  
  getCurrency();
  
</script>

<div class="converter_block">
  <div>
    <label for="">
      <select multiple bind:value={selectValue1} on:change={() => {
        let key1 = selectValue1[0]
        if(key1 !== 'USD'){
          cur1 = 1/rates[key1];
          k1 = rates[key1];
        } else{
          k1 = rates[key1];
          cur1 = 1/rates[key1];
          console.log(rates[key1])
        }
      }}  name="" id="1">
        {#each arrKeys as el}
          <option value={el}>
            {el}
          </option>
        {/each}
      </select>
      <input type="number" placeholder="chose the currency and enter value" bind:value={input1} on:input={changeInput}/>
    </label>
  </div>
  
  <button class="btn" type="button" on:click={similarInputs}><p>↔</p></button>
  
  <div>
    <label for="">
      <select multiple bind:value={selectValue2} on:change={() => {
        let key2 = selectValue2[0]
        if(key2 !== 'USD'){
          cur2 = 1/rates[key2];
          k2 = rates[key2];
        } else{
          k2 = rates[key2];
          cur2 = 1/rates[key2];
          console.log(rates[key2])
        }
      }} name="" id="2">
        {#each arrKeys as el1}
          <option value={el1}>
            {el1}
          </option>
        {/each}
      </select>
      <input type="number" placeholder="get the result" bind:value={input2} on:input={changeOutput}/>
    </label>
  </div>
</div>

<style>
  .converter_block{
    display: flex;
  }
  .btn{
    width: 90px;
    height: 55px;
    margin: 50px 40px;
    padding: 0;
  }
  .btn:hover{
    border: 2px solid #333;
  }
</style>

<script>
  export let value;

</script>

<button on:click={()=>{value = !value;
}}>
    {value}
</button>

<style>
  button{
    width: 86px;
    height: 42px;
  }
</style>
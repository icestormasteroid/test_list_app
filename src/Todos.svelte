<script>
import { text } from "svelte/internal";

import App from "./App.svelte";
import { slide } from 'svelte/transition';

    let todoItem = '';
    let todoList = [];
    //add items from input field into array
    function addToList() {
        if (!todoItem) return;
        todoList = [...todoList, {
            text: todoItem
        }];
        todoItem = '';
    }
    
    //remove items from array
    function removeFromList(index) {
        todoList.splice(index, 1);
        todoList = todoList;        
    }
</script>

<form on:submit|preventDefault={addToList}>
    <input bind:value={todoItem}>
        <button class="button is-primary">
          <span class="icon is-small">
            <i class="fas fa-plus"></i>
          </span>
        </button>
</form>

<div class="container">
<ol class="todoList">
    {#each todoList as item, index}
    <li transition:slide="{{ y: 20, duration: 120 }}">
    
    <div class="asdjklj">
    
    <div class="check"><input bind:checked={item.status} type="checkbox" class="checkbox"></div>

    <div class="items"><span class:checked={item.status}>{item.text}</span></div>
    <div class="x"><button style class="delete" type="button" on:click={() => removeFromList(index)} ></button></div>

    </div>

    <!--
    <button class="delete" type="button" on:click={() => removeFromList(index)} ></button>
    -->
    </li>
    {/each}
</ol>
</div>

<style>

    .todoList {
    list-style: none;
    }

    .checkbox {
        background-color: purple;
    }

    .checked {
        text-decoration: line-through;
    }

    .container {
        display: flex;
        justify-content: center;

    }

    .asdjklj {
       /*display: flex;
        flex-wrap: wrap;
        flex-direction: row;
        justify-content: space-evenly;
        align-items: stretch;


        */
    display:flex;
    flex-wrap:wrap;
    flex-direction:row;
    justify-content:space-between;
    align-items:stretch;
    background-color: rgb(228, 228, 228);
    border-radius: 5px ;
    margin: 0.8em 0em;
    padding: 0.8em 1em;
    }

    .check {
    order: 1;
    flex-basis: auto;
    }
    
    .items {
    order: 2;
    text-align: left;
    padding: 0em 5em;
    flex-basis: auto;

    }

    .x {
    order: 3;
    justify-content: right;    
    flex-basis: auto;
  }
</style>
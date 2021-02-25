---
title: JavaScript tests
date: 2020-10-29 12:30:00 HH:MM:SS +0100
categories: [Running, Trail]
tags: [running, trail, javascript, js]
---

<script>
// $("input[name='masknumber']").on("keyup", function(){
//     $("input[name='number']").val(destroyMask(this.value));
//     this.value = createMask($("input[name='number']").val());
// })

// function createMask(string){
//   console.log(string)
// 	return string.replace(/(\d{2})(\d{3})(\d{2})/,"$1-$2-$3");
// }

// function destroyMask(string){
//   console.log(string)
// 	return string.replace(/\D/g,'').substring(0, 8);
// }

$("input[name='minutes']").on("keyup", function(){
    $("input[name='toto']").val(this.value);
    // this.value = createMask($("input[name='number']").val());
})

</script>

<!-- <input type="text" name="masknumber">
<input type="text" name="number" style="display:none;"> -->

<input type="number" id="minutes" name="minutes" min="00" max="59">

<input type="number" id="seconds" name="seconds" min="00" max="59">

<input type="text" name="toto">
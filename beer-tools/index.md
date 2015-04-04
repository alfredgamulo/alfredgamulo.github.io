---
layout: page
title: Beer Tools
description: "Handy calculators for brewing"
image:
  feature: abstract-11.jpg
  credit: dargadgetz
  creditlink: http://www.dargadgetz.com/ios-7-abstract-wallpaper-pack-for-iphone-5-and-ipod-touch-retina/
share: true
---
{::options parse_block_html="true" /}

Some beer references and calculators for homebrewing. We get about a 80% efficiency for a 5.5 gallon system, so those are somewhat built into the page calculators.

Calculator using table of typical malt yields[^1]

<script>
function calculate()
{
	var malt1 = beercalculator.elements["malt1"];
	var malt2 = beercalculator.elements["malt2"];
	var malt3 = beercalculator.elements["malt3"];
	var malt4 = beercalculator.elements["malt4"];
	var malt5 = beercalculator.elements["malt5"];
	var malt6 = beercalculator.elements["malt6"];
	var malt7 = beercalculator.elements["malt7"];
	var malt8 = beercalculator.elements["malt8"];
	var malt9 = beercalculator.elements["malt9"];
	var malt10 = beercalculator.elements["malt10"];
	var malt11 = beercalculator.elements["malt11"];
	var malt12 = beercalculator.elements["malt12"];
	var malt13 = beercalculator.elements["malt13"];
	var malt14 = beercalculator.elements["malt14"];
	var malt15 = beercalculator.elements["malt15"];
	var malt16 = beercalculator.elements["malt16"];
	var malt17 = beercalculator.elements["malt17"];
	var malt18 = beercalculator.elements["malt18"];
	var malt19 = beercalculator.elements["malt19"];
	var malt20 = beercalculator.elements["malt20"];
	var malt21 = beercalculator.elements["malt21"];
	var malt22 = beercalculator.elements["malt22"];
	var malt23 = beercalculator.elements["malt23"];
	var malt24 = beercalculator.elements["malt24"];
	var malt25 = beercalculator.elements["malt25"];


	var total = 0;


if(malt1.value!=""){
	total+= 30 * parseInt(malt1.value) / 5.5;
}
if(malt2.value!=""){
	total+= 28 * parseInt(malt2.value) / 5.5;
}
if(malt3.value!=""){
	total+= 30 * parseInt(malt3.value) / 5.5;
}
if(malt4.value!=""){
	total+= 28 * parseInt(malt4.value) / 5.5;
}
if(malt5.value!=""){
	total+= 28 * parseInt(malt5.value) / 5.5;
}
if(malt6.value!=""){
	total+= 28 * parseInt(malt6.value) / 5.5;
}
if(malt7.value!=""){
	total+= 26 * parseInt(malt7.value) / 5.5;
}
if(malt8.value!=""){
	total+= 26 * parseInt(malt8.value) / 5.5;
}
if(malt9.value!=""){
	total+= 28 * parseInt(malt9.value) / 5.5;
}
if(malt10.value!=""){
	total+= 27 * parseInt(malt10.value) / 5.5;
}
if(malt11.value!=""){
	total+= 27 * parseInt(malt11.value) / 5.5;
}
if(malt12.value!=""){
	total+= 26 * parseInt(malt12.value) / 5.5;
}
if(malt13.value!=""){
	total+= 25 * parseInt(malt13.value) / 5.5;
}
if(malt14.value!=""){
	total+= 22 * parseInt(malt14.value) / 5.5;
}
if(malt15.value!=""){
	total+= 20 * parseInt(malt15.value) / 5.5;
}
if(malt16.value!=""){
	total+= 20 * parseInt(malt16.value) / 5.5;
}
if(malt17.value!=""){
	total+= 30 * parseInt(malt17.value) / 5.5;
}
if(malt18.value!=""){
	total+= 23 * parseInt(malt18.value) / 5.5;
}
if(malt19.value!=""){
	total+= 26 * parseInt(malt19.value) / 5.5;
}
if(malt20.value!=""){
	total+= 31 * parseInt(malt20.value) / 5.5;
}
if(malt21.value!=""){
	total+= 26 * parseInt(malt21.value) / 5.5;
}
if(malt22.value!=""){
	total+= 29 * parseInt(malt22.value) / 5.5;
}
if(malt23.value!=""){
	total+= 30 * parseInt(malt23.value) / 5.5;
}
if(malt24.value!=""){
	total+= 32 * parseInt(malt24.value) / 5.5;
}
if(malt25.value!=""){
	total+= 37 * parseInt(malt25.value) / 5.5;
}


var total = (1+(total/1000));
console.log(total);
beercalculator.elements["OG"].value=total.toFixed(3);


}
</script>

<form action="" id="beercalculator" onsubmit="return false;">

| Malt Type | Max. PPG | Typical PPG (80%) | Pounds |
|:----------|:--------:|:-----------------:|:---------:|
|2 Row Lager Malt | 37 | 30 | <input type="number" name="malt1" id="malt1" onchange="calculate()" /> |
|6 Row Base Malt | 35 | 28 | <input type="number" name="malt2" id="malt2" onchange="calculate()" /> |
|2 Row Pale Ale Malt | 38 | 30 | <input type="number" name="malt3" id="malt3" onchange="calculate()" /> |
|Biscuit/Victory Malt | 35 | 28 | <input type="number" name="malt4" id="malt4" onchange="calculate()" /> |
|Vienna Malt | 35 | 28 | <input type="number" name="malt5" id="malt5" onchange="calculate()" /> |
|Munich Malt | 35 | 28 | <input type="number" name="malt6" id="malt6" onchange="calculate()" /> |
|Brown Malt | 32 | 26 | <input type="number" name="malt7" id="malt7" onchange="calculate()" /> |
|Dextrin Malt | 32 | 26 | <input type="number" name="malt8" id="malt8" onchange="calculate()" /> |
|Light Crystal (10 - 15L) | 35 | 28 | <input type="number" name="malt9" id="malt9" onchange="calculate()" /> |
|Pale Crystal (25 - 40L) | 34 | 27 | <input type="number" name="malt10" id="malt10" onchange="calculate()" /> |
|Medium Crystal (60 - 75L) | 34 | 27 | <input type="number" name="malt11" id="malt11" onchange="calculate()" /> |
|Dark Crystal (120L) | 33 | 26 | <input type="number" name="malt12" id="malt12" onchange="calculate()" /> |
|Special B | 31 | 25 | <input type="number" name="malt13" id="malt13" onchange="calculate()" /> |
|Chocolate Malt | 28 | 22 | <input type="number" name="malt14" id="malt14" onchange="calculate()" /> |
|Roast Barley | 25 | 20 | <input type="number" name="malt15" id="malt15" onchange="calculate()" /> |
|Black Patent Malt | 25 | 20 | <input type="number" name="malt16" id="malt16" onchange="calculate()" /> |
|Wheat Malt | 37 | 30 | <input type="number" name="malt17" id="malt17" onchange="calculate()" /> |
|Rye Malt | 29 | 23 | <input type="number" name="malt18" id="malt18" onchange="calculate()" /> |
|Oatmeal (Flaked) | 32 | 26 | <input type="number" name="malt19" id="malt19" onchange="calculate()" /> |
|Corn (Flaked) | 39 | 31 | <input type="number" name="malt20" id="malt20" onchange="calculate()" /> |
|Barley (Flaked) | 32 | 26 | <input type="number" name="malt21" id="malt21" onchange="calculate()" /> |
|Wheat (Flaked) | 36 | 29 | <input type="number" name="malt22" id="malt22" onchange="calculate()" /> |
|Rice (Flaked) | 38 | 30 | <input type="number" name="malt23" id="malt23" onchange="calculate()" /> |
|Malto - Dextrin Powder | 40 | 32 | <input type="number" name="malt24" id="malt24" onchange="calculate()" /> |
|Sugar (Corn, Cane) | 46 | 37 | <input type="number" name="malt25" id="malt25" onchange="calculate()" /> |
|====
|Lovibond| ||<input type="text" name="Lovibond"> |
|Original Gravity   | ||<input type="number" name="OG" id="OG"> |
{: rules="groups"}

</form>




[^1]: [http://www.howtobrew.com/section2/chapter12-4-1.html](http://www.howtobrew.com/section2/chapter12-4-1.html)


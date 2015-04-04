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
	var weight = 0;

	if(malt1.value!=""){
		total+= 30 * parseFloat(malt1.value) / 5.5;
		weight+=parseFloat(malt1.value);
	}
	if(malt2.value!=""){
		total+= 28 * parseFloat(malt2.value) / 5.5;
		weight+=parseFloat(malt2.value);
	}
	if(malt3.value!=""){
		total+= 30 * parseFloat(malt3.value) / 5.5;
		weight+=parseFloat(malt3.value);
	}
	if(malt4.value!=""){
		total+= 28 * parseFloat(malt4.value) / 5.5;
		weight+=parseFloat(malt4.value);
	}
	if(malt5.value!=""){
		total+= 28 * parseFloat(malt5.value) / 5.5;
		weight+=parseFloat(malt5.value);
	}
	if(malt6.value!=""){
		total+= 28 * parseFloat(malt6.value) / 5.5;
		weight+=parseFloat(malt6.value);
	}
	if(malt7.value!=""){
		total+= 26 * parseFloat(malt7.value) / 5.5;
		weight+=parseFloat(malt7.value);
	}
	if(malt8.value!=""){
		total+= 26 * parseFloat(malt8.value) / 5.5;
		weight+=parseFloat(malt8.value);
	}
	if(malt9.value!=""){
		total+= 28 * parseFloat(malt9.value) / 5.5;
		weight+=parseFloat(malt9.value);
	}
	if(malt10.value!=""){
		total+= 27 * parseFloat(malt10.value) / 5.5;
		weight+=parseFloat(malt10.value);
	}
	if(malt11.value!=""){
		total+= 27 * parseFloat(malt11.value) / 5.5;
		weight+=parseFloat(malt11.value);
	}
	if(malt12.value!=""){
		total+= 26 * parseFloat(malt12.value) / 5.5;
		weight+=parseFloat(malt12.value);
	}
	if(malt13.value!=""){
		total+= 25 * parseFloat(malt13.value) / 5.5;
		weight+=parseFloat(malt13.value);
	}
	if(malt14.value!=""){
		total+= 22 * parseFloat(malt14.value) / 5.5;
		weight+=parseFloat(malt14.value);
	}
	if(malt15.value!=""){
		total+= 20 * parseFloat(malt15.value) / 5.5;
		weight+=parseFloat(malt15.value);
	}
	if(malt16.value!=""){
		total+= 20 * parseFloat(malt16.value) / 5.5;
		weight+=parseFloat(malt16.value);
	}
	if(malt17.value!=""){
		total+= 30 * parseFloat(malt17.value) / 5.5;
		weight+=parseFloat(malt17.value);
	}
	if(malt18.value!=""){
		total+= 23 * parseFloat(malt18.value) / 5.5;
		weight+=parseFloat(malt18.value);
	}
	if(malt19.value!=""){
		total+= 26 * parseFloat(malt19.value) / 5.5;
		weight+=parseFloat(malt19.value);
	}
	if(malt20.value!=""){
		total+= 31 * parseFloat(malt20.value) / 5.5;
		weight+=parseFloat(malt20.value);
	}
	if(malt21.value!=""){
		total+= 26 * parseFloat(malt21.value) / 5.5;
		weight+=parseFloat(malt21.value);
	}
	if(malt22.value!=""){
		total+= 29 * parseFloat(malt22.value) / 5.5;
		weight+=parseFloat(malt22.value);
	}
	if(malt23.value!=""){
		total+= 30 * parseFloat(malt23.value) / 5.5;
		weight+=parseFloat(malt23.value);
	}
	if(malt24.value!=""){
		total+= 32 * parseFloat(malt24.value) / 5.5;
		weight+=parseFloat(malt24.value);
	}
	if(malt25.value!=""){
		total+= 37 * parseFloat(malt25.value) / 5.5;
		weight+=parseFloat(malt25.value);
	}

	console.log("weight: " + weight);

	var total = (1+(total/1000));
	console.log("total points: " + total);

	beercalculator.elements["OG"].value=total.toFixed(3);

	var water = 1.25*weight;
	console.log("water volume: " + water);

	beercalculator.elements["Water"].value=water.toFixed(3);

	var gtemp = beercalculator.elements["GTemp"];
	var ttemp = beercalculator.elements["TTemp"];
	if(gtemp.value!="" && ttemp!=""){
		ttemp = parseFloat(ttemp.value);
		gtemp = parseFloat(gtemp.value);
		var stemp=(0.2/1.25)*(ttemp - gtemp)+ttemp;
		console.log("strike temp: " + stemp);
		beercalculator.elements["Temp"].value=stemp.toFixed(3);
	}

}
</script>

<form action="" id="beercalculator" onsubmit="return false;">

| Malt Type | Max. PPG | Typical PPG (80%) | Pounds |
|:----------|:--------:|:-----------------:|:---------:|
|2 Row Lager Malt | 37 | 30 | <input type="number" min="0" step="0.125" name="malt1" id="malt1" onchange="calculate()" /> |
|6 Row Base Malt | 35 | 28 | <input type="number" min="0" step="0.125" name="malt2" id="malt2" onchange="calculate()" /> |
|2 Row Pale Ale Malt | 38 | 30 | <input type="number" min="0" step="0.125" name="malt3" id="malt3" onchange="calculate()" /> |
|Biscuit/Victory Malt | 35 | 28 | <input type="number" min="0" step="0.125" name="malt4" id="malt4" onchange="calculate()" /> |
|Vienna Malt | 35 | 28 | <input type="number" min="0" step="0.125" name="malt5" id="malt5" onchange="calculate()" /> |
|Munich Malt | 35 | 28 | <input type="number" min="0" step="0.125" name="malt6" id="malt6" onchange="calculate()" /> |
|Brown Malt | 32 | 26 | <input type="number" min="0" step="0.125" name="malt7" id="malt7" onchange="calculate()" /> |
|Dextrin Malt | 32 | 26 | <input type="number" min="0" step="0.125" name="malt8" id="malt8" onchange="calculate()" /> |
|Light Crystal (10 - 15L) | 35 | 28 | <input type="number" min="0" step="0.125" name="malt9" id="malt9" onchange="calculate()" /> |
|Pale Crystal (25 - 40L) | 34 | 27 | <input type="number" min="0" step="0.125" name="malt10" id="malt10" onchange="calculate()" /> |
|Medium Crystal (60 - 75L) | 34 | 27 | <input type="number" min="0" step="0.125" name="malt11" id="malt11" onchange="calculate()" /> |
|Dark Crystal (120L) | 33 | 26 | <input type="number" min="0" step="0.125" name="malt12" id="malt12" onchange="calculate()" /> |
|Special B | 31 | 25 | <input type="number" min="0" step="0.125" name="malt13" id="malt13" onchange="calculate()" /> |
|Chocolate Malt | 28 | 22 | <input type="number" min="0" step="0.125" name="malt14" id="malt14" onchange="calculate()" /> |
|Roast Barley | 25 | 20 | <input type="number" min="0" step="0.125" name="malt15" id="malt15" onchange="calculate()" /> |
|Black Patent Malt | 25 | 20 | <input type="number" min="0" step="0.125" name="malt16" id="malt16" onchange="calculate()" /> |
|Wheat Malt | 37 | 30 | <input type="number" min="0" step="0.125" name="malt17" id="malt17" onchange="calculate()" /> |
|Rye Malt | 29 | 23 | <input type="number" min="0" step="0.125" name="malt18" id="malt18" onchange="calculate()" /> |
|Oatmeal (Flaked) | 32 | 26 | <input type="number" min="0" step="0.125" name="malt19" id="malt19" onchange="calculate()" /> |
|Corn (Flaked) | 39 | 31 | <input type="number" min="0" step="0.125" name="malt20" id="malt20" onchange="calculate()" /> |
|Barley (Flaked) | 32 | 26 | <input type="number" min="0" step="0.125" name="malt21" id="malt21" onchange="calculate()" /> |
|Wheat (Flaked) | 36 | 29 | <input type="number" min="0" step="0.125" name="malt22" id="malt22" onchange="calculate()" /> |
|Rice (Flaked) | 38 | 30 | <input type="number" min="0" step="0.125" name="malt23" id="malt23" onchange="calculate()" /> |
|Malto - Dextrin Powder | 40 | 32 | <input type="number" min="0" step="0.125" name="malt24" id="malt24" onchange="calculate()" /> |
|Sugar (Corn, Cane) | 46 | 37 | <input type="number" min="0" step="0.125" name="malt25" id="malt25" onchange="calculate()" /> |
| | |||
|**Temperature**   | |||
|====
|Target Temperature in F   | ||<input type="number" name="TTemp" id="TTemp" onchange="calculate()" /> |
|Grain Temperature in F   | ||<input type="number" name="GTemp" id="GTemp" onchange="calculate()" /> |
| | |||
|**Results**   | |||
|====
|Original Gravity   | ||<input type="number" name="OG" id="OG" readonly style="border:0"/> |
|Water for mash in quarts   | ||<input type="number" name="Water" id="Water" readonly style="border:0"/> |
|Strike Temperature in F   | ||<input type="number" name="Temp" id="Temp" readonly style="border:0" /> |
{: rules="groups"}

</form>




[^1]: [http://www.howtobrew.com/section2/chapter12-4-1.html](http://www.howtobrew.com/section2/chapter12-4-1.html)


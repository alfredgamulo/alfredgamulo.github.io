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
	var vol = beercalculator.elements["Vol"];
	var ppgyield = beercalculator.elements["PPG"];

	var tworowlager = beercalculator.elements["tworowlager"];
	var sixrowbase = beercalculator.elements["sixrowbase"];
	var tworowpaleale = beercalculator.elements["tworowpaleale"];
	var victory = beercalculator.elements["victory"];
	var vienna = beercalculator.elements["vienna"];
	var munich = beercalculator.elements["munich"];
	var brown = beercalculator.elements["brown"];
	var dextrin = beercalculator.elements["dextrin"];
	var lightcrystal = beercalculator.elements["lightcrystal"];
	var palecrystal = beercalculator.elements["palecrystal"];
	var mediumcrystal = beercalculator.elements["mediumcrystal"];
	var darkcrystal = beercalculator.elements["darkcrystal"];
	var specialb = beercalculator.elements["specialb"];
	var chocolate = beercalculator.elements["chocolate"];
	var roastbarley = beercalculator.elements["roastbarley"];
	var blackpatent = beercalculator.elements["blackpatent"];
	var wheat = beercalculator.elements["wheat"];
	var rye = beercalculator.elements["rye"];
	var flakedoatmeal = beercalculator.elements["flakedoatmeal"];
	var flakedcorn = beercalculator.elements["flakedcorn"];
	var flakedbarley = beercalculator.elements["flakedbarley"];
	var flakedwheat = beercalculator.elements["flakedwheat"];
	var flakedrice = beercalculator.elements["flakedrice"];
	var maltodextrin = beercalculator.elements["maltodextrin"];
	var sugar = beercalculator.elements["sugar"];


	var total = 0;
	var weight = 0;

	if(vol.value!=""){
		vol = parseFloat(vol.value);
	} else {
		vol = 5.5;
	}

	if(ppgyield.value!=""){
		ppgyield = parseFloat(ppgyield.value);
	} else {
		ppgyield = 0.80;
	}

	if(tworowlager.value!=""){
		total+= 37 * (ppgyield) * parseFloat(tworowlager.value) / vol;
		weight+=parseFloat(tworowlager.value);
	}
	if(sixrowbase.value!=""){
		total+= 35 * (ppgyield) * parseFloat(sixrowbase.value) / vol;
		weight+=parseFloat(sixrowbase.value);
	}
	if(tworowpaleale.value!=""){
		total+= 38 * (ppgyield) * parseFloat(tworowpaleale.value) / vol;
		weight+=parseFloat(tworowpaleale.value);
	}
	if(victory.value!=""){
		total+= 35 * (ppgyield) * parseFloat(victory.value) / vol;
		weight+=parseFloat(victory.value);
	}
	if(vienna.value!=""){
		total+= 35 * (ppgyield) * parseFloat(vienna.value) / vol;
		weight+=parseFloat(vienna.value);
	}
	if(munich.value!=""){
		total+= 35 * (ppgyield) * parseFloat(munich.value) / vol;
		weight+=parseFloat(munich.value);
	}
	if(brown.value!=""){
		total+= 32 * (ppgyield) * parseFloat(brown.value) / vol;
		weight+=parseFloat(brown.value);
	}
	if(dextrin.value!=""){
		total+= 32 * (ppgyield) * parseFloat(dextrin.value) / vol;
		weight+=parseFloat(dextrin.value);
	}
	if(lightcrystal.value!=""){
		total+= 35 * (ppgyield) * parseFloat(lightcrystal.value) / vol;
		weight+=parseFloat(lightcrystal.value);
	}
	if(palecrystal.value!=""){
		total+= 34 * (ppgyield) * parseFloat(palecrystal.value) / vol;
		weight+=parseFloat(palecrystal.value);
	}
	if(mediumcrystal.value!=""){
		total+= 34 * (ppgyield) * parseFloat(mediumcrystal.value) / vol;
		weight+=parseFloat(mediumcrystal.value);
	}
	if(darkcrystal.value!=""){
		total+= 33 * (ppgyield) * parseFloat(darkcrystal.value) / vol;
		weight+=parseFloat(darkcrystal.value);
	}
	if(specialb.value!=""){
		total+= 31 * (ppgyield) * parseFloat(specialb.value) / vol;
		weight+=parseFloat(specialb.value);
	}
	if(chocolate.value!=""){
		total+= 28 * (ppgyield) * parseFloat(chocolate.value) / vol;
		weight+=parseFloat(chocolate.value);
	}
	if(roastbarley.value!=""){
		total+= 25 * (ppgyield) * parseFloat(roastbarley.value) / vol;
		weight+=parseFloat(roastbarley.value);
	}
	if(blackpatent.value!=""){
		total+= 25 * (ppgyield) * parseFloat(blackpatent.value) / vol;
		weight+=parseFloat(blackpatent.value);
	}
	if(wheat.value!=""){
		total+= 37 * (ppgyield) * parseFloat(wheat.value) / vol;
		weight+=parseFloat(wheat.value);
	}
	if(rye.value!=""){
		total+= 29 * (ppgyield) * parseFloat(rye.value) / vol;
		weight+=parseFloat(rye.value);
	}
	if(flakedoatmeal.value!=""){
		total+= 32 * (ppgyield) * parseFloat(flakedoatmeal.value) / vol;
		weight+=parseFloat(flakedoatmeal.value);
	}
	if(flakedcorn.value!=""){
		total+= 39 * (ppgyield) * parseFloat(flakedcorn.value) / vol;
		weight+=parseFloat(flakedcorn.value);
	}
	if(flakedbarley.value!=""){
		total+= 32 * (ppgyield) * parseFloat(flakedbarley.value) / vol;
		weight+=parseFloat(flakedbarley.value);
	}
	if(flakedwheat.value!=""){
		total+= 36 * (ppgyield) * parseFloat(flakedwheat.value) / vol;
		weight+=parseFloat(flakedwheat.value);
	}
	if(flakedrice.value!=""){
		total+= 38 * (ppgyield) * parseFloat(flakedrice.value) / vol;
		weight+=parseFloat(flakedrice.value);
	}
	if(maltodextrin.value!=""){
		total+= 40 * (ppgyield) * parseFloat(maltodextrin.value) / vol;
		weight+=parseFloat(maltodextrin.value);
	}
	if(sugar.value!=""){
		total+= 46 * (ppgyield) * parseFloat(sugar.value) / vol;
		weight+=parseFloat(sugar.value);
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
|2 Row Lager Malt | 37 | 30 | <input type="number" min="0" step="0.125" name="tworowlager" id="tworowlager" onchange="calculate()" /> |
|6 Row Base Malt | 35 | 28 | <input type="number" min="0" step="0.125" name="sixrowbase" id="sixrowbase" onchange="calculate()" /> |
|2 Row Pale Ale Malt | 38 | 30 | <input type="number" min="0" step="0.125" name="tworowpaleale" id="tworowpaleale" onchange="calculate()" /> |
|Biscuit/Victory Malt | 35 | 28 | <input type="number" min="0" step="0.125" name="victory" id="victory" onchange="calculate()" /> |
|Vienna Malt | 35 | 28 | <input type="number" min="0" step="0.125" name="vienna" id="vienna" onchange="calculate()" /> |
|Munich Malt | 35 | 28 | <input type="number" min="0" step="0.125" name="munich" id="munich" onchange="calculate()" /> |
|Brown Malt | 32 | 26 | <input type="number" min="0" step="0.125" name="brown" id="brown" onchange="calculate()" /> |
|Dextrin Malt | 32 | 26 | <input type="number" min="0" step="0.125" name="dextrin" id="dextrin" onchange="calculate()" /> |
|Light Crystal (10 - 15L) | 35 | 28 | <input type="number" min="0" step="0.125" name="lightcrystal" id="lightcrystal" onchange="calculate()" /> |
|Pale Crystal (25 - 40L) | 34 | 27 | <input type="number" min="0" step="0.125" name="palecrystal" id="palecrystal" onchange="calculate()" /> |
|Medium Crystal (60 - 75L) | 34 | 27 | <input type="number" min="0" step="0.125" name="mediumcrystal" id="mediumcrystal" onchange="calculate()" /> |
|Dark Crystal (120L) | 33 | 26 | <input type="number" min="0" step="0.125" name="darkcrystal" id="darkcrystal" onchange="calculate()" /> |
|Special B | 31 | 25 | <input type="number" min="0" step="0.125" name="specialb" id="specialb" onchange="calculate()" /> |
|Chocolate Malt | 28 | 22 | <input type="number" min="0" step="0.125" name="chocolate" id="chocolate" onchange="calculate()" /> |
|Roast Barley | 25 | 20 | <input type="number" min="0" step="0.125" name="roastbarley" id="roastbarley" onchange="calculate()" /> |
|Black Patent Malt | 25 | 20 | <input type="number" min="0" step="0.125" name="blackpatent" id="blackpatent" onchange="calculate()" /> |
|Wheat Malt | 37 | 30 | <input type="number" min="0" step="0.125" name="wheat" id="wheat" onchange="calculate()" /> |
|Rye Malt | 29 | 23 | <input type="number" min="0" step="0.125" name="rye" id="rye" onchange="calculate()" /> |
|Oatmeal (Flaked) | 32 | 26 | <input type="number" min="0" step="0.125" name="flakedoatmeal" id="flakedoatmeal" onchange="calculate()" /> |
|Corn (Flaked) | 39 | 31 | <input type="number" min="0" step="0.125" name="flakedcorn" id="flakedcorn" onchange="calculate()" /> |
|Barley (Flaked) | 32 | 26 | <input type="number" min="0" step="0.125" name="flakedbarley" id="flakedbarley" onchange="calculate()" /> |
|Wheat (Flaked) | 36 | 29 | <input type="number" min="0" step="0.125" name="flakedwheat" id="flakedwheat" onchange="calculate()" /> |
|Rice (Flaked) | 38 | 30 | <input type="number" min="0" step="0.125" name="flakedrice" id="flakedrice" onchange="calculate()" /> |
|Malto - Dextrin Powder | 40 | 32 | <input type="number" min="0" step="0.125" name="maltodextrin" id="maltodextrin" onchange="calculate()" /> |
|Sugar (Corn, Cane) | 46 | 37 | <input type="number" min="0" step="0.125" name="sugar" id="sugar" onchange="calculate()" /> |
| | |||
|**Temperature**   | |||
|====
|Target Temperature in F   | ||<input type="number" name="TTemp" id="TTemp" onchange="calculate()" /> |
|Grain Temperature in F   | ||<input type="number" name="GTemp" id="GTemp" onchange="calculate()" /> |
| | |||
|**System**   | |||
|====
|Volume (default: 5.5 gal.)   | ||<input type="number" name="Vol" id="Vol" onchange="calculate()" placeholder="5.5" min="0"/> |
|PPG Yield (default: 0.80)	| ||<input type="number" name="PPG" id="PPG" onchange="calculate()" placeholder="0.80" min="0" max="1" step="0.01" size="20" /> |
| | |||
|**Results**   | |||
|====
|Original Gravity   | ||<input type="number" name="OG" id="OG" readonly style="border:0"/> |
|Water for mash in quarts   | ||<input type="number" name="Water" id="Water" readonly style="border:0"/> |
|Strike Temperature in F   | ||<input type="number" name="Temp" id="Temp" readonly style="border:0" /> |
{: rules="groups"}

</form>




[^1]: [http://www.howtobrew.com/section2/chapter12-4-1.html](http://www.howtobrew.com/section2/chapter12-4-1.html)


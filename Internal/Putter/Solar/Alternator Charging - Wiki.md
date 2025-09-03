---
title: "electrical:12v:alternator [RVwiki for vanfolk and others who live in vehicles]"
source: "https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#combiners"
author:
published:
created: 2025-09-02
description:
tags:
  - "clippings"
---
electrical:12v:alternator

### −Table of Contents

[Words of Wisdom](https://rvwiki.mousetrap.net/doku.php?id=lifestyle:words_of_wisdom "lifestyle:words_of_wisdom"): With a isolator you would run the truck early to get a fair amount of the bulk charging done and let the solar finish it off the rest of the day. – jimindenver <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__1">1)</a></sup>

## Alternator charging

Note: this is a basic overview. More details available on the [alternator details](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator_details "electrical:12v:alternator_details") page.

## TLDR

Alternators can generate *massive* quantities of electricity when the engine is running, which can be used for charging house batteries. Their ability to generate large amounts of current makes alternators particularly good at charging deeply-discharged batteries (especially [lead chemistry](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:deep_cycle_battery "electrical:12v:deep_cycle_battery") batteries)

- In many situations, it is possible to use a simple/inexpensive battery [combiner](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#combiners "electrical:12v:alternator") or [isolator](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#proper_isolators "electrical:12v:alternator") between the house batteries and the vehicle battery. These will allow the house battery to charge when the vehicle is running, but will prevent the vehicle battery from being drained when the engine is off.
	- Some situations may benefit from or [require DC-DC chargers](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:mandatory_dcdc "electrical:12v:mandatory_dcdc") in between the vehicle batteries and the house batteries.
- charging is *triggered* by a 12v signal <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__2">2)</a></sup> and/or by voltage-sensing <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__3">3)</a></sup>
- Idling the engine while parked for long periods of time just to recharge the batteries is possible, but generally a bad idea.
	- Pulling a lot of power from the alternator causes it to generate a lot of heat. When the vehicle is moving there's enough airflow to keep the alternator cool, but when parked the heat will build up and can damage the alternator.
	- Long periods of idling is also not great for engines, *especially* [modern emission equipped diesels](https://rvwiki.mousetrap.net/doku.php?id=rv:diesel "rv:diesel").
- The amount of amps the alternator can provide depends heavily on the vehicle
	- While many vans have alternators rated at 150+ amps, at least half of that is typically needed just to run the vehicle's driving functions.
	- Some vans were offered with second alternators from the factory, which allow for charging your house batteries at *hundreds* of amps.
	- It's also possible to install aftermarket alternators, or to have the factory alternator replaced with a higher power one.
- Alternator charging *alone* is unlikely to keep [lead-chemistry](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:deep_cycle_battery "electrical:12v:deep_cycle_battery") batteries healthy, so [combining with solar](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alt_and_solar "electrical:12v:alt_and_solar") is common

[about these summaries](https://rvwiki.mousetrap.net/doku.php?id=opinion:frater_secessus:pareto "opinion:frater_secessus:pareto")

## overview

The vehicle's alternator is designed to turn some of the engine's mechanical power into electrical power in order to

1. recharge the vehicle's starter battery after starting the engine
2. run electrical accessories

### dual-battery systems

We can, [within limits](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#alternator_current_rating "electrical:12v:alternator"),<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__4">4)</a></sup> use this power to [charge](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:charging "electrical:12v:charging") our batteries or run our [electrical loads](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:loads "electrical:12v:loads"). This page is about how to do that with a dual-battery system (i.e. starter battery + house or aux battery).

In a dual-battery system <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__5">5)</a></sup> some of the alternator output is used to charge the house batteries when the engine is running. When the engine is not running **the house battery is electrically isolated** from the starter battery to keep from draining it and leaving you stranded. So the devices that handle the isolating/combining duties are sometimes called *battery isolators*.

The setup is typically:

```js
starter battery -> fuse -> wire -> isolator -> wire -> house battery
```

We might call them “isolators” generically but there are three kinds of devices used to charge from alternator:

- [combiner](https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#combiners "electrical:12v:alternator ↵") - which parallels the starter and battery bank together under certain conditions. Inexpensive, historically most common. Includes manual switches.
- [DC-DC charger](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") - includes electronics to adjust voltage and current. More expensive, increasingly common
- actual [isolators](https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#proper_isolators "electrical:12v:alternator ↵") - which split alternator power and distributes it separately to starter and house batteries.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__6">6)</a></sup> Uncommon these days, but could be useful in some scenarios where some amount of voltage and some current attenuation are desirable.

## when alternator charging works well

- when batteries are deeply discharged
- when [combined with solar](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alt_and_solar "electrical:12v:alt_and_solar") or some other higher-voltage charging source
- when used with battery chemistries like [lithium](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:deep_cycle_battery#lithium_chemistries "electrical:12v:deep_cycle_battery") that do not need [staged charging](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:charging "electrical:12v:charging").
- when used with a [battery-to-battery boosting charger](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") that can produce correct charging voltage for the battery chemistry

> The bottom line is that current simply flows where it is needed, batteries will take what they need when batteries are combined, and the voltage becomes equal among the new combined bank. Unless your charger, alternator or solar/wind system is pumping out an incorrect voltage for you bank you will not over charge using an ACR.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__7">7)</a></sup> mainesail <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__8">8)</a></sup>

## limitations

With lead chemistries, alternator charging by combiners is generally only practical for the [bulk charging](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:charging "electrical:12v:charging") stage due to relatively **low alternator voltage** and the [long time periods required for absorption](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:charging "electrical:12v:charging"); [DC-DC chargers](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") can help with the voltage can address the voltage issue. Failure to fully charge lead batts regularly <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__9">9)</a></sup> will impact [battery longevity](https://rvwiki.mousetrap.net/doku.php?id=electrical:batterycide "electrical:batterycide"). For this reason [some solar](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alt_and_solar "electrical:12v:alt_and_solar") is usually added to [the power mix](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:power_mix "electrical:12v:power_mix") for lead banks. In contrast, [Lithium can charge fine from alternator alone](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:mandatory_solar "electrical:12v:mandatory_solar"), if one drives enough to get sufficent charging.

Combiners are effectively a pass-through:

- they have **no way to limit current** other than hitting their max rating and failing or tripping.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__10">10)</a></sup> This might mean the battery can pull more current than is good for itself or for the alternator, necessitating the use of [a DC-DC charger](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b"). This typically is an issue only with oversized banks or small alternators.
- they **can't boost voltage** <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__11">11)</a></sup> like DC-DC. They are not “smart” and have no charging stages – the house bank will be charged at alternator voltage while the engine is running. Compare your alternator's voltage output to the battery manufacturer's Absorption charging voltage [setpoint](https://rvwiki.mousetrap.net/doku.php?id=electrical:solar:charge_controller_setpoints "electrical:solar:charge_controller_setpoints") before going this route.
- the charge acceptance rate (Amps) will decrease as bank voltage rises; this is called the *current taper*. Because of the taper if you want to get maximal harvest for your engine's gasoline consumption it would be better to charge when the bank is low than if the bank is nearly full.
- vehicles with *smart* (variable voltage) alternators are usually not suitable for charging with normal combiners.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__12">12)</a></sup> See [below](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#smart_alternators "electrical:12v:alternator")

## effect on alternator

{WARNING from secessus: [idling](https://rvwiki.mousetrap.net/doku.php?id=rv:idling#charging "rv:idling") to charge can cause alternator temperatures to spike, damaging the alternator or its diodes. So don't do that. }

Charging the house batteries from the alternator increases the load on the alternator and can be expected to contribute to somewhat earlier failure. In practice it's usually a non-issue if one avoids overheating <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__13">13)</a></sup> or overloading <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__14">14)</a></sup> the alternator; alternator failures from aux battery charging are quite rare.

> I have created hundreds of designs and installed around 100 systems, many with isolators or solenoids. In four plus years not one customer has come to me saying that their alternator failed. I do tell them not to sit in a hot parking lot idling their engine to charge their batteries. – jimindenver <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__15">15)</a></sup>

But see [this cautionary tale](https://www.reddit.com/r/vandwellers/comments/v5otsu/alternator_troubles_advice/ibevy8f/ "https://www.reddit.com/r/vandwellers/comments/v5otsu/alternator_troubles_advice/ibevy8f/") of using a 60A (!) [DC-DC charger](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") to charge 200Ah of AGM from a 145A alternator.

If/when the OEM alternator does fail <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__16">16)</a></sup> a higher output one can be installed for not much more than it would cost to replace the original.

### heat

Be aware of how heat affects the alternator and its health:

- alternators are about 50% efficient; making 400w of power means it's also making 400w of heat
- heat is hard on internal components; excess heat can cause derating or failure
- idling greatly reduces the ability of the alternator shed this heat
	- the alternator's own internal fan <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__17">17)</a></sup> is running slower
	- ambient temperatures under the hood are higher; there is no forward motion to introduce cooler air through the car's grille

If the bank is slurping a lot of current and you are stuck in traffic on a hot day it might be a good time to disable alternator charging (see below).

SternWake reports **idling while charging causes a sharp increase in alternator temperature**.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__18">18)</a></sup> To avoid this, do your alternator charging *while driving* so airflow over the hot alternator will help cool it. Other measures included additional alternator cooling or pulley size tuning to alternator RPM at idle.

See [this sub-article](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator_details#heat "electrical:12v:alternator_details") on alternators and heat

### alternator current rating

In general, vehicles with higher-rated alternators (150A, for example) will handle a given load better than vehicles with lower-rated alternators (60A, for example). The rating in Amps will be listed on the window sticker, often on the alternator housing itself, or can be looked up using a VIN decoder for your automaker.

see [this related article](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator_details#current "electrical:12v:alternator_details") on assessing how much current you can safely take from the alternator

### fuel consumption

Fuel consumption for power generation will be greatest when the vehicle is idled. When charging loads are imposed on a vehicle that is already driving the added cost can be minimal.

Using the 3.6L [Promaster](https://rvwiki.mousetrap.net/doku.php?id=rv:ram_promaster "rv:ram_promaster") with a 40A [DC-DC charger](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") as an example, ObvB estimates:

## charging current patterns

- charging lead chemistries directly from the alternator tends toward
	- **high initial inrush currents**
	- then a linear taper of current as the bank comes up to alternator voltage <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__20">20)</a></sup>
- charging lithium batteries directly from alternator tends toward
	- **high initial inrush currents** when SoC is low, then
	- middling and gradually-tapering currents across the middle 80%, then
	- very low currents as the bank approaches full charge <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__21">21)</a></sup>
- charging lead with [DC-DC](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") tends to be
	- rather flat at the charger's rating until
	- [Absorption voltage](https://rvwiki.mousetrap.net/doku.php?id=electrical:solar:charge_controller_setpoints "electrical:solar:charge_controller_setpoints") is achieved, at which point it begins a linear taper.
- charging lithium with [DC-DC](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") tends to be
	- rather flat and dictated by the charger's rating.
	- At the tail end of charging will taper off.

If the alternator is contributing 23A and you drive for 20 minutes you can expect to replace 7.67Ah on the drive.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__22">22)</a></sup>

`23A x 20 minutes / 60 minutes in an hour = 7.666666667Ah`

## paralleling different chemistries

It is often said that one cannot parallel batteries of different chemistries. This is not so. The problem would be keeping batteries with different resting voltages connected *after charging is removed*. If they were left connected the higher-voltage batt would discharge into the lower-voltage batt. Note: **an isolator setup is specifically designed to keep this from happening**.

As long as the alternator voltage is acceptable to both battery chemistries they can be paralleled during charging.

**Example** using a flooded starter battery, LiFePO4 house battery, relay, and 14.2v alternator:

- **charging**: both batteries will charge to 14.2v (given enough time)
- **no charging**: relay separates (“isolates”) the batteries. Starter batt rests at 12.7v and lithium at 13.5v.

## alternator voltage

Traditional alternators typically try to hold a consistent voltage. The exact voltage being held might vary but it's relatively stable:

> > most alternators with internal regulators are designed with a voltage *turn-down* with temperature. Because the battery is often under the hood, it gets hot from the engine and needs a lower charging voltage to remain healthy. Typically a 14.4V regulator target will drop to a 13.8V regulator target by the time the alternator gets to 140F. – MechEngrSGH <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__23">23)</a></sup>

While this is not intended to be protection from overheating due to high current production, lowering the output voltage will indirectly reduce current when charging by relay/isolator. Example: a setup with accepting 85A @ 14.4v would only accept 65A @ 13.8v.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__24">24)</a></sup>

### smart alternators

*Smart alternators* on the other hand talk to the vehicle's ECU (computer) and **can vary output voltage wildly moment by moment** depending on present conditions. It might unload the alternator during heavy acceleration to reduce parasitic losses, or run the alternator at high voltage just after starting to speed up the recovery of used energy.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__25">25)</a></sup>

When the smart alt goes low voltage the normal relationship between the two systems (higher-voltage chassis charging lower-voltage house battery) is disrupted. It can result in rapid ON/OFF cycling of the isolator ([voltage sensing](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#voltage-sensing_relays "electrical:12v:alternator") types) or the discharge of the house battery into the starter battery ([solenoid](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#constant-duty_solenoid "electrical:12v:alternator") type triggered by D+).

> > There are several methods of identifying a smart alternator… the most conclusive is the existence of a current sensor on the negative battery cable. It is often a small box with 2 or 3 wires placed right at the battery terminal. In some cases (GM mostly) it may be 6-8“ down the cable from the battery. – MechEngrSGH <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__26">26)</a></sup>

#### solutions

- the usual solution is to use a [DC-DC charger](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") with an awareness of smart alternators.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__27">27)</a></sup> The DC-DC is already upconverting chassis voltage to house battery charging voltage, and does not mind unusual source voltages from the alternator.
- Some smart alternators can have the “smarts” disabled or tricked into producing higher voltage; this depends on the alternator/vehicle.
- in extreme situations the OEM alternator might be replaced with a traditional one, or a dual alternator setup (one smart, one traditional) might be engineered

#### further reading on smart alternators

- Redarc - [standard vs smart alternators](https://www.redarc.com.au/alternator-vs-fixed-alternator "https://www.redarc.com.au/alternator-vs-fixed-alternator")

## combiners

“Split charge relay (SCR)”, “split charger”, “automatic charge relay (ACR)”, “Voltage sensing relay (VSR)”, solenoid, relay, etc.

Power from the alternator is shared with the house battery by paralleling the two sets of batteries at certain times. This allows the [house battery](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:intro "electrical:12v:intro") to charge but does not allow the house battery to pull power from the starter battery when not combined. [This short video](https://www.youtube.com/shorts/nHS7aJuJd6c "https://www.youtube.com/shorts/nHS7aJuJd6c") illustrates how it works.

### continuous-duty solenoid

[![m.media-amazon.com_images_i_41zfkq0puil._ac_uy218_ml3_.jpg](https://rvwiki.mousetrap.net/lib/exe/fetch.php?w=75&tok=2b6e38&media=https%3A%2F%2Fm.media-amazon.com%2Fimages%2FI%2F41zFkQ0pUIL._AC_UY218_ML3_.jpg "m.media-amazon.com_images_i_41zfkq0puil._ac_uy218_ml3_.jpg")](https://amzn.to/2RgAFUw "https://amzn.to/2RgAFUw") A [continuous-duty solenoid](http://amzn.to/2fZCfEr "http://amzn.to/2fZCfEr") is an electromechanical device which uses an electromagnet to complete the charging circuit when the engine is running. The basic idea is the relay uses a low-current circuit <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__28">28)</a></sup> to activate a higher-current circuit.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__29">29)</a></sup>

**Solenoids are generally cylindrical**. Energizing the solenoid will cause a **0.5A - 1A current drop** between the alternator and house battery. Exception: [Latching isolators](https://amzn.to/3egI27C "https://amzn.to/3egI27C") use latches <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__30">30)</a></sup> instead of electromagnets to hold the circuit closed, eliminating that vector of power consumption.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__31">31)</a></sup> and therefore heat. SternWake recommends the [Blue Sea 9012](http://amzn.to/2fZLFzs "http://amzn.to/2fZLFzs") <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__32">32)</a></sup> although [non-marine units in the $20-$50 range](https://amzn.to/2NLVwg0 "https://amzn.to/2NLVwg0") are more common in vans.  
Solenoids can be used for [self-jumpstarting](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:self-jumpstarting "electrical:12v:self-jumpstarting") *if* the chassis battery has enough juice to engage the solenoid.

See [this video](https://www.youtube.com/watch?v=qsBXinpuwDA "https://www.youtube.com/watch?v=qsBXinpuwDA") that shows the theory and practice of how these relays work.

Note: some solenoids only have three terminals: 2 big load terminals and 1 small control terminal. This type gets the “ground” <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__33">33)</a></sup> through the body of the solenoid. The pic above is of a “three post” solenoid – the case is grounded to the chassis through the metal feet.

#### starter relays vs continuous duty relays

While they may be externally identical, starter relays and continuous duty relays are built differently inside.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__34">34)</a></sup>

The **starter relay** needs to switch huge currents for brief amounts of time. The switching has to be very fast and powerful to minimize arcing. To achieve this the solenoid will pull several amps to run a powerful electromagnet. The solenoid will not overheat because it is only “on” for a few moments. The control terminals typically have resistance of 3-4 ohms.

The **continuous duty relay** is used for much longer periods of time and is rated for less current. The lower current means the connection doesn't have to be slammed closed as fast with a powerful electromagnet. As a result this relay type typically draws <1A and the control terminals have resistance of 15-30 ohms.

Note that per Cole-Hersee even a CD relay will get hot:

> > The coil circuit (control circuit) in a continuous duty solenoid is usually energized for long periods of time. Under these conditions the coil will generate heat and within less than an hour the solenoid housing will become hot to the touch. This is normal. Always make sure that all wiring is properly sized for the load it is carrying, that the terminals are the correct size and have been securely crimped to the wire, that the terminals have the proper torque to the solenoid studs.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__35">35)</a></sup>

##### orientation

Cole-Hersee [recommends](https://www.littelfuse.com/technical-resources/technical-centers/commercial-vehicle-technical-center/frequently-asked-questions.aspx?utm_source=colehersee.com&utm_medium=redirect&utm_campaign=colehersee-lf#question_38 "https://www.littelfuse.com/technical-resources/technical-centers/commercial-vehicle-technical-center/frequently-asked-questions.aspx?utm_source=colehersee.com&utm_medium=redirect&utm_campaign=colehersee-lf#question_38") mounting relays with the dimple facing downward:

### voltage-sensing relays

[![](https://rvwiki.mousetrap.net/lib/exe/fetch.php?tok=54b5ad&media=https%3A%2F%2Fimages-na.ssl-images-amazon.com%2Fimages%2FI%2F418qcncjT0L._AC_US218_.jpg)](https://amzn.to/2Ri2jQV "https://amzn.to/2Ri2jQV") voltage sensing relays (VSR, also called Automatic Charging Relays or ACR) are combiners with a bit of extra logic to know when to connect/disconnect. The VSR does not get trigger voltage from the fuse panel but rather reads the voltages of one <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__36">36)</a></sup> or both <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__37">37)</a></sup> batteries to know when to switch on.  
This kind of isolator may have a “combine” override function to enable [self-jumpstarting](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:self-jumpstarting "electrical:12v:self-jumpstarting").

> in its simplest form, all an ACR really does is parallel batteries when charging is present and un-parallel batteries when there is no charging present. It does this automatically with no human forgetfulness.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__38">38)</a></sup>

#### starter battery priority

Some VSR have a feature where they delay the connection a few seconds until the starter battery has recovered a bit from starting the engine. Often misunderstood as “charging house batteries after the starter battery is *fully charged* ”, the typical criterion is chassis voltage of ≥13.4v. Contrary to common belief the starter battery is not *fully charged* at that point but the current inrush to it has settled down enough that the alternator can do other things.

#### examples

1. [single voltage sensing](http://amzn.to/2h2tDxp "http://amzn.to/2h2tDxp") - this type reads the voltage of only one battery. In the case of an RV it would read the voltage of the starting battery. When it is high enough above resting voltage (ie, being charged by alternator) it connects the starting and house batteries.  
	\[secessus says: “ IMO the practical benefit (if any) to charging the starter battery “first” is keeping the load on the alternator reasonable. In practice, the isolator generally connects the two within a few seconds.”\]  
	Examples:
	- [Sure Power 1314](http://amzn.to/2h2tDxp "http://amzn.to/2h2tDxp") - Connect >13.2v, disconnect 12.9v <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__39">39)</a></sup>,<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__40">40)</a></sup> Automatic [self-jumpstarting](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:self-jumpstarting "electrical:12v:self-jumpstarting") when aux bank voltage > starter batt voltage.
	- [Battery Doctor](https://amzn.to/2Ri2jQV "https://amzn.to/2Ri2jQV") - connect >13.4v, disconnect <12.8v.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__41">41)</a></sup>
	- ["Smart Battery Isolator"](https://amzn.to/3p6F7s7 "https://amzn.to/3p6F7s7") and [many similar models](https://amzn.to/41huZtY "https://amzn.to/41huZtY")
2. [dual voltage sensing](http://amzn.to/2gVmLFU "http://amzn.to/2gVmLFU") - this type reads the voltage from *both* sides and when either is high enough it connects the batteries. This may or [may not be what an RVer wants](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator_charging_hvd "electrical:12v:alternator_charging_hvd")  
	Examples:
	- [Victron Cyrix-ct](https://amzn.to/3h5iMUd "https://amzn.to/3h5iMUd") - connect >13.0v <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__42">42)</a></sup>, disconnect <12.8v <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__43">43)</a></sup>,<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__44">44)</a></sup>
	- [Sure Power 1315](http://amzn.to/2gVmLFU "http://amzn.to/2gVmLFU")
	- Blue Sea - unless otherwise noted, these ACR combine at 13.0v after 120 seconds or 13.6v after 30 seconds. Disconnect at 12.75v after 30 seconds.
		- [M-ACR 7601](https://amzn.to/3UC8GvX "https://amzn.to/3UC8GvX") - **65A**. [manual](https://d2pyqm2yd3fw2i.cloudfront.net/files/resources/instructions/980014350.pdf "https://d2pyqm2yd3fw2i.cloudfront.net/files/resources/instructions/980014350.pdf")
		- [BlueSea BatteryLink 7611](https://amzn.to/2tEGp1e "https://amzn.to/2tEGp1e") - **120A**. Connect 13.0v <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__46">46)</a></sup>, disconnect 12.75v <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__47">47)</a></sup>. If “auxiliary battery priority” is triggered the cut-out voltage drops to 12.25v. This can be triggered by D+ so it's only active when the engine is running. It can also be always-on from 12v, in effect acting like [an LVD](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:lvd "electrical:12v:lvd"). [manual](https://image.fisheriessupply.com/f_jpg/f_auto/t_Legacy-750x750/v1/static-images/b-s7611InstallManual.pdf "https://image.fisheriessupply.com/f_jpg/f_auto/t_Legacy-750x750/v1/static-images/b-s7611InstallManual.pdf")
		- [BlueSea ML-ACR 7620](https://amzn.to/3yR2bhA "https://amzn.to/3yR2bhA") - **500A**. This is a latching relay which allows the solenoid to de-energize after changing state. This minimizing parasitic losses <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__48">48)</a></sup> and heat. The ML has Starter Isolation as described on the SI-ACR. Allows [self-jumpstarting](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:self-jumpstarting "electrical:12v:self-jumpstarting"). Cut in and cut out voltages are slightly different; see [the manual](https://image.fisheriessupply.com/f_jpg/f_auto/t_Legacy-750x750/v1/static-images/b-s7611InstallManual.pdf "https://image.fisheriessupply.com/f_jpg/f_auto/t_Legacy-750x750/v1/static-images/b-s7611InstallManual.pdf").
		- [BlueSea ML-ACR w/manual controll 7622](https://amzn.to/3FgFggW "https://amzn.to/3FgFggW") - **500A**. Version of the ML-ACR above with a manual control knob <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__49">49)</a></sup> to override isolation or combination if desired.
	- [JayCorp Smart Dual Battery 140A Isolator](https://amzn.to/2RFaXI7 "https://amzn.to/2RFaXI7") <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__50">50)</a></sup>
	- Precision Circuits [BIM](https://www.precisioncircuitsinc.com/product/battery-isolation-manager/ "https://www.precisioncircuitsinc.com/product/battery-isolation-manager/"). Latching relays in **160A** and **225A** versions.. Disconnects after 1 hour max to prevent overcharging: “The BIM does not guarantee 100% battery charge, but prevents harmful battery charge levels.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__51">51)</a></sup> *Sig* terminal can use used for [self-jumpstarting](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:self-jumpstarting "electrical:12v:self-jumpstarting").  
		Also see Li-BIM below.
3. DC-DC isolators (aka *[b2b](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") isolators*) that boost alternator voltage to [more appropriate levels for lead chemistries](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:charging "electrical:12v:charging") and can do multistage charging. These have [their own page](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b").

Note: [voltages-sensing (with or without delay)](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:voltage_sensing_delay "electrical:12v:voltage_sensing_delay") can be added to plain solenoids.

### lithium-specific VSR

A “lithium compatible” VSR has a higher voltage setpoint for disconnecting the batteries *after charging stops*; the charging function is no different.

Reasoning: A traditional VSR might disconnect at ≤12.9v, since that is slightly above resting voltage for a lead-chemistry battery. (When it sees ≤12.9v it knows charging must have stopped and the batts should be disconnected from each other) **Fully-charged LiFePO4 rests at higher voltage** so the voltage at which the VSR disconnects needs to be higher. If it waited for 12.9v the batteries would get “stuck” together longer than appropriate. In effect the lithium batt would prop up the lead starter batt (and parasitic chassis loads) until the LFP were substantially discharged. So a “lithium compatible” VSR disconnects at something like 13.2v - 13.4v.

Note: a normal VSR can be used with LiFePO4; it may be useful to add a way to [disable temporarily](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#disabling_alternator_charging "electrical:12v:alternator") it to break the “stuckness”. Also see [the Gotchas section](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#gotchas "electrical:12v:alternator") for related information.

#### Li-BIM

[![m.media-amazon.com_images_i_41d3iimvdjl._ac_ul320_.jpg](https://rvwiki.mousetrap.net/lib/exe/fetch.php?w=100&tok=7fc11e&media=https%3A%2F%2Fm.media-amazon.com%2Fimages%2FI%2F41d3IImVdJL._AC_UL320_.jpg "m.media-amazon.com_images_i_41d3iimvdjl._ac_ul320_.jpg")](https://amzn.to/3c6XwMv "https://amzn.to/3c6XwMv") The [Precision Circuits Li-BIM](https://amzn.to/3c6XwMv "https://amzn.to/3c6XwMv") is a lithium-specific [dVSR isolator](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#voltage-sensing_relays "electrical:12v:alternator") with some differences:

1. the VSR circuit disconnects at 13.4v when there is no charging occuring on the alternator side. See section above for more info on why this feature is present.
2. the isolator opens the circuit (disconnects) regularly to allow alternator cooling. Charge for 15 minutes, disconnect for 20 minutes, repeat. So the BIM is charging ~43% of total runtime.
3. the isolator disconnects when it detects >= 14.4v on the alternator side, to avoid overcharging

The unit supports [self-jumpstarting](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:self-jumpstarting "electrical:12v:self-jumpstarting") but a switch must be installed by the user. 160A and 225A models are available. BB suggests the BIM is recommended for lithium banks >= 300Ah.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__52">52)</a></sup>

An interesting teardown of the Li-BIM can be seen in [this video](https://www.youtube.com/watch?v=pFd9Uulo9rY "https://www.youtube.com/watch?v=pFd9Uulo9rY").

#### True Amalgamated Lithium VSR

True [makes a VSR](https://www.trueam.com/product/true-lithium-large-dual-battery-kit/ "https://www.trueam.com/product/true-lithium-large-dual-battery-kit/") with 13.5v ON and 13.2v OFF setpoints.

### manual switch

[![m.media-amazon.com_images_i_81n-ap_0lpl._ac_uy218_.jpg](https://rvwiki.mousetrap.net/lib/exe/fetch.php?w=125&tok=9e7d47&media=https%3A%2F%2Fm.media-amazon.com%2Fimages%2FI%2F81n-ap%2B0lPL._AC_UY218_.jpg "m.media-amazon.com_images_i_81n-ap_0lpl._ac_uy218_.jpg")](https://amzn.to/2VaL8SG "https://amzn.to/2VaL8SG") The simplest and least-featured isolator is a *manual switch*.

A [manual battery switch](http://amzn.to/2gsDtNc "http://amzn.to/2gsDtNc") normally has 4 positions: A, B, A+B, and Off. A would be for the starter battery and used during starting. B would be used for house use when one is not driving. A+B could be used to combine both sets for starting or for charging while driving. This kind of setup is prone to user error. A manual switch has no current or voltage losses.

## RV-specific combiners

> > All late model Essex and King Aire’s use Silverleaf systems with the White Rodgers Solenoid. In 2014, the Mountain Aire will also be using Silverleaf. It is a computerized system that controls all aspects of charging. All late model Mountain Aire and Dutch Star Diesel Pushers use the Battery Isolation Manager (BIM). This is an all in one system that is made by Precision Circuits. Class A models before 2010 use the Bidirectional Isolator Relay Delay (BIRD) with a solenoid. The Bay Star Sport has a manual switch to disconnect power, which is located in the overhead above the entry door. This is similar to the ones in the fifth-wheels. All others have a single lighted switch that is in the front overhead to turn off house voltage.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__53">53)</a></sup>

also see [DUVAC](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator_details#duvac "electrical:12v:alternator_details")

### BIRD

Some RVs came with “BIRD” <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__54">54)</a></sup> controllers that drove the constant duty relay.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__55">55)</a></sup> These controllers from Intellictec combine when either side is >13.xv, depending on model/vintage.

- the *delay* in the name is a 2.5 minute delay after the chassis voltage reaches the setpoint. “This delay allows a cold engine an opportunity to start and warm up before having the heavy load of a discharged coach battery placed

on it.”

- BIRDs with GEN terminals may disable chassis battery charging when the generator is operating.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__56">56)</a></sup>
- BIRDs with AUX terminal will override and close the relay regardless of voltage conditions. This could be useful for [self-jumpstarting](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:self-jumpstarting "electrical:12v:self-jumpstarting").

The functionality of the RV-specific BIRD is largely supplanted by dVSR (see above). In some cases RV manufacturers have moved to the BIM (see above).<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__57">57)</a></sup>

### BIC

Intellitec also made a Battery Isolation Controller, which drives the relay based on chassis voltage.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__58">58)</a></sup> It also has manual override for self-jumpstarting.

The functionality of the RV-specific BIC is largely supplanted by a VSR (see above).

### Silverleaf

Silverleaf is a CAN-based system for controlling various functions, including charging relays. [Technical reference](https://www.silverleafelectronics.com/wp-content/uploads/2021/10/Silverleaf-Technical-Reference.pdf "https://www.silverleafelectronics.com/wp-content/uploads/2021/10/Silverleaf-Technical-Reference.pdf") (pdf)

## proper isolators

### solid state isolator: diode-based

[![m.media-amazon.com_images_i_81on3erszsl._ac_uy218_.jpg](https://rvwiki.mousetrap.net/lib/exe/fetch.php?w=125&tok=b7383e&media=https%3A%2F%2Fm.media-amazon.com%2Fimages%2FI%2F81on3erSzsL._AC_UY218_.jpg "m.media-amazon.com_images_i_81on3erszsl._ac_uy218_.jpg")](https://rvwiki.mousetrap.net/lib/exe/fetch.php?tok=3fe312&media=https%3A%2F%2Fm.media-amazon.com%2Fimages%2FI%2F81on3erSzsL._AC_UY218_.jpg "https://m.media-amazon.com/images/I/81on3erSzsL._AC_UY218_.jpg")

Note: this type of isolator was common in the 80s and 90s. It is no longer common for our uses for several reasons. Nevertheless they might be useful in some setups where bidirectional charging <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__59">59)</a></sup> is undesirable, or where alternator voltage is excessively high for house the battery chemistry.

These are proper “isolators” and **never parallel the starter and house batteries**. The isolator is effectively a Y connection *installed between the alternator and starter battery*.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__60">60)</a></sup> It receives power from the alternator and distributes it separately to the starter battery and house battery. The isolator's Amp rating is the maximum input from the alternator.

[These isolators](http://amzn.to/2gVwmKw "http://amzn.to/2gVwmKw") are electronic devices which use diodes to prevent backflow from either battery. **Isolators are generally brick-shaped**. Silicon diode isolators typically have a **0.7v voltage drop** (“forward voltage drop”) between the alternator and house battery when running near rated capacity.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__61">61)</a></sup> This may be desirable if the house battery is a wants lower-voltage charging like [LiFePO4](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:lifepo4_batteries_thread "electrical:12v:lifepo4_batteries_thread").<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__62">62)</a></sup> The slightly-lower voltage will also [reduce charging current somewhat](https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#effect_of_isolator_type_on_charge_rates "electrical:12v:alternator ↵").

Notes:

- solid state relays typically can't combine batteries for [self-jumpstarting](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:self-jumpstarting "electrical:12v:self-jumpstarting")
- the unidirectional nature of the diode isolator may be desirable to prevent “backflow” of higher voltage from the house bank to the chassis.
- diode-based isolators are typically installed *between* the alternator and starter battery. This is in contrast to solenoids and VSRs which can be daisy-chained off the starter battery. The batteries are, in effect, always isolated and never electrically combined.
- some diode-based isolators (Victron, see above) have a feature to slightly tweak alternator voltage upwards to compensate for voltage drop across the isolator. Note that this increases alternator voltage everywhere, not just after the isolator.
- isolators cannot be [disabled the way DC-DC and relays can](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#disabling_alternator_charging "electrical:12v:alternator").
- see info on alternator self-excitation below

#### three+ pin examples

These mount between the alternator and the target batteries.

- [Cole-Hersee 48161](https://amzn.to/3T7bqSd "https://amzn.to/3T7bqSd"), 250A.
- [Cole-Hersee 48162](https://amzn.to/3pAFfNy "https://amzn.to/3pAFfNy"), 250A. With exciter.
- [Cole-Hersee 48122](https://amzn.to/3h8cXFw "https://amzn.to/3h8cXFw"), 140A. With exciter.
- The [Victron Argo-diode](https://amzn.to/3jbCNuT "https://amzn.to/3jbCNuT"), 200A, claims to use **Schottky diodes** instead of silicon diodes so that “voltage drop is approximately 0.3V and at the rated output approximately 0.45V”.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__63">63)</a></sup> With exciter and built-in voltage-sensing diode function. Schottkys are prone to heating up at high current <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__64">64)</a></sup> so proper mounting with airflow may be critical.

#### two-pin examples

[![m.media-amazon.com_images_i_314v99tptsl._ac_ul400_.jpg](https://rvwiki.mousetrap.net/lib/exe/fetch.php?w=125&tok=0db04e&media=https%3A%2F%2Fm.media-amazon.com%2Fimages%2FI%2F314V99TPtsL._AC_UL400_.jpg "m.media-amazon.com_images_i_314v99tptsl._ac_ul400_.jpg")](https://amzn.to/3YzMXZa "https://amzn.to/3YzMXZa") Instead of mounting between alternator and battery it goes between the power source (battery, alternator, etc) and the house battery like a combiner.

When daisy chained with a relay we get the unidirectionality of an isolator without rewiring, alternator-excitation issues, etc, mentioned elsewhere in this article.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__65">65)</a></sup>

- [Cole-Hersee 48051](https://amzn.to/3YzMXZa "https://amzn.to/3YzMXZa")

### solid state isolator: FET-based

This type of isolator is similar to the diode-based one above, except that FET components are used instead of diodes, minimizing voltage drop and allowing two-way power if designed to do so. They tend to cost 2x as much as the diode versions.

#### three+ pin examples

- [Victron Argo 200A FET Battery Isolator](https://amzn.to/2Cwjkln "https://amzn.to/2Cwjkln")
- the [Ctek SmartPass](https://amzn.to/2TozjWu "https://amzn.to/2TozjWu").<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__66">66)</a></sup> is a MOSFET-based isolator with additional features/logic:
	- Connect at >13.1v, disconnect at 12.8v, or 11.8v / 11.4v with smart alternators.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__67">67)</a></sup>
	- Battery overtemp protection at 140F.
	- Starter assist when starter batt voltage ~6v.
	- Will trickle charger starter batt when house battery is charging from other means.
	- See [this article](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:diysmartpass "electrical:12v:diysmartpass") about DIYing a similar solution.

#### two-pin examples

- [Perfect Switch](https://perfectswitch.com/isolators/single-rectifier-isolator-gen4-0/ "https://perfectswitch.com/isolators/single-rectifier-isolator-gen4-0/"), 100A-600A. Presumed to be FET-based since forward-voltage drop is given as 30mV.

### misc

\[note from secessus: “not sure what's inside these solid state isolators”\]

[![m.media-amazon.com_images_i_51xoshk5uil._ac_uy218_.jpg](https://rvwiki.mousetrap.net/lib/exe/fetch.php?w=125&tok=6fe999&media=https%3A%2F%2Fm.media-amazon.com%2Fimages%2FI%2F51XoShK5uIL._AC_UY218_.jpg "m.media-amazon.com_images_i_51xoshk5uil._ac_uy218_.jpg")](https://amzn.to/3fVuKh0 "https://amzn.to/3fVuKh0") The [Magnum Energy ME-SBC](https://amzn.to/3fVuKh0 "https://amzn.to/3fVuKh0") is notable for some unusual features:

- configurable connect/disconnect setpoints
- ability to drive a solenoid, which allows for much greater current

Xantrex makes [a 15A Digital-Echo Charge isolator](https://amzn.to/3eKhkEc "https://amzn.to/3eKhkEc").

The [Mastervolt Charge Mate Pro 90](https://amzn.to/2P9uxyG "https://amzn.to/2P9uxyG") is an electronic current-limiting isolator.

### self-exciting alternators and isolators

All alternators <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__68">68)</a></sup> need to be able to sense battery voltage to regulate their output. This was traditionally done with a separate voltage sense wire.

“1-wire self- [exciting](https://alternatorparts.com/what-is-a-self-exciting-alternator.html "https://alternatorparts.com/what-is-a-self-exciting-alternator.html") ” alternators <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__69">69)</a></sup> do not have a sense wire and rely on the output wire from the alternator (“B+”) to the starter battery. This is normally not an issue since the battery and alternator are wired to each other.

However when a diode- or FET-based isolator is inserted between them the alternator's B+ can no longer sense the battery voltage; the isolator is one-way by design. The solution is to provide a small amount of current from the starter battery to the isolator's common input terminal where the B+ can sense it. Because this “leak” violates the isolator's one-way principle it should only occur when the vehicle is on.

So a D+ (IGNition) signal is provided to so-equipped isolators on additional “alternator excite” stud <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__70">70)</a></sup>, which triggers the leak from starter battery to common INPUT.

\[note from secessus: it's not clear if the leak is momentary or if there is a diode on the leak circuit to prevent charging from flowing down this tiny circuit. [Some manufacturers](https://perfectswitch.com/support/optional-excitation-circuit/ "https://perfectswitch.com/support/optional-excitation-circuit/") suggesting getting the 12v signal from the starter relay so it is momentary.\]

Per Littelfuse (maker of Cole-Hersee isolators):

> > Most alternators on new vehicles have an integral electronic voltage regulator that requires the use of the 4-stud battery isolator. The small 4th stud is for connection to a circuit switched by the ignition switch… A 4-stud battery isolator can be used with older pattern alternators (in this case the 4th stud will remain unconnected), but a 3-stud battery isolator cannot be used with the Delcotron-type alternator.

Yet another explanation, this time [from Victron](https://www.victronenergy.com/upload/documents/Manual-Argodiode-Battery-Isolators-EN-NL-FR-DE-IT-ES-SE-TR.pdf "https://www.victronenergy.com/upload/documents/Manual-Argodiode-Battery-Isolators-EN-NL-FR-DE-IT-ES-SE-TR.pdf"):

> > The new Argodiode isolators have a special current limited energize input that will power the B+ when the engine run/stop switch is closed.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__71">71)</a></sup>

### effect of isolator type on charge rates

Because I=V/R we can compare how different “forward voltage drops” affect charging. Assuming 20mR resistance as a baseline, 14.4v alternator output and 12.1v bank voltage:

- direct charging (0v loss) would be ~115A
- charging with FET-based isolator (0.3v loss) would be ~100A
- charging with Schottky diode isolator like ArgoDiode (0.45v loss) would be ~92.5A
- charging with normal diode isolator (0.7v loss) would be 80A

These are relative numbers, not intended to predict actual charge rates.

.

## how to choose

For many <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__72">72)</a></sup> use cases a plain **constant-duty solenoid** triggered by an ignition circuit will augment aux battery charging nicely. It can deliver large amounts of current when battery [state of charge](https://rvwiki.mousetrap.net/doku.php?id=electrical:depth_of_discharge "electrical:depth_of_discharge") is low, and is quite inexpensive. The wiring might cost more than the solenoid.

When access to an ignition circuit is impractical, a **voltage sensing relay** will do the job, no external trigger required.

In some cases [a DC-DC charger](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") is **preferable or mandatory**:

- when using alternator as the sole form of charging lead chemistries
- when the vehicle has a “smart” alternator <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__73">73)</a></sup>
- when using an alternator to charge large aux battery banks that may strain the alternator
- when alternator and aux battery bank voltage are different (12v alternator and 24v bank, for example)

A diode-based isolator may be preferable in niche cases.

See also [the effect of alternator charging method on current](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator_details#effect_of_alternator_charging_method_on_current "electrical:12v:alternator_details")

See [the gotcha section](https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#gotchas "electrical:12v:alternator ↵") below to see if there are hidden traps in your intended use case.

## sizing an isolator

If an isolator is **oversized** it will cost more for no benefit, will self-consume somewhat more energy to hold the combining circuit closed,<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__74">74)</a></sup> and may take more physical space.  
If an isolator is **undersized** (less common) it will not be able to carry enough current, resulting in overheating and/or [sudden shutdown](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#sudden_disconnection "electrical:12v:alternator").

Most AGM will pull about C/3 when deeply discharged (33A for a 100Ah bank) but premium brands may do more. Flooded lead-acid batteries tend to pull less current (C/5, 20A per 100Ah of bank). If your flooded back will only pull ~40A, or your AGM bank 70A then there is little reason to spend more money on a 150-200A isolator.

Lithium in particular has low internal resistance and *can* pull [1C](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:battery_capacity "electrical:12v:battery_capacity") (100A for an 100Ah bank) or more. [In practice](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:directcharginglfp#actual_reports "electrical:12v:directcharginglfp"), they tend to pull about the same as AGM.

Since lithium does not care much about [state of charge](https://rvwiki.mousetrap.net/doku.php?id=electrical:depth_of_discharge "electrical:depth_of_discharge"), **there is little reason to go for maximum force lithium charging**. Some Li bank owners use [DC-DC isolators](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") which limit themselves to a particular output (20A, 60A, 100A, etc).<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__75">75)</a></sup>

Reasonable charging rates can also be easier on the alternator when charging suddenly stops, whether by completion <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__76">76)</a></sup> or BMS intervention. Blue Sea makes an [alternator field disconnect](https://www.bluesea.com/resources/91 "https://www.bluesea.com/resources/91") which shuts down alternator power just before disconnecting the load, but this may be chiefly applicable to marine alternators. Others have discussed installing a small lead-acid battery parallel to the Li bank; in theory this could soften the blow from Li leaving the circuit. Other sources suggest the presence of the starter battery would be sufficient.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__77">77)</a></sup>

### harvest

Ah = Amps x hours. If your combiner averages 30A and you drive for 1.5 hours it can replace 45Ah (30A x 1.5 hours).

Note: the current produced by direct charging vs DC-DC charging is different.

- direct charging results in *tapering* charge current, decreasing as battery bank voltage / SoC increases.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__78">78)</a></sup>. So over an hour the current might go from 30A to 10A, an average of 20A. 20A x 1 hour = **20Ah replaced**. Pro: your bank gets more charging when it needs it most. Con: charge rates are less predictable until you learn how your system works.
- [DC-DC charging](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") generally make its rated output (20A, for example) for the majority of the charging cycle. Pro: highly predictable charging (20A x 1 hour = **20Ah replaced**). Con: charging current is the ~same regardless of bank SoC
- in this artificial example both charging setups will replace 20Ah in an hour of charging but they do it differently. In reality which charges “better” depends on your specific use case, bank chemistry & capacity, alternator voltage and rating, DC-DC rating, etc. Do your research and pick your poison.

### flooded lead-acid

FLA batteries can accept up to [C](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:battery_capacity "electrical:12v:battery_capacity") /5 in [Bulk stage](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:charging "electrical:12v:charging").

Example: a 200Ah FLA battery bank will pull up to 40A <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__79">79)</a></sup> in Bulk charging. An isolator rated for constant duty at 40A <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__80">80)</a></sup> would be sufficient.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__81">81)</a></sup>

### AGM lead-acid

Consumer-grade AGM batteries typically will accept C/5 - C/3.

Example: a 200Ah AGM bank will pull up to 67A in Bulk. A 75A isolator <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__82">82)</a></sup> would be sufficient.

Note: high-end AGM like Lifeline, Odyssey, Rolls, etc, can pull massive current when charging. 200A+ would be possible for the example bank and could shorten the life of a stock alternator.

### lithium

Lithium has the potential to accept massive amounts of charging, up to 1.0C. All other things being equal, [heaviest current will be pulled when battery bank voltage is the lowest](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:directcharginglfp#the_formula_in_60_seconds "electrical:12v:directcharginglfp").<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__83">83)</a></sup>

There are mitigating factors that tend to reduce current in real world use:

- resistance in the charging path often [limits lithium charging current to ~0.5C](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:directcharginglfp "electrical:12v:directcharginglfp").
- Because lithium can use about 80% of it's capacity instead of 50% for lead-acid if one is upgrading to a LiFePO4 bank with *the same usable Ah* the Li bank will be ~0.6 the rated capacity of the lead it replaces.
- Li voltage remains in the thirteens for most of its usable capacity, reducing the voltage delta mentioned above.

#### sudden disconnection

Note: this is an issue for rigs with **secondary alternators dedicated to charging a battery bank**. In normal <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__84">84)</a></sup> setups the vehicle's starter battery acts as a buffer to cushion sudden disconnects.

**Sudden disconnection of a large load <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__85">85)</a></sup> when the alternator is making substatial power** can damage the alternator and chassis electronics. Sudden disconnection can occur when:

- an isolator shuts off for whatever reason
- a BMS shuts off lithium charging. This can include overvoltage, overcurrent, temperature extremes, etc.

## externally-regulated alternators

It's more common in marine setups than vehicles, but external regulators can be used to trick the alternator into outputting specific non-OEM voltages <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__86">86)</a></sup>. [Balmar](https://balmar.net/ "https://balmar.net/") appears to be the industry leader in external regulation.

Note that while your battery bank might like higher voltages the vehicle chassis may not.

## secondary alternators

In RVs with heavy electrical consumption a secondary alternator may be installed for aux power and charging. It runs off the engine and effectively replaces the [generator](https://rvwiki.mousetrap.net/doku.php?id=electrical:generator "electrical:generator"); some systems will auto-start the engine similar to how gens can auto-start. The secondary alt is typically rated for heavier current and/or externally-regulated (see above). It may be run off a smaller pulley that increases alternator RPM at idle for more power and/or cooling.

Challenges include hefty cost, already-cramped space in van engine bays, mechanic unfamiliarity with non-OEM systems, and potentially-increased time running the engine.

## gotchas

The average user will likely not notice these effects; some of them rather subtle.

- Solar charging while the isolator circuit is closed (ie, batteries connected) can pass higher-than-normal voltage to the chassis and starter battery. Workaround: see notes on HVD and DC-DC charging below.
- LiFePO4 resting voltages are high enough they may hold the circuit closed on VSRs designed for lead chemistries. Workarounds:
	- [disable alternator charging](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#disabling_alternator_charging "electrical:12v:alternator") (at least momentarily) after driving
	- use a relay [triggered by D+](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#triggering "electrical:12v:alternator")
	- use a relay like [the Li-Bim](https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#li-bim "electrical:12v:alternator ↵") with setpoints designed for LFP
	- install a voltage sensing switch to control the relay, set more appropriately for LFP's resting voltage
	- install [DC-DC](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b").
- Voltage-sensing relays can be unintentionally triggered <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__87">87)</a></sup> or “held closed” <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__88">88)</a></sup> [by voltage from the solar-charged side](http://bdp.mousetrap.net/index.php/2018/10/27/side-effect-of-solar-alternator-charging/ "http://bdp.mousetrap.net/index.php/2018/10/27/side-effect-of-solar-alternator-charging/") in some scenarios. Workaround: address with HVD as below if desired, or with a [DC-DC charger](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b"), or by adding a switch to disable the VSR.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__89">89)</a></sup>
- On ignition-triggered <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__90">90)</a></sup> setups **if the key is turned to ACC but the engine not started a depleted house battery can pull down the starter battery**. Workarounds: use a VSR, a DC delay timer, a DC-DC charger, or start the vehicle immediately after inserting the key <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__91">91)</a></sup>.
- Solar charging while the engine is running may [get "stuck" at alternator voltage](https://rvwiki.mousetrap.net/doku.php?id=opinion:frater_secessus:alternatorsolarstall "opinion:frater_secessus:alternatorsolarstall"). Workaround: higher solar wattage, DC-DC charger, or diode/FET-based isolator, or a switch to disconnect isolator after alternator voltage is reached. The [Victron Cyrix-ct isolator](https://amzn.to/3h5iMUd "https://amzn.to/3h5iMUd") could be useful here, as it appears to disconnect >13.8v.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__92">92)</a></sup>
- Alternator charging may bring some battery chemistries (like bare lithium cells with no BMS) to **unsuitably high voltages**. Workarounds: A [high voltage disconnect](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:hvd "electrical:12v:hvd") can [restrict alternator charging to lower voltages](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator_charging_hvd "electrical:12v:alternator_charging_hvd"). And [DC-DC chargers](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") can also regulate voltage provided to the house battery.
- It is possible for a plain combiner to “mask” the symptoms of a failing starter battery since the house bank would be assisting with the start. It is also possible for powerful solar to mask symptoms of a dying alternator because in that case the solar is helping run the chassis electricals.

## disabling alternator charging

It may be desirable to disable alternator charging on-the-fly when stopped in traffic, on hot days, to avoid charging frozen Li cells,<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__93">93)</a></sup> stop charging at a given voltage,<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__94">94)</a></sup> or neutralize [gotchas](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#gotchas "electrical:12v:alternator"), etc. The method of disabling will vary depending on the gear:

- relays and DC-DC that are triggered solely by D+ can be disabled by a switch on the D+ wire. [Additional control could be introduced](https://www.reddit.com/r/VanLife/comments/1c4vjl0/is_this_renogy_a_good_dcdc_option_for_a_200ah/kzuc78v/ "https://www.reddit.com/r/VanLife/comments/1c4vjl0/is_this_renogy_a_good_dcdc_option_for_a_200ah/kzuc78v/") with a relay and or delay ([example](https://amzn.to/3TUEbmu "https://amzn.to/3TUEbmu"))
- VSR triggered by voltage can can be disabled by a switch on the thin ground wire on the VSR itself.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__95">95)</a></sup>
- some DC-DC can be *derated* <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__96">96)</a></sup> by providing a 12v signal to the CURRENT LIMIT terminal ([Renogy DC1212 series](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b#renogy1 "electrical:12v:b2b"), [Leaptrend](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b#leaptrend "electrical:12v:b2b")) or through a setting in an app (Renogy DCC50S), etc
- some DC-DC can be *disabled* by providing a 12v signal to a remote ON/OFF terminal ([Victron Orion-TR](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b#victron "electrical:12v:b2b")), [Kisae](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b#disabling_the_kisae "electrical:12v:b2b").
- on units that have a dedicated NEG (“ground”, negative return) to the starter battery there may be no easy disable method. The brute force method would be to insert a relay between the starter battery POS and the unit's POS input, and control the relay with a switch.
- bluetooth-enabled DC-DC can often be disabled or derated from the app

[A NC thermal switch](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator_details#thermal_switches "electrical:12v:alternator_details") affixed to the alternator case might be used to automate this shutoff, or a NO switch to trigger a low-output mode on the Renogy or Leaptrend chargers mentioned above.

A voltage-sensing relay might be used to add voltage-sensing to a relay triggered by D+, or to disconnect at a given setpoint.

## wiring the setup

In most setups 'dwellers:

- install a dedicated POS line from the starterbatt or alternator to the combiner's input
- run another length of dedicated POS from the device's output the house battery bank
- **use the vehicle chassis/body for the NEG return path** back to the alternator/starterbatt <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__97">97)</a></sup>
- [trigger](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#triggering "electrical:12v:alternator") charging by voltage or with a 12v signal

Exceptions:

- vehicles without solid connection between the chassis and alternator (pickup truck beds, travel trailers, fiberglass vehicles) will require a separate NEG return wire to complete the circuit
- the chassis introduces considerable resistance, so high-current setups may require a separate NEG return. This resistance is often beneficial, [reducing the current acceptance of LiFePO4 or large lead banks to manageable levels](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:directcharginglfp#neg_return_through_chassis "electrical:12v:directcharginglfp").
- **Solar** NEG doesn't need to be connected to the chassis <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__98">98)</a></sup> because it brings its own NEG/POS to the party and isn't trying to talk (electrically) with the vehicle itself.

### sizing the wire

1. Assess how much current the charging system will pass. With DC-DC that current will be the output rating of the charger (40A, 50A, etc). With plain relays there will be [a bit of arithmetic](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#sizing_a_relay "electrical:12v:alternator") involved
2. use the [Blue Sea chart](http://assets.bluesea.com/files/resources/newsletter/images/DC_wire_selection_chartlg.jpg "http://assets.bluesea.com/files/resources/newsletter/images/DC_wire_selection_chartlg.jpg") to choose the appropriate wiring gauge. Note: *distance* includes the entire circuit, even if NEG is bonded to the chassis.

#### wire size and voltage sag

The Blue Sea chart shows wire sizes for both **Critical** and **Non-Critical loads**. The difference is in how much [voltage sag](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:voltage_sag "electrical:12v:voltage_sag") will be present at high levels of current. *Critical* in this context refers to electronics with narrow input voltage requirements <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__99">99)</a></sup>, or power transmission where every watt counts <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__100">100)</a></sup>. Both critical and noncritical wiring specs in the chart are safe.

All other things being equal, it is generally preferable to size the wiring to the Critical loads criteria. It makes little sense to buy a 60A DC-DC then choke it to 40A with thin wiring (see below).

There are reasons where one might choose Non-Critical sizing:

- fatter wire won't fit through the available space, or fit into the charger
- the DC-DC is [voltage sensing](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:voltage_sensing#chargers_with_voltage_sensing "electrical:12v:voltage_sensing") the house battery and can adjust for sag
- a relay is being used and the owner wants to tamp down current acceptance
- a relay is being used [alongside solar](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alt_and_solar "electrical:12v:alt_and_solar") so we are not relying on every Amp and volt from the alternator

#### effect of voltage sag on direct charging rates

We will use alternator voltage of 14.4v and discharged battery voltage of 12.1v below to illustrate how sag affects charging with a relay.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__101">101)</a></sup>. Current obeys the formula I=V/R, so **the greater the voltage sag the lower the current**. The actual values here aren't important, only the general pattern:

- a bank with theoretical max charging (massively oversized wiring for ~zero sag): **115A**
- critical load wiring (3% sag): **93.5A**
- noncritical load wiring (10% sag): **45A**

#### examples

Let's assume a 200A AGM bank that sits 10ft (20ft of wire for the complete circuit) from the starter battery or other connection point. 200Ah of AGM will pull ~60A (0.3C) at 50% depth of discharge.

If we want to make full use of DC-DC charging we would

- plan on a 60A DC-DC charger. Note that due to voltage boosting, 60A of charging to the battery may require ~20% more current (72A) from the battery.
- fuse for 72A + 20% = 86.4A between chassis and charger
- select **2awg** from the chart (20', critical, 70A-80A)

A plain isolator can't boost voltage while meeting a charging current target so we only have to worry about 60A. Run critical spec wiring if you want “full blast” and noncritical for reduced current:

- use any isolator rated at least 60A
- fuse for 60A + 20% = 72A between chassis and charger
- select wiring from the chart
	- **4awg** (20', critical, 60A), yielding ~60A when first connected. Maximum charging current for 200Ah of consumer-grade AGM.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__102">102)</a></sup>
	- **6awg** (20', noncritical (10% voltage sag), 60A), yielding ~30A when first connected. Minimum charging current for 200Ah of AGM.

Over time <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__103">103)</a></sup> isolator charging will deliver the same Ah back to the battery bank with either critical or noncritical wiring. The critical wiring will deliver high current that falls off sharply and linearly. The slope is quite steep. Noncritical wiring will deliver moderate current that also falls off linearly although more gradually. The slope is shallower.

A side effect is that if one drives on very short trips the critical wiring may deliver more Ah to the bank in the limited time available. The noncriticial wiring would be gentler on the alternator.

**Reminder**: it is hard to [keep lead batteries healthy](https://rvwiki.mousetrap.net/doku.php?id=electrical:batterycide "electrical:batterycide") by alternator charging alone. In order of decreasing effectiveness:

1. [add solar](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alt_and_solar "electrical:12v:alt_and_solar") to augment alternator charging
2. use [a DC-DC charger](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") to get at least the correct charging voltage
3. if charging by relay only, use Crtical size wire to get the most voltage and current to the lead house battery

### triggering

The setup needs to be *triggered* (told when to start/stop) so that it isn't connected all the time. There are two main methods:

1. use of an ON/OFF 12v trigger signal (“D+”, “IGN”, “ACC”). When the 12v signal is present the charging circuit is operational. Caveat: in this kind of setup leaving the key in the ACC position without starting the engine can drain the starter battery.
2. voltage-sensing - 12v is always being provided to the charger. The batteries are connected when the chassis voltage is above a voltage setpoint (often ≥13.4v) and disconnected when the chassis side measures below a setpoint (often ≤13.2v).

In some cases both voltage-sensing and D+ trigger are combined to work with the odd voltages that smart alternator equipped vehicles can present.

## alternator hacks

There are ways to get the alternator to pump out more power:

- a higher-output alternator can handle higher continuous output in a given set of conditions
- a different **voltage regulator** for older vehicles, [as demonstrated by SternWake](http://www.cheaprvliving.com/forums/Thread-Your-Vehicles-voltage-regulator "http://www.cheaprvliving.com/forums/Thread-Your-Vehicles-voltage-regulator"), increases the voltage available for charging but also increases the coach voltage.
- a [Sterling](http://www.sterling-power-usa.com/ "http://www.sterling-power-usa.com") “fake load” regulator will cause the alternator to put out more amps and then will DC-DC convert the voltage up to correct charging range.<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__104">104)</a></sup>. This is the opposite direction of how [MPPT charging](https://rvwiki.mousetrap.net/doku.php?id=electrical:solar:charge_controller "electrical:solar:charge_controller") works. Also see [b2b chargers](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b").

also see the [Alternator Details](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator_details "electrical:12v:alternator_details") page

## using the coach battery only

A simple possible approach would be to [replace the starter battery with a marine or AGM battery](https://rvwiki.mousetrap.net/doku.php?id=electrical:solar:shallow_cycling "electrical:solar:shallow_cycling").<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__105">105)</a></sup>

## charging remote batteries

### truck beds

If the bed does not have sufficient ground connectivity to run the NEG return through the body, then you can either:

- add an additional and/or beefier ground strap between bed and frame; or
- run a dedicated NEG return from the bank back to the starter batt, frame, etc.

### trailers

Some amount of power can be passed along the 7pin harness, usually enough to *maintain* the trailer battery's voltage and run small loads. For the purposes of this discussion [the important wires](https://www.etrailer.com/faq-wiring-7-way.aspx "https://www.etrailer.com/faq-wiring-7-way.aspx") in the 7-pin are:

- battery hot lead, typically **black**.
- ground <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__106">106)</a></sup> wire, typically **white**.

The minimum size for these wires is 12ga and some heavier models use 8ga.

### current on different sized wires

Given: a 3% maximum voltage drop <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__107">107)</a></sup> and a 40' round-trip wiring run from alternator to trailer battery we can provide Float voltage to the trailer battery [at these rates](https://www.tacomaworld.com/threads/hard-to-find-how-much-current-via-7-pin-trailer-connector.554056/#post-18045656 "https://www.tacomaworld.com/threads/hard-to-find-how-much-current-via-7-pin-trailer-connector.554056/#post-18045656"):

- 12ga ~5A
- 10ga ~8A
- 8ga ~10A

### workaround: voltage boosting

#### DC-DC charging

A configurable [DC-DC charger](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:b2b "electrical:12v:b2b") might be able to pass high enough voltage to overcome sag. If the 7-pin is the conduit then we are still limited to the currents listed above.

#### high-voltage boosting

More power (and more appropriate charging voltages) can be passed along separate wiring or down the 7-pin by [injecting higher voltages into the harness](https://diysolarforum.com/threads/ricks-charge-from-the-tv-solution-for-owners-of-mppt-charge-solar-in-the-trailer.20730/ "https://diysolarforum.com/threads/ricks-charge-from-the-tv-solution-for-owners-of-mppt-charge-solar-in-the-trailer.20730/").<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__108">108)</a></sup> This section will address 7pin injection.

The basic idea is alternator → DC boost to 36v or something → run down the 7pin charging wire to the trailer → MPPT charge controller → battery

Using 12ga wire as an example, 5A @ 13.6v = **68w**. After the same 3% voltage drop and MPPT conversion losses the boosted setup would deliver **166w**, and be able to ” [smart charge](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:charging "electrical:12v:charging") ” the trailer battery at appropriate voltage.

### workaround: heavier wiring

It's also possible to run a separate and (much) heavier & more expensive cable/connector from the TV to the trailer; this would minimize voltage sag.

## isolator without a house battery

**Q.** An “isolator” (combiner, relay, etc) is typically used to charge a house battery, so why install [a relay](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator#combiners "electrical:12v:alternator") if you have no house battery?

**A.** because it can bring Big Current into the cabin for other uses, and do so *only when the engine is running*. Ciggy ports are typically limited to 10A (120-150w).

**Examples:**<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__109">109)</a></sup>

- 120vac 300w [rice cooker](https://rvwiki.mousetrap.net/doku.php?id=food:cooking:excess_power#ac_inverter "food:cooking:excess_power") running on 500w MSW inverter, (~330w total after inefficiencies).
- 120vac 300w wall charger for your [solar generator](https://rvwiki.mousetrap.net/doku.php?id=lifestyle:faq_solar_generator "lifestyle:faq_solar_generator") running on a 400w inverter.
- if you have a stout enough alternator, a 120vac 700w instant pot running off an inverter.

This setup would be: starter battery → combiner <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__110">110)</a></sup> → inverter → 120vac devices

## the Orton method

Similar to the above, [the Orton method](https://www.ortontransit.info/electrical "https://www.ortontransit.info/electrical") uses a combiner to control power to an inverter. The inverter in turn runs AC-DC battery chargers and other shore power loads.

## tweaking the current

With a combiner there is no easy way to adjust current with precision; the batteries are effectively paralleled. You can *influence* the current a bit if you know what's going on.

With relays and isolators charge current is dependent on

1. the difference in voltage between alternator and battery bank. Because of this you will observe highest charging current when the bank voltage is lowest, decreasing as bank voltage rises. This is called the *current taper*.
2. the willingness of the batteries to accept current <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fn__111">111)</a></sup>
3. the resistance across the entire charging circuit

….and is [governed by the formula ''I=V/R''](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:directcharginglfp#the_formula_in_60_seconds "electrical:12v:directcharginglfp").

You can't do much about the first two, other than do any elective driving in the morning when bank voltage is likely to be lowest.

The third issue (excess resistance) might be tweaked by the user.

### increasing current

- If the NEG return goes through the chassis (the usual approach), then **doublecheck the “ground” connection to the chassis for corrosion and looseness**. The ground is a likely suspect if the setup charged at a higher rate in the past but has been falling off recently.
- If the ground is good and current acceptance is still too low you can either **run a dedicated NEG return wire of sufficient thickness back to the starter battery**. Or **install a DC-DC charger**, whichever is easiest/cheapest
- increase the capacity of the battery bank (100Ah → 200Ah) or replace the bank with a chemistry that will accept more currrent (AGM or LiFePO4); this is a radical change most will not adopt.
- unless the alternator is the sole/main form of charging one might choose to “live with it”, knowing that relay charging current will taper off as bank state of charge rises. The silver lining is current will be highest when you need it most (when the bank is low).

Note that, perhaps counterintuitively, the presence of active solar charging will often decrease alternator charging current because the solar is bumping up the bank voltage (case #1 above).

### decreasing current

- If there is a dedicated NEG return wire to the starter battery consider routing the “ground” through the chassis instead; that is the usual approach anyhow. ([further reading](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:directcharginglfp#tweaking_current_with_resistance "electrical:12v:directcharginglfp"))
- replace the combiner with a diode isolator (bigger drop) or FET isolator (smaller drop) ([further reading](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:directcharginglfp#tweaking_current_with_voltage "electrical:12v:directcharginglfp"))
- replace the combiner with a small DC-DC charger

## further reading

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__1">1)</a></sup>

[http://www.cheaprvliving.com/forums/showthread.php?tid=26877&pid=337117#pid337117http://www.cheaprvliving.com/forums/showthread.php?tid=26877&pid=337117#pid337117](http://www.cheaprvliving.com/forums/showthread.php?tid=26877&pid=337117#pid337117http://www.cheaprvliving.com/forums/showthread.php?tid=26877&pid=337117#pid337117 "http://www.cheaprvliving.com/forums/showthread.php?tid=26877&pid=337117#pid337117http://www.cheaprvliving.com/forums/showthread.php?tid=26877&pid=337117#pid337117")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__2">2)</a></sup>

“D+”, “IGN”, “ACC”

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__3">3)</a></sup>

monitoring of the actual voltage coming from the chassis

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__4">4)</a></sup>

and understanding the alternator has it's own stuff to run – wipers, fans, headlights, ECU, etc

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__5">5)</a></sup>

starter battery and house battery

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__6">6)</a></sup>

sits between alternator and batteries rather than between starter and house batteries

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__7">7)</a></sup>

ie, an isolator

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__8">8)</a></sup>

[https://www.cruisersforum.com/forums/f14/agm-battery-failure-two-sets-in-two-years-239438-7.html#post3229546](https://www.cruisersforum.com/forums/f14/agm-battery-failure-two-sets-in-two-years-239438-7.html#post3229546 "https://www.cruisersforum.com/forums/f14/agm-battery-failure-two-sets-in-two-years-239438-7.html#post3229546")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__9">9)</a></sup>

daily is ideal

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__10">10)</a></sup>

diode-based isolators will reduce current somewhat due to forward-voltage losses

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__11">11)</a></sup>

diode isolators will reduce voltage

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__12">12)</a></sup>

[https://www.redarc.com.au/how-do-i-know-if-i-have-a-variable-voltage-smart-alternator](https://www.redarc.com.au/how-do-i-know-if-i-have-a-variable-voltage-smart-alternator "https://www.redarc.com.au/how-do-i-know-if-i-have-a-variable-voltage-smart-alternator")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__13">13)</a></sup>

as when idling

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__14">14)</a></sup>

as with giant AGM or lithium banks

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__15">15)</a></sup>

[https://vanlivingforum.com/threads/new-wiring-sketch.43877/post-544396](https://vanlivingforum.com/threads/new-wiring-sketch.43877/post-544396 "https://vanlivingforum.com/threads/new-wiring-sketch.43877/post-544396")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__16">16)</a></sup>

all alternators have a non-infinite lifespan, not just ones used to charge aux banks

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__17">17)</a></sup>

or fans

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__18">18)</a></sup>

[http://www.cheaprvliving.com/forums/Thread-Longer-alternator-life-when-used-to-charge-house-batteries?pid=182096#pid182096](http://www.cheaprvliving.com/forums/Thread-Longer-alternator-life-when-used-to-charge-house-batteries?pid=182096#pid182096 "http://www.cheaprvliving.com/forums/Thread-Longer-alternator-life-when-used-to-charge-house-batteries?pid=182096#pid182096")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__19">19)</a></sup>

[https://www.promasterforum.com/threads/fuel-consumption-at-idle.103939/post-841876](https://www.promasterforum.com/threads/fuel-consumption-at-idle.103939/post-841876 "https://www.promasterforum.com/threads/fuel-consumption-at-idle.103939/post-841876")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__20">20)</a></sup>

this happens because lead chemistry voltage rises (and acceptance drops) linearly while charging

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__21">21)</a></sup>

this happens because lithium has a flat middle in the voltage curve with steep angles at either end

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__22">22)</a></sup>

disregarding charging inefficiences

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__23">23)</a></sup>

[https://www.irv2.com/forums/f87/alternator-burn-out-from-lithium-batteries-558284-10.html#post6433111](https://www.irv2.com/forums/f87/alternator-burn-out-from-lithium-batteries-558284-10.html#post6433111 "https://www.irv2.com/forums/f87/alternator-burn-out-from-lithium-batteries-558284-10.html#post6433111")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__24">24)</a></sup>

I=V/R

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__25">25)</a></sup>

[https://www.redarc.com.au/alternator-vs-fixed-alternator](https://www.redarc.com.au/alternator-vs-fixed-alternator "https://www.redarc.com.au/alternator-vs-fixed-alternator")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__26">26)</a></sup>

[https://www.irv2.com/forums/f87/alternator-burn-out-from-lithium-batteries-558284-10.html#post6433029](https://www.irv2.com/forums/f87/alternator-burn-out-from-lithium-batteries-558284-10.html#post6433029 "https://www.irv2.com/forums/f87/alternator-burn-out-from-lithium-batteries-558284-10.html#post6433029")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__27">27)</a></sup>

triggered by D+, and DIP or other setting might be required

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__28">28)</a></sup>

typically from the vehicle ignition

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__29">29)</a></sup>

from starter battery to house battery

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__30">30)</a></sup>

surprise!!!

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__33">33)</a></sup>

return circuit

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__34">34)</a></sup>

[https://aviondemand.com/insider/starter-solenoids-and-continuous-duty-solenoids/](https://aviondemand.com/insider/starter-solenoids-and-continuous-duty-solenoids/ "https://aviondemand.com/insider/starter-solenoids-and-continuous-duty-solenoids/")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__35">35)</a></sup>

[https://www.littelfuse.com/technical-resources/technical-centers/commercial-vehicle-technical-center/frequently-asked-questions.aspx?utm\_source=colehersee.com&utm\_medium=redirect&utm\_campaign=colehersee-lf#question\_37](https://www.littelfuse.com/technical-resources/technical-centers/commercial-vehicle-technical-center/frequently-asked-questions.aspx?utm_source=colehersee.com&utm_medium=redirect&utm_campaign=colehersee-lf#question_37 "https://www.littelfuse.com/technical-resources/technical-centers/commercial-vehicle-technical-center/frequently-asked-questions.aspx?utm_source=colehersee.com&utm_medium=redirect&utm_campaign=colehersee-lf#question_37")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__36">36)</a></sup>

VSR

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__37">37)</a></sup>

dVSR - d is for *dual*

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__38">38)</a></sup>

[https://marinehowto.com/automatic-charging-relays/](https://marinehowto.com/automatic-charging-relays/ "https://marinehowto.com/automatic-charging-relays/")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__39">39)</a></sup>

apparently time-based, see documentation

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__40">40)</a></sup>

[https://www.al-electric.de/\_dokumente/143/1314A/1314A.pdf](https://www.al-electric.de/_dokumente/143/1314A/1314A.pdf "https://www.al-electric.de/_dokumente/143/1314A/1314A.pdf")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__41">41)</a></sup>

[https://www.wirthco.com/battery-doctor-isolator-20090-and-20092-user-manual](https://www.wirthco.com/battery-doctor-isolator-20090-and-20092-user-manual "https://www.wirthco.com/battery-doctor-isolator-20090-and-20092-user-manual")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__42">42)</a></sup>, <sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__46">46)</a></sup>

time-based, see documentation

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__43">43)</a></sup>

time-based

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__44">44)</a></sup>

[https://www.victronenergy.com/upload/documents/Manual-Cyrix-ct-120-EN-NL-DE-FR-ES.pdf](https://www.victronenergy.com/upload/documents/Manual-Cyrix-ct-120-EN-NL-DE-FR-ES.pdf "https://www.victronenergy.com/upload/documents/Manual-Cyrix-ct-120-EN-NL-DE-FR-ES.pdf")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__45">45)</a></sup>

*not* to D+/IGN

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__47">47)</a></sup>

[https://www.bluesea.com/products/7611/BatteryLink\_Automatic\_Charging\_Relay\_-\_12V\_24V\_DC\_120A](https://www.bluesea.com/products/7611/BatteryLink_Automatic_Charging_Relay_-_12V_24V_DC_120A "https://www.bluesea.com/products/7611/BatteryLink_Automatic_Charging_Relay_-_12V_24V_DC_120A")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__48">48)</a></sup>

typically 0.5A

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__49">49)</a></sup>

yellow knob visible on top of housing

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__50">50)</a></sup>

bonus points to the Jaycorp for printing the connect/disconnect setpoints right on the isolator!

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__51">51)</a></sup>

[https://www.precisioncircuitsinc.com/wp-content/uploads/2017/06/00-10041-2xx-Battery-Isolation-Manager-Rev7-1.pdf](https://www.precisioncircuitsinc.com/wp-content/uploads/2017/06/00-10041-2xx-Battery-Isolation-Manager-Rev7-1.pdf "https://www.precisioncircuitsinc.com/wp-content/uploads/2017/06/00-10041-2xx-Battery-Isolation-Manager-Rev7-1.pdf")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__52">52)</a></sup>

[https://sprinter-source.com/forums/index.php?threads/68203/post-762424](https://sprinter-source.com/forums/index.php?threads/68203/post-762424 "https://sprinter-source.com/forums/index.php?threads/68203/post-762424")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__53">53)</a></sup>

[https://www.irv2.com/forums/f103/bird-vs-bim-236021.html#post2432852](https://www.irv2.com/forums/f103/bird-vs-bim-236021.html#post2432852 "https://www.irv2.com/forums/f103/bird-vs-bim-236021.html#post2432852")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__54">54)</a></sup>

BI-DIRECTIONAL ISOLATOR RELAY DELAY

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__55">55)</a></sup>

[https://intellitec.com/wp-content/uploads/2019/05/53-00362-100.pdf](https://intellitec.com/wp-content/uploads/2019/05/53-00362-100.pdf "https://intellitec.com/wp-content/uploads/2019/05/53-00362-100.pdf")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__56">56)</a></sup>

[https://www.irv2.com/forums/f115/bird-bad-advice-158964.html#post1544130](https://www.irv2.com/forums/f115/bird-bad-advice-158964.html#post1544130 "https://www.irv2.com/forums/f115/bird-bad-advice-158964.html#post1544130")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__57">57)</a></sup>

[https://newpar.newmarcorp.com/instance1Env99NEWMAR/html/images/SS2011Electrical12V.pdf](https://newpar.newmarcorp.com/instance1Env99NEWMAR/html/images/SS2011Electrical12V.pdf "https://newpar.newmarcorp.com/instance1Env99NEWMAR/html/images/SS2011Electrical12V.pdf")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__58">58)</a></sup>

[https://8hi01e.a2cdn1.secureserver.net/wp-content/uploads/2022/02/53-00131-100-SERVICE-MANUAL-1.pdf](https://8hi01e.a2cdn1.secureserver.net/wp-content/uploads/2022/02/53-00131-100-SERVICE-MANUAL-1.pdf "https://8hi01e.a2cdn1.secureserver.net/wp-content/uploads/2022/02/53-00131-100-SERVICE-MANUAL-1.pdf")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__59">59)</a></sup>

where current could go either way after connection is made

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__60">60)</a></sup>

since the existing wiring is usually `alternator → starter → starter battery` the install is either directly from the alternator or after the starter.

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__61">61)</a></sup>

the actual drop is described by the Shockley diode equation, which exceeds the scope of this article.

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__63">63)</a></sup>

[https://www.victronenergy.com/upload/documents/Datasheet-Argodiode-Battery-Isolators-EN.pdf](https://www.victronenergy.com/upload/documents/Datasheet-Argodiode-Battery-Isolators-EN.pdf "https://www.victronenergy.com/upload/documents/Datasheet-Argodiode-Battery-Isolators-EN.pdf")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__64">64)</a></sup>

[https://www.rutronik.com/article/power-electronics-si-si-schottky-or-sic-schottky/](https://www.rutronik.com/article/power-electronics-si-si-schottky-or-sic-schottky/ "https://www.rutronik.com/article/power-electronics-si-si-schottky-or-sic-schottky/")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__65">65)</a></sup>

the relay would be required to keep the isolator from continuously draining the starter battery. In a three-pin setup there is no power coming from the alternator when the engine is off

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__66">66)</a></sup>

[https://www.ctek.com/storage/5CDB4E293A03CBF6442A620EC8E49CFB548CB48E9BF93425638077279A13BBA1/ac5639c5feaa46d38411ebd69f915b5b/pdf/media/65589cee7d4342e0891e2130149be66f/SmartPass%20120S.pdf](https://www.ctek.com/storage/5CDB4E293A03CBF6442A620EC8E49CFB548CB48E9BF93425638077279A13BBA1/ac5639c5feaa46d38411ebd69f915b5b/pdf/media/65589cee7d4342e0891e2130149be66f/SmartPass%20120S.pdf "https://www.ctek.com/storage/5CDB4E293A03CBF6442A620EC8E49CFB548CB48E9BF93425638077279A13BBA1/ac5639c5feaa46d38411ebd69f915b5b/pdf/media/65589cee7d4342e0891e2130149be66f/SmartPass%20120S.pdf") says it is MOSFET

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__67">67)</a></sup>

[https://www.12voltplanet.co.uk/user/downloads/SMARTPASS\_120S-manual-low-UK-EN.pdf](https://www.12voltplanet.co.uk/user/downloads/SMARTPASS_120S-manual-low-UK-EN.pdf "https://www.12voltplanet.co.uk/user/downloads/SMARTPASS_120S-manual-low-UK-EN.pdf")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__68">68)</a></sup>

at least the voltage regulators

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__69">69)</a></sup>

Delcotron-style?

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__70">70)</a></sup>

usually the fourth stud, assuming there is one input and two outputs

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__71">71)</a></sup>

ie, “closed” = “circuit is complete/active”

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__72">72)</a></sup>

most?

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__73">73)</a></sup>

variable voltage

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__74">74)</a></sup>

an electromagnet holds the parts of the active circuit together, When power to the inolator input is cut the electromagnet can no longer hold the circuit closed. The circuit is open and the batteries are isolated from each other.

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__76">76)</a></sup>

same reason headlights are turned on at the donor car when jumpstarting

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__78">78)</a></sup>

among other factors

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__79">79)</a></sup>

200Ah/5

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__80">80)</a></sup>

likely with peak tolerance of 60A or so

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__81">81)</a></sup>

assuming you aren't applying heavy loads like a microwave while driving

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__82">82)</a></sup>

100A peak

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__83">83)</a></sup>

It's actually the *delta* (difference) between alternator and battery voltage but we assume that alternator voltage is stable

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__84">84)</a></sup>

single alternator

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__85">85)</a></sup>

including a charging battery

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__86">86)</a></sup>

even “smart” [staged charging](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:charging "electrical:12v:charging")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__87">87)</a></sup>

dVSR

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__88">88)</a></sup>

both VSR and dVSR

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__89">89)</a></sup>

a momentary-off switch would kill the connection, although an ON/OFF switch might be useful for other purposes

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__90">90)</a></sup>

IGN, D+

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__91">91)</a></sup>

ie, do not leave in the Accessory position which would drain the starter battery

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__92">92)</a></sup>

[https://www.victronenergy.com/upload/documents/Datasheet-Cyrix-ct-120A-230A-EN.pdf](https://www.victronenergy.com/upload/documents/Datasheet-Cyrix-ct-120A-230A-EN.pdf "https://www.victronenergy.com/upload/documents/Datasheet-Cyrix-ct-120A-230A-EN.pdf")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__93">93)</a></sup>

using a temperature controller

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__94">94)</a></sup>

using a [High Voltage Disconnect](https://rvwiki.mousetrap.net/doku.php?id=electrical:12v:alternator_charging_hvd "electrical:12v:alternator_charging_hvd")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__95">95)</a></sup>

the VSR requires a ground to make a complete circuit to run internal electronics. Breaking this circuit turns off the VSR

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__96">96)</a></sup>

output intentionally reduced

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__97">97)</a></sup>

VSRs, DC-DC and other types with internal electronics will have a small ground wire

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__98">98)</a></sup>

there are some exceptions with 1-wire panels that use the mounting for the other leg of the circuit

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__99">99)</a></sup>

not an issue with most van gear

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__100">100)</a></sup>

(not applicable to alternator charging

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__101">101)</a></sup>

We will also assume a resting resistance of 20m Ohm to complete the formula

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__102">102)</a></sup>

high end AGM like Lifeline requires 0.5C, or 100A for 200Ah

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__103">103)</a></sup>

half hour? hour?

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__104">104)</a></sup>

[http://www.sterling-power-usa.com/library/What%20is%20an%20alternator%20to%20battery%20charger.pdf](http://www.sterling-power-usa.com/library/What%20is%20an%20alternator%20to%20battery%20charger.pdf "http://www.sterling-power-usa.com/library/What%20is%20an%20alternator%20to%20battery%20charger.pdf")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__105">105)</a></sup>

[http://www.cheaprvliving.com/forums/Thread-Easiest-simplest-cheapest-power-set-up](http://www.cheaprvliving.com/forums/Thread-Easiest-simplest-cheapest-power-set-up "http://www.cheaprvliving.com/forums/Thread-Easiest-simplest-cheapest-power-set-up")

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__106">106)</a></sup>

negative return

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__107">107)</a></sup>

14v at the alternator and 13.6v at the battery

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__108">108)</a></sup>

disregard the relay complication; you can use a toggle switch if desired

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__109">109)</a></sup>

while driving, not while idling

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__110">110)</a></sup>

A $25-$40 VSR (often marketed as a smart battery isolator) might be easiest. Could go even cheaper with a regular relay but you'd have to hunt for a D+/IGN signal.

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__111">111)</a></sup>

mainly an issue with lead chemistries in late Absorption, “solar generators”, and Li with exceptionally hamstrung BMS

<sup><a href="https://rvwiki.mousetrap.net/?id=electrical:12v:alternator#fnt__112">112)</a></sup>

and is not “smart”, or variable voltage

electrical/12v/alternator.txt · Last modified: 2025/06/23 15:42 by frater\_secessus

---
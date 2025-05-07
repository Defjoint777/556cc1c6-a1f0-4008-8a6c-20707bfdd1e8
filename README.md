<!---
{
  "depends_on": ["cartesian product", "mapping", "functions"],
  "author": "Stephan Bökelmann",
  "first_used": "2025-03-27",
  "keywords": ["binary", "digital logic", "relays"]
}
--->

# Mapping Binary Numbers onto Switches and Relays

## 1) Introduction
When we think of computers and electronics, we often imagine complex circuits. But at their heart, they are systems that make decisions based on **binary input** — sequences of 0s and 1s.

Without needing any electronics background, we can think about each **input switch** as being either in state `0` (off) or `1` (on). This means each switch is a variable from the set:
```
{0, 1}
```

Now imagine we have **multiple switches** — for example, two or three. Then the full state of the system is described by all combinations of those switches. This is a Cartesian product of multiple `{0, 1}` sets.

---

### 1.0.1) One Switch, One LED
Let’s begin simply. We have **one switch** and **one LED**. The LED turns on when the switch is ON (`1`), and turns off when the switch is OFF (`0`).

We can describe this relationship as a **function**:
```
f: {0, 1} → {off, on}
f(x) = if x == 1 then 'on' else 'off'
```

This simple wire between switch and LED *is the function*.

Visualization:
```
Switch:  0   -->   LED: off
Switch:  1   -->   LED: on
```

---

### 1.0.2) Two Switches, One Relay
Now let’s add a second switch. Each switch still has two possible states, so together they form:
```
{0, 1} × {0, 1} = { (0,0), (0,1), (1,0), (1,1) }
```

This is the set of all possible combinations of the two switches. We now define a function based on these inputs. For instance:
```
f(a, b) = 'on' if both a == 1 and b == 1, else 'off'
```

This function behaves like an **AND gate** in digital electronics.

Visualization:
```
Switch A  Switch B  ->  LED
   0          0         off
   0          1         off
   1          0         off
   1          1         on
```

---

### 1.0.3) Generalizing
If you add a third switch, the total set of inputs becomes:
```
{0, 1} × {0, 1} × {0, 1} = 8 combinations
```
Each combination is a **tuple**, like `(1, 0, 1)`, and the function describes how this tuple is mapped to an output — like turning on a light or triggering a relay.

This shows how binary inputs (the domain) and output states (the codomain) are connected via a **function**, which you can think of as the **wiring** between switches and LEDs.

---

## 2) Tasks

1. **Map a Single Switch to a Light**: Write down the mapping table for one switch connected to one LED, as shown above.
   eingabe 0 = LED aus
   eingabe 1 = LED AN
   

3. **Enumerate the Cartesian Product of Two Switches**: List all 4 combinations of 2 switches. Define a function that turns the LED on *only if both are ON*.
  function (a,b)
    while(a && b !== 0)
   {
      led.turnOn()
   }

input     output
1  1        on
1  0        off
0  1        off
0  0        off

5. **Explore Your Own Logic**: Design a function for 3 switches that turns on a "lamp" in the following cases:
   - If at least two switches are ON
   - If the first and last switches are ON
   - If exactly one switch is ON
   - 
function(a,b,c)
  if(a+b+c >= 2)
{
    lamp.On()

}
if(a && c => 2)
{
  lamp.On()
}
if(a || b || c == 1)
{
lamp.On()
}

A  B  C   Output
1  1  0  110
0  1  1  011
1  0  1  101
1  1  1  111
0  0  0  000
0  1  0  010
1  0  0  100
0  0  1  001
   Draw the corresponding truth table (all 8 combinations).

---

## 3) Questions
1. Why does the total number of combinations grow as 2^n when you add more switches?
   Because every switch got 2 states, if we got 2 switsches with 2 states it means 4 possible combinations if we add 1 more switch that meanse the 4 * 2, because all combinations can be combinated with 2 second states.
   
3. In which ways can you think of the wiring between inputs and outputs as a function?
4. u can think about it in the way of function because inputs (domain) generate output(codomain)
   what means we can ilustrate a relationship between 2 elements
   
6. How would you represent these switch states as binary numbers?
7. Can you find a function that always maps different input states to different outputs? What kind of function is that?
   its calls Injective function

---

## 4) Final Advice
Binary inputs like switches are a perfect, tangible model for understanding Cartesian products and mappings. You don’t need electronics to grasp how a function connects states of switches to outcomes like turning on a light.

> Try imagining the switches as bits in a binary number, and the wiring as a simple set of rules — this is exactly how computers think.

Once you’ve mastered this, everything from logic gates to programming conditions becomes much easier to understand.

Want to build your own version with actual switches and LEDs? That’s just the next step.


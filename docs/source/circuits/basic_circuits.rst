===========
DC Circuits
===========

The following is a beginner's introduction to direct current (DC), written for
a college-aged audience. If you have prior knowledge of circuits (e.g. by
having taken a physics class in high school or in college) and have a
working understanding of Ohm's Law, you can safely skip this section.

What is direct current?
=======================

`Wikipedia <https://en.wikipedia.org/wiki/Direct_current>`_ defines direct
current (also referred to as "DC", or more redundantly as "DC current") as "the
unidirectional flow of an electric charge." There are two key components to
this definition: there is an electric charge (in the form of electrons moving
between atoms), and it is moving in one direction.

This differs from `alternating current
<https://en.wikipedia.org/wiki/Alternating_current>`_, or AC, wherein the flow
of charge will oscillate back and forth, like a child on a swing.
There are important differences between what DC and AC are typically used for,
and how to work with them safely. AC is most commonly used for power
transmission (i.e. through power lines), and other contexts that require
large amounts of electrical power.

DC is easier to understand than AC; is much more commonly used in building
circuits with Arduino boards than AC; and is usually much safer than AC, since
common direct currents are very small. We'll be focusing on the intuitive
basics of DC in this tutorial.


Electric potential and voltage (:math:`V`)
==========================================

A common analogy for teaching about electrical current `compares electric
current to flowing water <https://en.wikipedia.org/wiki/Hydraulic_analogy>`_.

Imagine water flowing through a long garden hose. One end of the hose is
screwed into a spigot: when a person turns the valve on the spigot, water flows
into the hose *under pressure* and flows toward the other end. We assume that
the other end isn't connected to anything, and that water simply dribbles out
when it reaches it.

If the person fully opens the valve, then the pressure pushing water into (and
through) the hose increases. The water will move faster, that is, the volume of
water moving through the hose per second will increase. This movement rate
would be measured in units of volume per unit time, e.g. in liters per second.
If the person starts to close the valve, that driving pressure decreases, and
water will flow more slowly.

The pressure in the hose is analogous to the *voltage* (denoted :math:`V`) of
an electric current; the spigot is *loosely* analogous to a so-called "voltage
source", like a battery. Just as a person can control the rate of water flow
through their hose by adjusting water pressure at the spigot, a person can also
control the rate at which electric charges (electrons) move through a wire by
adjusting the **voltage** produced at the voltage source. A higher voltage is
more forceful and, all else being equal, will push more electrons through the
circuit per second.

The rate at which electrons move through a conductor is almost literally
measured in "electrons per second". The units used are seconds and the `coulomb
(C) <https://en.wikipedia.org/wiki/Coulomb>`_, where one coulomb represents a
*positive* charge of magnitude equivalent to that of approximately :math:`1.602 *
10^{19}` electrons, or the same number of protons. One coulomb per second is an
`ampere (A) <https://en.wikipedia.org/wiki/Ampere>`_, often abbreviated "amp."

It's worth noting that the vast majority of electric currents in an
Arduino-based circuit are on the order of milliamps (:math:`mA`), i.e.
thousandths of an ampere. When working with microcontrollers, one "full" ampere
is a *gargantuan* amount of current that would usually only be seen when
working with high-power components, like an electric motor. An Arduino Uno, as
specced, can produce no more than :math:`40 mA` from a single (ordinary) pin.

Measuring voltage
-----------------

The volt is a measurement of electric potential at a particular point, given in
units of `joules <https://en.wikipedia.org/wiki/Joule>`_ per coulomb.

You may recognize the joule as a unit of energy. Roughly speaking, if a battery
produces nine volts, that means that it will impart nine joules of electrical
energy into every :math:`1.602 * 10^{19}` electrons that it pushes into the
circuit.

This can be understood by comparison to gravitational potential. The
`gravitational potential energy (GPE) <https://en.wikipedia.org/wiki/Gravitational_energy>`_
of an object is given by the equation :math:`GPE = mgh`, where :math:`GPE` is the
potential energy of the object in joules, :math:`m` is the object's mass in
kilograms, `g` is the acceleration due to gravity in meters-per-second-squared,
and `h` is the object's distance from the ground in meters.

On Earth, any object dropped on the Earth's surface will accelerate towards it
at :math:`9.81` meters per second, per second (i.e. :math:`9.81 (m/sec)/sec`,
or `9.81 m/sec^2`). For this reason, :math:`g` can usually be treated as a
constant.

For a :math:`1 kg` object one meter above the ground will have GPE equal to:

.. math::
  (1 kg)(9.81 m/s^2)(1m) = 9.81 kg*(m/s)^2 = 9.81 J

A :math:`2 kg` object would have GPE equal to:

.. math::
  (2 kg)(9.81 m/s^2)(1m) = 19.62 kg*(m/s)^2 = 19.62 J

Note that, with :math:`g` and :math:`h` being held constant, doubling :math:`m`
doubles the potential energy of the object. Halving :math:`m` would halve the
object's potential energy, and so on.

Because of this, one might say that the *gravitational potential* of any object
one meter above the ground on Earth is:

.. math::
  gh = (9.81 m/s^2)(1m) = 9.81 (m^2/s^2) = 9.81 (m/s)^2 = 9.81 J/kg

In other words, given a fixed :math:`g` and a fixed :math:`h`, you can find the
GPE of any object just by multiplying its mass by the gravitational potential
:math:`9.81 J/kg`.

In a similar way, you can find the energy of any clump of electric charge by
taking the amount of charge (in coulombs) and multiplying it be the electric
potential at its location (in volts, i.e. joules-per-coulomb).

For reasons we'll skip over, voltage measurements are almost always reported as
the *difference* in voltage/electric potential between two points in a circuit.
A `ground <https://en.wikipedia.org/wiki/Ground_(electricity)>`_ within the
circuit is defined as the zero point; just as an object literally resting on
the ground would have zero joules of GPE, we say that that an electric charge
at *electrical* ground has zero joules of energy.

This isn't *literally* true. The "true" electric potential of the electrical
ground is almost always nonzero. However, this generally only matters when the
circuit in question might be connected to a larger circuit or object. Imagine a
circuit whose ground actually has an electric potential of :math:`0.005 J/C`.
The *literal* ground (i.e. the dirt on the surface of the Earth) might have an
electric potential of :math:`0.001 J/C`; if the circuit's electrical ground
were connected to the literal, Earth-dirt ground, current would flow from the
circuit ground into the Earth ground. DC circuits don't typically do this,
however, so defining the circuit's electrical ground as having electric
potential :math:`0 V = 0 J/C` (so that, in this example, the literal Earth has
electric potential :math:`-0.004 V = -0.004 J/C`) just serves to make math
easier. If a circuit is powered by an ordinary battery, its negative terminal
("minus-end") is usually chosen as the circuit's electrical ground.

Note that a good electrical ground is assumed to have a constant voltage, no
matter what component of the circuit it may be connected to, which is almost
always true with small DC circuits. In some applications, however, this isn't a
good assumption. The actual, literal Earth is used as an electrical ground for
(e.g.) the circuits of a house, often by driving a metal stake into the dirt
and running a wire to it. But if enough circuits are connected to Earth ground
in this fashion, it becomes possible for current to flow through the Earth from
one metal stake to another. This doesn't matter much for home wiring, but this
condition (called a `ground loop <https://en.wikipedia.org/wiki/Ground_loop_(electricity)>`_)
can be an issue for sensitive electronics, like radio receivers.


Direction of current flow
-------------------------

Note that you can infer the direction in which water will flow based on where
the water pressure "comes from." In the given example, water flows from the
spigot (where water pressure is high) to the open end of the hose, where water
pressure is low.

One can determine the direction in which electric current will flow using a
similar, but much more counterintuitive set of principles. In short, current
will flow from points of *high* electric potential (i.e. high voltage) to
points of low potential (i.e. low voltage).

However, the short answer masks a great deal of underlying weirdness. First,
note that the electron is a *negatively charged particle*. When theories of
electricity were first being formulated, it was *incorrectly* assumed that the
particle that "carries" electric charge was *positively* charged; common
conventions describing electrical current developed using that assumption.

The most odious of these is the convention for electric current. Recall that
an ampere is one coulomb of charge per second (:math:`1 C/sec`), and that
:math:`1 C` is a *positive* charge. But electrons are negatively charged! So
when one coulomb of current flows from a voltage source to a voltage "sink"
(i.e. from the positive "plus-end" of a battery to its minus-end), what is
*actually* happening is that :math:`1.602 * 10^{19}` electrons are flowing in the
*opposite direction* from the negative terminal to the positive terminal.

This can be confusing, and tends to be massively frustrating for students
studying electricity. The authors find it helpful to pretend that electrons
aren't real, and to *pretend* that there are positively charged anti-electrons
flowing from the plus-end of a battery to its minus-end.

Resistance and ohms (:math:`\Omega`)
====================================

Let's return to the flowing water analogy. Imagine that you were to attach a
`clamp <https://en.wikipedia.org/wiki/C-clamp>`_ to the hose, and were using it
to pinch the hose's tube. As you tighten the clamp, the section of hose being
pinched will become increasingly narrow. It becomes harder for water to move
past; that section offers more **resistance** to water flow. The rate at which
the water flows the end of the hose (in liters per second) will decrease.

A clamp isn't the only thing that could have this effect. If you were to
connect the hose's free end to an `oscillating sprinkler
<https://home.howstuffworks.com/sprinkler.htm>`_, the added difficulty of
forcing water through the sprinkler's tubing and sprinkler holes also adds
resistance, reducing the volume of water that can move through the hose per
second. Even sticking your thumb into the open end of the hose (to make water
spray out from around your thumb, rather than coming out as a dribble) adds
resistance.

Note that these "water flow resistors" don't act as *hard limits* on how much
water can flow through the hose, that is, these resistors won't limit water
flow to 50 liters per minute, or similar. Increasing the water pressure in the
hose (by opening the spigot's valve further) will also increase the rate of
flow. The resistors simply make it more difficult (i.e. more pressure is
required) to move water through the hose at a fixed rate; or, equivalently,
they reduce the amount of water that can flow given a fixed water pressure.

.. note::
  One of the major effects of putting a nozzle on the end of the hose is to
  make the water that *does* comes out of the hose move faster (i.e. in meters
  per second). There's no analogue to this with electric circuits; forcing
  electrons through a resistor does not "spray" them out the other side.

The electrical analogue of this resistance is called, appropriately, `electrical
resistance <https://en.wikipedia.org/wiki/Electrical_resistance_and_conductance>`_,
measured in ohms (:math:`\Omega`). Any electrical component, be it a wire or a
light bulb or a purpose-built resistor, has an associated electrical
resistance; this is usually constant, though some components (e.g. transistors
and electric motors) have electrical resistances that vary with respect to some
external factor. The higher a component's resistance in ohms, the less current
that can pass through that component at a given fixed voltage.

Ohm's Law
---------

The effect that a given combination of voltage and resistance will have on a
basic circuit is given by Ohm's Law, generally stated as:

.. math::
  V = IR

Or, equivalently, through algebraic manipulation:

.. math::
  I &= V/R \\
  R &= V/I

Where :math:`V` is voltage, :math:`I` is current in amperes, and :math:`R` is
resistance in ohms.

.. TODO: add Ohms Law tutorial

Electrical loads and interpreting Ohm's Law
-------------------------------------------

One way to interpret a component's electrical resistance is as a measure of how
easily **electrical energy** will be *lost* as a current passes through. A
simple resistor (a component that does literally nothing except add some fixed
resistance in ohms to a circuit) dissipates electrical energy as waste heat; a
light-bulb will dissipate energy as both light and waste heat; an electric
motor "dissipates" energy as rotational motion. In all but the first case,
electrical energy is being used to "do something"; because energy is always
conserved, this "used" energy is removed from the circuit.

Because it's typically assumed that any high-resistance component of a circuit
is using the "lost" electrical energy for some useful purpose, such components
are usually called a `load <https://en.wikipedia.org/wiki/Electrical_load>`_.

Electrical shorts ("short circuiting")
--------------------------------------

All electrical components that aren't `superconductors <https://en.wikipedia.org/wiki/Superconductivity>`
have nonzero electrical resistance. This includes electric wire, though its
resistance is generally negligible and can be ignored in most calculations.

The electrical resistance of a length of wire typically only matters when the
circuit in question has no load. For example, rather than having a battery's
terminals wired to a lightbulb, we would have a battery where the plus-end is
wired directly to the minus-end.

This condition of having a voltage source connected directly to electrical ground
with no (or negligible) load in between is called a `short circuit
<https://en.wikipedia.org/wiki/Short_circuit>`_. In a short circuit, the only
"resistor" in the circuit is the wire connecting its components to each other.

To see why this is bad, consider a circuit powered by a :math:`1.5V` alkaline
battery whose terminals are connected by 1 foot of 22-gauge copper wire.
One foot of 22 AWG copper wire has a resistance of :math:`0.01614 \Omega`. So
using Ohm's Law, we can calculate that the total current through this circuit to be:

.. math::
  I = V/R = (1.5V)/(0.01614\Omega) = 92.94 A

*Ninety-three amperes* of current. In practice, it's unlikely that a common
alkaline battery will produce so much current (eventually other factors, like
the battery's cell chemistry, will dominate over Ohm's Law), but it will
produce *enough* current to produce a dangerous amount of heat, possibly
causing fires, or (in exceptional cases) causing the battery to explode.

Creating a short-circuit on accident is a common mistake when working with
small DC circuits. As we'll see, DC circuits built around an Arduino typically
draw current from its 5V power output pin, and run current into its ground
("GND") pin; **short-circuiting these will destroy the Arduino.**

As a side note, frying delicate electronics in this fashion is often (jokingly)
referred to as `"releasing the magic blue smoke." <https://en.wikipedia.org/wiki/Magic_smoke>`_
Electronics depend on the magic smoke being kept *inside*, so that they may
continue to provide Magic.

.. TODO: add tutorial on finding electrical shorts

.. .. topic:: In Summary,
..   -

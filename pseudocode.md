# Pseudocode: Doing Laundry

## Premise

We humans have problems. You could describe life as a series of problems. One is that, lacking the full body hair exhibited by many animals, we frequently find ourselves in environments that we find uncomfortably cool. For this and other reasons, he habitually wear clothes, which insulate us from the cold.

Another problem we have is that, just by being alive, we accumulate on our persons various substances and odors. In the normal course of functioning we frequently sweat, which creates a smell that others, and even ourselves, find unpleasant, and as we move through the world we can encounter things that get stuck to us, like mud, or pollen, or a spilt meal. In short, we become **dirty**. Fortunately, we are not trapped in this state; using baths and showers, or a body of freshwater in a pinch, we can instead become **clean**. 

Of course, solutions to one problem frequently come with their own challenges to deal with, and wearing clothes to live introduces the clothes to the hazards of our lives, including the dangers of becoming **dirty**. In fact, one of the other reasons we have for wearing clothes is to safeguard our bodies from dangerous, or just rankling, outside substances. But even without having to catch a (hopefully metaphorical) bullet for us, our garments become bogged down in our body's byproducts. Clothes, due to their proximity to our bodies, have the tendency to both induce sweating by warming us, and to absorb that sweat and take on its smell. And though we cleanse ourselves of our grime, we typically do so unclad, and should we return to the same vestments we find that they remain **dirty**. But again, if life is a series of problems, living is about being problem solvers, and the human animal has devised a solution, a way to make not just us but our clothes **clean**:

***Laundry.***

## How to do laundry

### Goal
We have 1 or more **dirty** articles of clothing. After doing laundry, some or all of the **dirty** clothes will be **clean**. What's **dirty** and what's **clean** is a matter of judgement and there's some nuance here, but I mostly see it being clothes that are stained, smelly, or just worn for too long are **dirty**, and clothes that have been washed and dried are **clean**.

### Objects & Variables

1. Clothes
   - Without clothes there is no laundry. There are a number of ways you can represent this; I'm thinking something like a LaundryBasket array to represent a collection of dirty clothes, though you might have a hamper or bag or just a shirt in your hands. You can just Pop the most recently added items out into the washer, or search the array for items that have specific properties, like a White Color or Woolen Material.
2. Washer and Dryer
   - Humans have been doing laundry probably for almost as long as we've been wearing clothes, but the modern person has at their disposal two handy tools to help simplify and expedite the process: the *washing machine* and the *dryer*. These fulfill a similar function to a bath and a towel for a human, but can operate on a larger number of clothes. They have a number of properties and methods; the salient ones are:
     - DrumIsFull: Washing machines and dryers have finite capacity. Articles of clothing have different sizes. You can describe the capacity of one of these machines by volume, but it's hard to translate that into number of clothes. This is instead a judgement on sight if there is space remaining or not. Ideally the washing machine and the dryer have similar capacities, but this might not be the case, so it's important to check in both stages.
     - SetCycle: This describes the pattern of washing/drying you want a machine to perform. It sets various properties, like RunTime, Temperature, SpinSpeed, and so on. Depending on the machine, this might actually be done with Set methods for individual properties.
     - Run: Starts a cycle if SetCycle has been completed
     - TimeRemaining: When a machine is running, this describes the amount of time until the machine's cycle is done.
3. Cleaning Agent(s)
   - In addition to the water that is the lifeblood of the washing process (and is provided automatically by a hooked up washing machine), we can employ a number of cleaners to improve the efficacy of the washing process. Chief among them and the only assumed one is detergent, which helps actually dissolve the stains/odor producers in the water. Other things that can be provided are bleach, useful for stained articles of clothing that are white, fabric softener and dryer sheets that can affect the texture and smell of laundered clothes, and various stain removers that can be applied to clothes before loading the washing machine. The amount of detergent to use is calculated after loading the washing machine but before starting it; other agents are options selected at various points of the laundry process. 

### Procedure

1. START CheckLaundry
2. IF (LaundryBasket is Full OR FavoriteSweater is Stained) AND FreeTime is Available
   - CALL Laundry
3. ELSE CheckTomorrow

   1. START Laundry
   2. INPUT LoadType (like LastIn to take from the top of LaundryBasket, or Whites)
   3. WHILE Washer is not Full AND Clothes in LaundryBasket is greater than 0
      - Remove an Article of clothing from LaundryBasket
      - IF Article meets condition of LoadType
        - Pre-Treat Article
          - IF Article has Pockets, empty them
          - IF Article has Stain, apply Detergent or INPUT other cleaning agent to apply to area
        - Load Article into Washer
      - ELSE set Article aside
   4. IF Articles were set aside
      - Return them to LaundryBasket
   5. CALL SetCycle for Washer based on LoadType
      - INPUT TimeNeededBy; IF less than 2 hours select SpeedWash
      - CASE LoadType of
        - LastIn: Probably PermanentPress
        - Blankets: Bulky
        - Delicates: Delicates
        - etc.
   6. COMPUTE amount of Detergent and add it to washer
   7. INPUT any other cleaning agents to add, like bleach or fabric softener
   8. CALL Run for Washer
   9. WHILE Washer has TimeRemaining
      - DO something else
   10. WHILE Dryer is not Full AND Clothes in Washer is greater than zero
       - Select an Article of clothing
       - IF Article has a stain still
         - Set aside to dry outside of the machine
         - Return to LaundryBasket when it is done
       - Place Article in Dryer
   11. CALL SelectCycle for Dryer
   12. INPUT any other cleaning agents to add, like dryer sheets or ball of aluminum foil
   13. CALL Run for Dryer
   14. WHILE Dryer has TimeRemaining
       - DO another something else
   15. Remove clothes from Dryer
   16. IF Clothes in Washer is still greater than zero, repeat steps 10-15 (Not a goto, let's call it LoadDryer or something)
   17. Store clothes 

Congratulations! You have one or more freshly **clean** loads of laundry. You can go out into the world looking good, smelling fine, and feeling a comfortable temperature for another day!

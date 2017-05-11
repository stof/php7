# Iterable Type

We're going to talk about another PHP 7.1 feature, iterable. I know, most of this tutorial is actually about PHP 7.1 features, not PHP 7. First, the setup. Open up your genus class. At the bottom, we're going to make a fun new function called bead, and we're going to be able to pass this function an array of food, and it's going to return a string that talks about this genus eating that food. We'll put some code here. If food equals 0, then we'll return a little string. This genus is looking at you in a funny way. Else, if we do pass something, we'll return that this genus recently ate a list of those foods. I'll use this arrow, get name, and then we'll use implode, and we'll implode that food. Cool, easy enough.

Next, we'll find show action, and we'll say food equals, how about, shrimp, clams, lobsters, and a shark, to make it a really interesting meal. Now, it passes a new variable that I [inaudible 00:01:46] recently ate. We'll say genus arrow feed, and we'll pass it that food. This renders genus/show.html.twig, which I'll open in my editor. We'll just print that stuff, so we can see it, under diet. We'll print recently ate. Cool.

Now, you have to go back to your show page and refresh. Not surprisingly, we see [A-ri 00:02:26] Elliot recently ate shrimp, clams, lobsters, shark. Okay, here's the deal. Suppose we're making this feed function, and maybe we're even making it inside of a reusable library, and we want to make it as flexible as possible. Right now, we are requiring this to be an array. It must be an array. Really, if you passed me anything that I could loop over, anything that I could for each over, we can make this function work. I could loop over the food and create my string down here.

I'm going to show you an example. In genus controller, I'm going to rename the variable food to food array, and then I'm going to say food equals new/array object, and I'll pass in food array. If you're not familiar with the array object, it's an object, but it looks and acts like an array. You can access keys off it like an array, and most importantly, you can for each over that. If we try that, it's going to throw a huge error. Argument one passed a feed must be an array object given. That makes sense, because that's the type that we have here.

It's kind of lame. Well, in PHP 7.1, since all what we really want is something we can loop over, we can change this to iterable. That's not a class name, that's a pseudo-type. Just like array is not a class name, it's a pseudo-type. Notice, PHP Storm doesn't like this. My version of PHP Storm still doesn't think that this exists in PHP. Oh well. It is valid.

Now, of course, as soon as we do that, we're going to get a different error. What we're passing into the vunction is iterable, so we don't get that error. It says, "Warning, implode, invalid arguments passed." Even though our function allows for an array or an iterable object, implode still requires the second argument to be an array. When you type hint with iterable, the only thing you're guaranteed is that you can loop over that. It's not even legal to count it like I am. If I want this to be more flexible, I need to rewrite it a little bit.

I'll create a new variable called food items equals array, and then I'm going to for each over food as food item. What I can do is I can just put those into my food items array. Now, we know that food items is an array. It's definitely legal to iterate over food. I'll just update the count to count food items, and down here we'll pass that to implode. Just like that, this function can accept any value that we can loop over. Our code works.

That is just a little bit more professional than before. I wouldn't necessarily do this in your code if you know you're always going to be passing an array. Don't go to the extra work of making it work with both of them, but if you are already looping over something and that's all you're doing with it, you can type hint it with iterable if you want to.

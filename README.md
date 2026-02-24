<!-- >>>>>>> -->
1. What is the difference between getElementById, getElementsByClassName, and querySelector / querySelectorAll?

Ans: 
getElementById: 

    >> The Vibe: The Sniper.

    >> How it works: It lokks for one specific element with a unique ID. Since IDs should only be used one per page, it's extremely fast.

    >> What it returns: A single element. If it doesn't find it, it returns null.

    >> Example: document.getElemetById('total-count') 

getElementByClassName:

    >> The Vibe: The Group Chat.

    >> How it works: It finds every element that has a specific class name.

    >> What it returns: An HTMLCollection. This looks like an array, but it’s "live"—meaning if you add another element with that class via code later, the collection updates itself automatically. Note: You can't use common array methods like .forEach() on this directly without converting it first.

    >> Example: document.getElementsByClassName('job-card') 

querySelector / querySelectorAll:

    >> The Vibe: The Swiss Army Knife.

    >> How it works: These are the most modern and flexible. They use CSS Selector syntax (the same stuff you use in your .css file).

        querySelector: Returns only the first match it finds.

        querySelectorAll: Returns a NodeList of all matches. Unlike an HTMLCollection, a NodeList is "static" (it doesn't change if the DOM changes later), but it does let you use .forEach() directly, which is why developers love it.

    >> Example: document.querySelector('.card > h3') or document.querySelectorAll('.btn-primary')

<!-- >>>>>>> -->
2. How do you create and insert a new element into the DOM?

ans: 
To create and insert a new element, here is 3 steps:

    1. Create: Use document.createElement('tagName') to generate the element in memory (e.g., const div = document.createElement('div');).

    2. Configure: Add content or styles using properties like .innerText, .innerHTML, or .classList.add().

    3. Insert: Attach it to the visible page using a method like .appendChild() (adds to the end) or .prepend() (adds to the beginning) on a parent element.

    Example: 
        JavaScript:
            const newTag = document.craeteElement('p');
            newTag.innerText = "New Job Added!";
            document.getElementById('container').appendChild(newTag);

<!-- >>>>>>> -->
3. What is Event Bubbling? And how does it work?

ans:
Event Bubbling is a process where an event starts at the specific element you clicked and then "bubbles up" to its parent elements one by one.

    How it works:

        1. Target: You click a child element (like a button inside your job card)

        2. Propagation: The event triggers on the button first, then move to its parent div, then the section, all the way up to the document.

        3. Capture: Any click listeners on those parent elements will also be triggered.

    Key Utility:

        Event Delegation: It allows you to put one listener on a parent to manage many children.

        To Stop it: Use event.stopPropagation() if you want the event to stay only on the child and not notify the parents.   

<!-- >>>>>>> -->
4. What is Event Delegation in JavaScript? Why is it useful?

ans:
Event Delegation is a design pattern where you attach a single event listener to a parent element instead of adding individual listeners to multiple child elements.

Why it is useful:

    1. Memory Efficiency: Instead of creating 100 listeners for 100 job cards, you only create one. This saves system memory.

    2. Dynamic Elements: If you add a new job card to the list via JavaScript, it will automatically have the click functionality because the parent is already "listening" for it. You don't have to manually bind a new listener.

    3. Cleaner Code: It simplifies your logic by centralizing event handling in one place.

<!-- >>>>>>>     -->
5. What is the difference between preventDefault() and stopPropagation() methods?

Ans:
preventDefault()

    1. The Job : It stops the browser's default action from happening.

    2. When to use it: Use this when an element has a built-in behavior that you want to cancel.

    3. Example: Stopping a form from refreshing the page when you click "Submit," or stopping a link from opening a new URL.

    The event still bubbles up the DOM; it just doesn't perform its "default" job.

 stopPropagation()

    1. The Job: It stops the event from bubbling up the DOM tree.

    2. When to use it: Use this when you have a click listener on a child (like a "Delete" button) and a click listener on the parent (the "Job Card"), and you don't want the parent's listener to trigger when the button is clicked.

    3. Example: Clicking a "Favorite" star inside a card without accidentally "opening" the card details.

<!-- >>>>>>>      -->
Scripts are written in **C#**.

When we open a script for a GameObject, we will find two functions:

```C#
void Start() {

}

void Update() {

}
```

The first `void Start()` is for any code that will run as soon as the script is enabled, and so it runs *once*.

The `void Update()` function runs *constantly* while the script is enabled and it will fire off every line of code, every single frame.

Scripts are used to **talk** to the game.
For example:

```C#
void Start() {
	gameObject.name = "Bob Birdington";
}
```

What we are doing here is:
- choosing to whom we want to talk to, `gameObject` for example
- choosing the topic of the conversation, `name` (after the 'dot', we're going to find all the "variables" of the inspector)
- how we want to change the name of the `GameObject` "Bird"

**Why we want to use the script, if we have the inspector?**
Initially, the script created can all talk to the first bit of the Inspector![[Screenshot 2025-05-07 at 08.34.17.png]]
and the "Transform" section.
At first, the script is completely unaware of other components of the `GameObject`.

We're trying to do a Flappy Bird, so we want to change the velocity of the bird on the y-axis.
So, we're going to create a [[Reference]] to the `Rigidbody2D` inside the `BirdScript`.

How to do so:
```C#
public class BirdScript: MonoBehaviour
{
	public Rigidbody2d myRigidbody; //here is the reference to the Rigidbody2D, and we set a name to it

	//existing code
	
}
```

![[Screenshot 2025-05-07 at 08.40.49.png]]
Ta-da! We have the reference to the Rigidbody 2D inside the Inspector.

To establish the link, drag the component Rigidbody2D (the one above the Script, with a green circle) inside "My Rigidbody".

```C#
if (Input.GetKeyDown(KeyCode.Space))
```

`Input` - we're talking about input of the player;
`GetKeyDown` - to detect the pressing of a key on the keyboard;
`KeyCode` - which key is pressed? --> `Space`!

---
Be careful to `GameObject` that has their velocity, but are not affected by gravity.
When we write code in `Update()`, be mindful that the code will run for each FPS, so we need to add [[Time.deltaTime]] to make things move at a constant speed, no matter the device is running the game on.

We don't need this for `GameObject` that are `Rigidbody` - so they obey to gravity - 'cause gravity has its own rules.

---
**Instantiate**: to spawn a new object in the game
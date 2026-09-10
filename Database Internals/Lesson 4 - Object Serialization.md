- Need to store/load an object between runs
- An instance of an object is:
	- the specific values of the instance variables (its state)
	- stored in a specific order somewhere in the heap
	- with a reference that tells you where to find the structure
- Easy if instance variables are all primitive values.
- If instance variable contains object references (aggregation), then the specific values of the aggregate objects are also part of the objects effective state.
- To store a complex object we must flatten it out and all the objects it knows about (and so on) to a "flat" savable representation.
- This process is known as serialization
- classes that implement `java.io.Serializable` can be serialized.

## Example: Deck of Cards
```Java
import java.io.Serializable;
public class Card implements Serializable {
	String suit;
	String rank;
	
	public Card (String suit, String rank){
		this.suit = suit;
		this.rank = rank;
	}// end constructor
	
	public String toString() {
		return (rank + " of " + suit+ "s");
	}
}// end class Card

// class header and state
public class Deck implements Serializable {
	static final String[] suitList = {"Club", "Diamond", "Heart", "Spade"};
	static final String[] rankList = {"Ace", "Two", "Three", ...}
	
	ArrayList<Card> cardList = new ArrayList<Card>();
}

// class methods
public Deck() {
	for (Stirng suit : suitList){
		for (String rank : rankList){
			cardList.add(new card(rank, suit));
		}// for rach rank
	}// for each suit
}// end constructor

public void show
```
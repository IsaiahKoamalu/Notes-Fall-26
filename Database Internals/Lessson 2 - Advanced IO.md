## Exceptions
- You cannot control everything
	- other users
	- available memory
	- file allocation
- Need to write a safe method to behave sanely even in possibility of failure under reasons out of control.
	- Exceptions: tell the calling code "Something bad happened. I failed."
	- Any method that takes a risk should declare the risk when you take it so that the failure can be dealt with if it occurs.
	- A try/catch block tells the compiler that you know you are calling something that might fail at run-time and what to do if it does fail.

## What is an Exception
- In Java, an exception is an object.
	- can make your own
- Generated (thrown) by methods that perform risky behavior
- Exceptions that are of type `RuntimeException` (or its subclass) are unchecked by the compiler.
- The compiler forces code to deal with all other types of exceptions

## Generating an Exception

```Java
public class RobotException extends Exception{
	public RobotException { super("Error: Bad robot!";) }
	// end class RobotException
}

pubic class RobotOnFireException extends RobotException{
} // end class RobotOnFireException

publc class CrazedRobotException extends RobotException{
} // end class CrazedRobotExcption

public void useRobot (Order order) throws RobotException {
	boolean taskPerformed = giveRobotOrder(Order order);
	if (!taskPerformed()){
		if (isRobotOnFire()){
			throw new RobotOnFireException();
		}
		if (RobotIQ > 200) { throw new CrazedRobotException(); }
	}
} // end useRobot
```
- Exceptions declare a problem they do not handle/fix it, that is for the person who called the code to deal with.

## Stack Trace
```
Exception in thread "main"
java.lang.StringIndexOutOfBoundsException:
	String index out of range: 3
		at java.lang.String.charAt(Unknown Source)
		at coordinate.getStatus (Coordinate: 67)
		at Ship.
```

## Binary Files
- Text files
	- all data is stored in character format (UNICODE, ASCII, etc).
	- number 4 stored as one character '4'
	- number 10000000 is stored as 8 characters '1' '0' '0' ... '0'
	- each character is 16-bits in unicode
- Binary files
	- all data stored in "raw binary" format (as in computer memory)
	- number 4 is stored as one 32-bit value
	- far more efficient (few conversions, usually less space)
	- Some things have no text equivalent (images, etc)

## Writing to Binary Files
```Java
import java.io.FileOutputStream
import java.io.DataOutputStream
...
	public void storeToFile(ArrayList<Integer> numberList){
		try{
			FileOutputStream fs = new FileOutputStream(filename);
			DataOutputStream output = new DataOutputStream(fs);
			for (int number : numberList){
				output.WriteInt(number);
			}
			output.close();
		} catch(Exception ex) {
			ex.printStackTrace();
		}
	}// end method storeToFile
```

## Reading from a Binary File
```Java
import java.io.FileInputStream;  
import java.io.DataInputStream;  
...  
	public ArrayList<Integer> readFromFile() {  
		ArrayList<Integer> numberList = new ArrayList<Integer>();  
		boolean endOfFile = false;  
		try {  
			FileInputStream fs = new FileInputStream(filename);  
			DataInputStream input = new DataInputStream(fs);  
			while (!endOfFile) {  
			numberList.add( input.readInt() );  
			}  
		} catch (Exception ex) {  
			if (ex instanceof EOFException) { endOfFile = true; }  
			else {ex.printStackTrace();}  
		}  
		input.close();  
	} // end method readFromFile
```

## Random Access File
- Sequential access
	- opening a file sets the file pointer to byte 0
	- reading/writing advances the file pointer the correct number of bytes
- Random access
	- opening a file sets the file pointer to byte 0
	- reading/writing advances the file pointer the correct number of bytes
	- the file pointer can be changed without reading.
- Class RandomAccessFile
	- opens files for read, read/write
	- mode "r" Read
	- mode "w" Write

## Serializing Objects
- Need to be able to store/load an object between runs
- An instance of an object is really just: 
	- the specific values of the instance variables (its state)
	- stored in a specific order somewhere in the heap
	- with a reference that tells you where to find the structrue
- If the instance variables are all primitive values, this is easy.
- 
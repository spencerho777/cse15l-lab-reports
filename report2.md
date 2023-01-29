

# Lab Report 2 - Servers and Bugs

In this blog post, I will demonstrate how to run a server on the local host that has behavior based on queries, and also run through debugging practices

## String Server
This is my code for StringServer.java:
```
import java.io.IOException;
import java.net.URI;

class StringHandler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    StringBuilder str = new StringBuilder();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return str.toString();
        } else if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    str.append("\n" + parameters[1]);
                }
                return str.toString();
        }
        return "404 Not Found!";
    }
}
class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }
        int port = Integer.parseInt(args[0]);
        Server.start(port, new StringHandler());
    }
}
```

This is almost a replica of our NumberServer with a couple of changes. Firstly, we are keeping track of a StringBuilder variable instead of a integer, and we only have 2 path options: `/` and `/add-message`
After a ‘javac StringServer.java` and `java StringServer 3000`, our server is up and running.
Our first run gives us this:

![add-screen1 example](/assets/report2/add-message1.png)

In this screenshot, the method `handleRequest(URI url)` was called which takes a variable `url` which is the url of the page we are accessing. In this case, the value of this field is `http://localhost:3000/add-message?s=What is love? Baby don't worry x10`. This will update the StringBuilder variable `str` by appending a “\n” newline and the String value after the equals sign. It finishes by returning this new value. In this case, it returns “\nWhat is love? Baby don't worry x10”.

Our second run:

![add-screen2 example](/assets/report2/add-message2.png)

In this screenshot, the method `handleRequest(URI url)` was called which takes a variable `url` which is the url of the page we are accessing. In this case, the value of this field is `http://localhost:3000/add-message?s=huh?`. This will update the StringBuilder variable `str` by appending a “\n” newline and the String value after the equals sign. It finishes by returning this new value which is “\nWhat is love? Baby don't worry x10\nhuh?”.

## Debugging
The following code produces a failure for ListExamples.filter(list, sc).
```
class TestStringChecker implements StringChecker {
    @Override
    public boolean checkString(String s) {
        if (s.charAt(0) == 'a') { return false; }
        return true;
    }
}
public class ListTests {
	@Test 
	public void testFilter() {
        List<String> testList = Arrays.asList("a", "b", "c");
        TestStringChecker tsc = new TestStringChecker();
        String[] expected = {"b", "c"};
        assertArrayEquals(expected, ListExamples.filter(testList, tsc).toArray());
	}
}
```
Running this produces the symptom:
![input1 symptom](/assets/report2/input1symptom.png)

The following code does *not* induce a failure:
```
class TestStringChecker implements StringChecker {
    @Override
    public boolean checkString(String s) {
        if (s.charAt(0) == 'a') { return false; }
        return true;
    }
}
public class ListTests {
	@Test 
	public void testFilter() {
        List<String> testList = Arrays.asList("a", "b");
        TestStringChecker tsc = new TestStringChecker();
        String[] expected = {"b"};
        assertArrayEquals(expected, ListExamples.filter(testList, tsc).toArray());
	}
}
```
Running this test produces no symptom as the test passes:

![input2 symptom](/assets/report2/input2symptom.png)

The bug can be found on line 15 of ListExamples.java.
Lines 13-15 read:
```
if(sc.checkString(s)) {
        result.add(0, s);
      }
```
Which **inserts** the element into the first position, effectively reversing its order. To fix this, we simply need to get rid of the index in result.add, resulting in
```
if(sc.checkString(s)) {
        result.add(s);
      }
```
This will **append** the input to the end of the list and give us the correct output.

## Takeaways
In week 2, I learned what a URL truly means and the many parts to its structure. When I look in the top bar of my search engine, I can now pick apart the domain, the path, and the query, separated by “/”s and “?” respectively. Now I know why these elements exist and how programs can parse a URL and decide behavior based on it.


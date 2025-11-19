# Flattening a Nested List Using an Iterator
## DATE:
## AIM:
To design and implement a class NestedIterator that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (next() and hasNext()).
## Algorithm
```text
1. Start
2. Create an empty list called result
3. Call the function flattenList(nestedList)

4. In the function flattenList(nestedList):
   4.1 For each element in nestedList:
       a) If the element is an Integer:
              i) Add the element to result
       b) Else if the element is a List:
              i) Recursively call flattenList on this element (cast as List<Object>)
              ii) Add all returned integers into result

5. After flattenList finishes, result contains all integers from the nested list in order
6. Print or use the list result
7. End
```

## Program:
Program to find Flattening a Nested List Using an Iterator
```java
import java.util.*;

public class FlattenNestedListSimple {
    public static List<Integer> flattenList(List<Object> nestedList) {
        List<Integer> result = new ArrayList<>();
        for (Object element : nestedList) {
            if (element instanceof Integer) {
                result.add((Integer) element);
            } else if (element instanceof List) {
                result.addAll(flattenList((List<Object>) element));
            }
        }
        return result;
    }

    public static void main(String[] args) {
        List<Object> nestedList = new ArrayList<>();
        nestedList.add(1);
        nestedList.add(Arrays.asList(2, Arrays.asList(3, 4), 5));

        System.out.println("Original Nested List: " + nestedList);

        List<Integer> flattened = flattenList(nestedList);

        System.out.println("Flattened List: " + flattened);
    }
}
```
Developed by: THILAK RAJ . P  
RegisterNumber:  212224040353


## Output:

<img width="442" height="108" alt="image" src="https://github.com/user-attachments/assets/7079b91d-bbe5-4c37-931c-4a8ce8fa2698" />


## Result:
The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.

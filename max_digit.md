```java

import java.util.*;

class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int num = sc.nextInt();
// List<Integer> lst = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6, 5);
        List<Integer> lst = new ArrayList<>();

        while (num != 0) {
            int digit = num % 10;   // get last digit
            lst.add(digit);        // store in list
            num = num / 10;        // remove last digit
        }

        // Collections.reverse(lst);  // optional: to keep original order

        // System.out.println(lst.size());
        
        int maxNumber = Collections.max(lst); // Correct usage
        System.out.println("Maximum number: " + maxNumber);
        
        
        sc.close();
    }
}

```

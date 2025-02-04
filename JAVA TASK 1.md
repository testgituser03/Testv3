
### **Basic Level**
**1. Basic Arithmetic Operations**
```java
public class BasicArithmetic {
    public static void main(String[] args) {
        int a = 10, b = 5;
        System.out.println("Sum: " + (a + b));
        System.out.println("Difference: " + (a - b));
        System.out.println("Product: " + (a * b));
        System.out.println("Quotient: " + (a / b));
    }
}
```

---

### **Average Level**
**1. Modulus Operator**
```java
public class ModulusExample {
    public static void main(String[] args) {
        int num1 = 10, num2 = 3;
        System.out.println("Remainder: " + (num1 % num2));
    }
}
```

**2. Float and Double Operations**
```java
public class FloatDoubleExample {
    public static void main(String[] args) {
        float f = 5.5f;
        double d = 3.3;
        System.out.println("Sum: " + (f + d));
        System.out.println("Difference: " + (f - d));
    }
}
```

---

### **Intelligent Level**
**1. Swap Without Third Variable**
```java
public class SwapVariables {
    public static void main(String[] args) {
        int a = 5, b = 10;
        System.out.println("Before swap: a = " + a + ", b = " + b);
        a = a + b;
        b = a - b;
        a = a - b;
        System.out.println("After swap: a = " + a + ", b = " + b);
    }
}
```

**2. Ternary Operator for Largest of Three**
```java
public class TernaryLargest {
    public static void main(String[] args) {
        int x = 10, y = 20, z = 15;
        int largest = (x > y) ? (x > z ? x : z) : (y > z ? y : z);
        System.out.println("Largest: " + largest);
    }
}
```

---

### **Tough Level**
**1. Check Even/Odd Without Modulus**
```java
public class EvenOddWithoutModulus {
    public static void main(String[] args) {
        int num = 7;
        if ((num & 1) == 0) System.out.println(num + " is even.");
        else System.out.println(num + " is odd.");
    }
}
```

**2. Type Promotion in Arithmetic**
```java
public class TypePromotionExample {
    public static void main(String[] args) {
        byte b = 2;
        short s = 10;
        int i = 100;
        int result = b + s + i;
        System.out.println("Result: " + result);
    }
}
```

---

### **Experienced Level**
**1. Count Set Bits**
```java
public class CountSetBits {
    public static void main(String[] args) {
        int num = 15, count = 0;
        while (num > 0) {
            count += num & 1;
            num >>= 1;
        }
        System.out.println("Set bits: " + count);
    }
}
```

**2. Shift Operators Demo**
```java
public class ShiftOperatorsDemo {
    public static void main(String[] args) {
        int a = 8;
        System.out.println("Left shift by 2: " + (a << 2));
        int b = -8;
        System.out.println("Signed right shift: " + (b >> 2));
        System.out.println("Unsigned right shift: " + (b >>> 2));
    }
}
```

**3. String vs StringBuilder**
```java
public class StringVsBuilder {
    public static void main(String[] args) {
        // String concatenation
        String str1 = "Hello", str2 = "World";
        String concatStr = str1 + ", " + str2 + "!";
        System.out.println(concatStr);

        // StringBuilder concatenation
        StringBuilder sb = new StringBuilder();
        sb.append("Hello").append(", ").append("World").append("!");
        System.out.println(sb);
    }
}
```

---

### **Research Level**
**1. Matrix Multiplication**
```java
public class MatrixMultiplication {
    public static void main(String[] args) {
        int[][] a = {{1, 2, 3}, {4, 5, 6}};
        int[][] b = {{7, 8}, {9, 10}, {11, 12}};
        int[][] result = new int[a.length][b[0].length];

        for (int i = 0; i < a.length; i++) {
            for (int j = 0; j < b[0].length; j++) {
                for (int k = 0; k < a[0].length; k++) {
                    result[i][j] += a[i][k] * b[k][j];
                }
            }
        }

        // Print result
        for (int[] row : result) {
            for (int val : row) System.out.print(val + " ");
            System.out.println();
        }
    }
}
```

**2. Overflow/Underflow Demo**
```java
public class OverflowUnderflow {
    public static void main(String[] args) {
        int maxInt = Integer.MAX_VALUE;
        System.out.println("Max int: " + maxInt);
        System.out.println("Overflow: " + (maxInt + 1));

        float maxFloat = Float.MAX_VALUE;
        System.out.println("Max float: " + maxFloat);
        System.out.println("Float overflow: " + (maxFloat * 2));
    }
}
```

**3. Division Operator Behavior**
```java
public class DivisionExample {
    public static void main(String[] args) {
        int a = 5, b = 2;
        double c = 5.0, d = 2.0;
        System.out.println("int division: " + (a / b)); // 2
        System.out.println("double division: " + (c / d)); // 2.5
    }
}
```

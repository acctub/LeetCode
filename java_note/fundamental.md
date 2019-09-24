# Fundamental

### Print array

```java
int[][]Matrix =
 {
	 {16,3,2,13},
	 {5,10,11,8},
	 {9,6,7,3}
 };
 
 >>Matrix[0] = &{16,3,2,13}
 
 //for each
 for(int[] i:Matrix){
     for(int j:i)
         System.out.print(j+" ");
     System.out.println();
 }
 
 //Using toString
 for(int i = 0; i < Matrix.length; i++)
     System.out.println(Arrays.toString(Matrix[i]));
```


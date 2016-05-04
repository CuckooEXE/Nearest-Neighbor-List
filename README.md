# Nearest-Neighbor-List
Nearest Neighbor List for LAMMPS in FORTRAN
---



#bruteNNL.f03
Runtime: O(n^2)

Program Explanation:
  The program asks the user for an input file and a lattice parameter. After that, it reads in all atom coordinate data from the input file. To test if an atom is a nearest neighbor without using the square root operator, you just have to test the squares. Because '(n+1)^2' is always larger than '(n)^2', we can deduce that if 'dx^2 + dy^2 + dz^2 < lattice^2' (where dx, dy, and dz is the difference in the coordinates of two atoms and lattice is the lattice parameter) that the two atoms are nearest neighbors. 
  
To do:
  - Account for periodic boundaries
  - Fix actual values for distances
  - See how it scales in O(n^2)
  
---


#sortedNNL.f03
Runtime: O(n*k)

Program Explanation:
  The program asks the user for an input file and a lattice parameter. After that, it reads in all atom coordinate data from the input file. It sorts the data by changing the index and the value stored at that index in the array that holds data. Then it shrinks the array to destroy all non-valued elements of the function. From there the program will only check atoms in the array that can possibly exist inside the interaction radius by looking at the bounds. An atom will never be a nearest neighbors if one of its cordinates is greater than +- another atom's interaction radius.
  
To do:
  - Account for periodic boundaries
  - Fix lost data in sorting
  - Implement nearest neighbor checking
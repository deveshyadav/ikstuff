Recursion Part - 1

Key Takeaways

Choose recursion if you are following a div-conq strategy [MULTIPLE SUBPROBLEMS]
Choose iteration if you are following a dec-conq strategy [ONE SUBPROBLEMS]

sum(2^i) i -> [0..n] = 2^(n+1) - 1

Space Complexity proportional to the height of the tree (look at the size of each activation record)
Time complexity proportional to the no of nodes in the tree (look at work done per function)

General Template

Def helper(subproblem, slate):
	If subproblem == empty:
		print(slate)
		Return

	For c1, c2, c3 … ck (the list of choices):
		New_subproblem = subproblem - {ci}
		New_slate = slate + {ci}
		helper(new_subproblem, new_slate)


Leaf Node:
	Receives the entire solution
	Print / appends / returns

Internal Node:
	Takes a series of choices. For each choice:
		Decrease the problem
		Increases the solution

Permutations 
https://leetcode.com/problems/permutations/  

class Solution(object):
   def helper(self, nums, slate, result):
       if len(nums) == 0:
           result.append(slate)
           return
      
       for i in range(0, len(nums)):
           # nums[i] is the choice


           new_nums = nums[:]
           new_nums.pop(i)


           new_slate = slate + [nums[i]]


           self.helper(new_nums, new_slate, result)


   def permute(self, nums):
       result = []
       self.helper(nums, [], result)
       return result
      

No of nodes

#leaf = O(n!)
#internal = O(n.n!)

work/leaf = O(1)
work/internal = O(n^2)

TC = O(n^3. n!)

Height = n+1
N AR are internal nodes (each taking O(n))
1 AR for leaf node (O(1))

SC = O(n.n + 1.1) = O(n^2)
Letter Case Permutations (Optimized)

class Solution(object):
   def helper(self, S, i, slate, result):
       if i == len(S):
           result.append(''.join(slate))
           return
      
       if S[i].isdigit():
           slate.append(S[i])
           self.helper(S, i+1, slate, result)
           slate.pop()
       else:
           slate.append(S[i].lower())
           self.helper(S, i+1, slate, result)
           slate.pop()


           slate.append(S[i].upper())
           self.helper(S, i+1, slate, result)
           slate.pop()


   def letterCasePermutation(self, s):
      result = []
      self.helper(s, 0, [], result)
      return result

No of nodes
#leaf = O(2^n)
#internal = O(2^n)

work/leaf = O(n)
work/internal = O(1)
TC = O(n. 2^n)

Height = n+1
N AR are internal nodes (each taking O(1))
1 AR for leaf node (taking O(n) space)

SC = O(n.1 + 1.n) = O(n)

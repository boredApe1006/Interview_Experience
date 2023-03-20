# Google_Interview_Experience

## There were 3 rounds in total.
Had an online assessment which has 2 questions to be solved in 60 mins. Solved both. 40 students (19 boys + 21 girls)from my college were selected for interviews.
# Round 1 (45 mins DSA + 15 mins googlyness)
The interviewer started with we have a connected graph with some infected nodes. 1) Given a source node and a destination find if a path exists from the source node to destination without visiting any infected nodes. 2) If yes find the length of the shortest path from source to destination. She just wanted to know the approach. I told the BFS approach.
Then the follow up was now every infected node has a same virality factor. Definition of Virality factor is that let's suppose virality factor is 2 so all nodes which are at distance 2 or less from any of the infected nodes should also not be visited. Now again same questions. I told the multisource BFS approach and coded it. Find all set of nodes which can not be visited using multisource bfs and then again run bfs from source to destination. Time compexity O(V + E) due to multisource bfs.
Similar logic : https://leetcode.com/problems/rotting-oranges/
Next follow up was now every infected node has a different virality factor. Again same both question. I told a approach using max priority queue similar to what we do in dijkstras. In priority queue I pushed all the {initial virality factor and the infected node} in priority queue using a a pair and found maximum virality factor for all non infected nodes using dijkstras like approach. If the virality factor is positive for non infected node so that means we can not visit it. Otherwise we can visit it. Then do a bfs from source node using the nodes of virality factor <= 0.
Coded it quickly as less time was left. This round went good. The interviewer seemed satisfied.
Next 15 min were behavioural questions like the time when you were stuck on a project. Then what you did to unblock ? and How will you ensure whether your product is not biased to a particular community or not ? How will you work with team mates with different opinions than yours ?







# Round 2: (45 mins DSA + 15 mins googlyness)
You have an array of with n building. ith building has arr[i] number of floors in it. You can reduce as many number of floors from any building. The cost of reducing 1 floor is 1. If you remove all floors from the ith building so the final height of that building will be 0, which is considered as free space and will not be considered a building now(read test case 1 for why this condition is given). You have to make height of all buildings equal in final array with minimum cost.
Test case one [2,4,5] : min cost => 3. Remove 2 from the 0th index and 1 from the 2nd index. Final array => [0,4,4] with cost 2.
Clarification on test case : One quick solution which can come to your mind is to make height of every building equal to minimum height but this will give WA in test case one. as cost of [2,2,2] from [2,4,5] is 0 + 2 + 3 = 5 is more than cost of [0,4,4].
Solution : The final array will have some zeros and some equal non zero elements like [0,x,0,x,x,0]. One important observation is that final value x will always be one of the ith building height. For [3,7,11,15,17] , the final building height will be one among 3, 7 ,11 ,15, 17. If the final building height is 11 so we will have to reduce 3 7 to 0 as we can not increase the height and reduce 15 17 to 11. So we can sort the array the calculate if the final height is the ith value then what is the current cost using prefix sum and suffix sums. Coded it quickly. Time Complexity O(nlogn) due to sort and space optimized to 0(1).
Follow up : Optimize time complexity can take extra space.
As I was using inbuilt sort so I asked the interviewer what are the constraints of arr values. He told assume the max height to be m present in the array. So rather than normal sorting I approached it similar to count sort. Using an temp array , temp[i] denotes building with height i is present temp[i] times in the original array. Coded this too. Time Complexity 0(max(n,m)), space complexity O(m).
Next follow up was :
Now there can be two different non zero building heights in the final array. So the final state will be [0,0,0,x,y,y,y]. Explained the approach using the the previous method only but was not able to code it due to less time. Interviewer had poker face the whole time so didn't knew whether the approach was right or wrong for this question. This round went average.
Then 15 min googlyness round : He asked on my ongoing intern project. Whether you had any difference in opinion with other people and other questions which now I don't remember.





# Round 3 : 45 mins DSA
This was the best round. The interviewer was very chill and we matched vibe from the start.
You have a N * N chessboard. Every cell of a chessboard has a integer written on it. You have to find the length of the longest path. The path is defined as : If you are standing at cell (i,j) you can move to a cell(x,y) if and only if either (x == i) or (y == j) i.e. it should share a row or a column with the previous cell (like rook in chess) and the new cell value must be greater than the previous value. You can start at any cell and can end at any cell.
Eg
8 6 10
9 2 3
1 4 11

The ans will be 6 (1->4->6->8->10->11)
Solution. Its basically dp on directed acyclic graph. If we can move from cell a to b then we can not move from b to a due to the strictly increasing condition. So we can model it into a graph problem and we have to find the longest path in DAG.
Very similar to https://leetcode.com/problems/longest-increasing-path-in-a-matrix/ Only the transitions will be changed as here rather than adjacent I can move to any cell in the same row or same column with greater value. Time Complexity(N^3). N^2 for states and order N for transitions so total will be N^2 * N == N^3. Space Complexity 0(N^2) . Coded it quickly.
The interviewer then said I will not waste your time by asking to print the longest path because I know you can do that.
Then he told that a more optimized solution exists for this problem. Let's try to code that together.
Took me 5 more mins to come up with the N^2 log(N) solution. Make a vector of <cell value, cell row no, cell col no> and sort it in decreasing order of cell value. Now if you are on ith value on this the decreasing order than all values greater than the ith value are already visited. So i maintained 2 vectors rowVector(n) and colVector(n). rowVector[i] will tell the length of the longest path starting from the ith row. Similarly colVector[i] will tell the length of the longest path starting from the ith col. So for the ith value if row and col no is (r,c). Its ans will the 1 + max(rowVector[r],colVector[c]). Now we will update rowVector[r] = colVector[c] = ans. We have to handle the case for equal values by first computing ans for all equal values and then updating their ans for all same values simultaneously. Coded it properly. Time Complexity 0(N^2 log(N)) and space complexity O(N). This round went very good. Had a good feeling after this round.

Got the results after 2 days. I was finally selected at Google India SWE.

Prep : Started with DSA course from coding ninjas in my first sem. Then did their Competitive Programming Course and participated in codechef long challenges in first year. Didn't saw much improvement in my skills. Started practicing on codeforces and gave contests on codeforces and atcoder. Reached 1800 on codeforces by the end of 2nd year. From third year I practiced more on leetcode and used to give contest on codeforces to keep it touch with CP skills. Learnt a lot of algos on leetcode. Reached Candidate Master on codeforces in March 2022 finally. Then used a leetcode premium acount from my friend and speed runned through all google asked questions in last 6 months.

Thank you !!

class Solution {

  public int[] findOrder(int numCourses, int[][] prerequisites) {

​    int[] indegree = new int[numCourses];

​    List<List<Integer>> graph = new ArrayList<>();

​    

​    for (int i = 0; i < numCourses; i++) {

​      graph.add(new ArrayList<>());

​    }

​    for (int[] p : prerequisites) {

​      int a = p[0];

​      int b = p[1];

​      graph.get(b).add(a);

​      indegree[a]++;

​    }

​    Queue<Integer> queue = new LinkedList<>();

​    for (int i = 0; i < numCourses; i++) {

​      if (indegree[i] == 0) {

​        queue.offer(i);

​      }

​    }

​    int[] res = new int[numCourses];

​    int index = 0;

​    while (!queue.isEmpty()) {

​      int cur = queue.poll();

​      res[index++] = cur;

​      for (int next : graph.get(cur)) {

​        indegree[next]--;

​        if (indegree[next] == 0) {

​          queue.offer(next);

​        }

​      }

​    }

​    if (index == numCourses) {

​      return res;

​    }

​    return new int[0];

  }

}
---

title: "Graph에 대하여"
comments: true
header:
  teaser: "http://drive.google.com/uc?export=view&amp;id=1kvqN8dv10vdgY9CN9Nt8scugwabkURAp"
categories:
  - data structure
tags:
  - algorithm
  - graph
show_date: true
last_modified_at: 2020-08-28
toc: true
toc_sticky: true
toc_label: 목차
---

## GRAPH란?

그래프 알고리즘은 수학자 '오일러'에 의해 고안되었다고 한다.

수학 문제를 풀다가 한번쯤 마주쳤을 법한 문제인 '쾨니히스베르크의 다리 문제'를 풀기 위해 그래프 이론을 사용했다고 한다.

문제 : <cite>모든 다리를 한 번씩만 건너서 처음 출발했던 장소로 돌아올 수 있는가?</cite>

![쾨니히스베르크의 다리 문제](https://upload.wikimedia.org/wikipedia/commons/5/5d/Konigsberg_bridges.png "쾨니히스베르크의 다리 문제")



그래프에는 __정점__ 과 __간선__ 이 있다.

<img src="http://drive.google.com/uc?export=view&amp;id=1wfhOOrFE7oTFi4AX4giZ-Sq7I5Yc8tm1" alt="그림" style="zoom:50%;" />





__정점__ 은 Node, Vertex라고 불리고

__간선__ 은 Edge라고 불린다.



'정점'은 연결의 대상이 되는 __개체__ 또는 __위치__ 를 의미하고

'간선'은 __정점__ 간의 __관계__ 를 나타낸다.

___

## GRAPH의 종류

그래프는 __방향 그래프__, __무방향 그래프__ 가 있다.



* 방향 그래프(Directed Graph) : 간선에 방향이 있다. digraph라고도 한다.

  <img src="http://drive.google.com/uc?export=view&amp;id=1oAb8A--5JdglG9alXaAiwQQBFyzmaHpk" style="zoom:50%;" />



* 무방향 그래프(Undirected Graph) : 간선에 방향이 없다. 양방향 그래프(Bidirection Graph)라고도 함.

  * 1-3인 경우, 1->3과 3->1로 저장해야 한다.

    <img src="http://drive.google.com/uc?export=view&amp;id=1xYggFVHiw50LAi0TfgHSXMIBLFr8bPSj" style="zoom:50%;" />



그리고 __방향/무방향 그래프__ 는 간선의 연결 형태에 따라 __완전 그래프__ 로 구분이 된다.



* 완전 그래프 : 각각의 정점에서 다른 모든 정점을 연결한 그래프

  <img src="http://drive.google.com/uc?export=view&amp;id=1FrWADmqD1yL0OtJ36TxPpqpk9f6T3RJ7" alt="완전" style="zoom:50%;" />

  <img src="http://drive.google.com/uc?export=view&amp;id=1t1PnW05kQib96JSsURkvzZ6nW8DhfsbR" alt="완전_방향" style="zoom:50%;" />



* 추가

  * 두 정점 사이에 간선이 여러 개일 수도 있다.

    <img src="http://drive.google.com/uc?export=view&amp;id=1KmcMODFAtkqHZWl_rKwyufeek-j9wvuZ" style="zoom:50%;" />

  * 간선의 양 끝점이 같을 수도 있다.(루프)

    <img src="http://drive.google.com/uc?export=view&amp;id=19o5gKm3e5pwpRNNQRLdPhph0HL1vLCvh" style="zoom:50%;" />



간선에 __가중치__ 정보를 제공하여 그래프를 구성 할 수도 있다.

가중치가 없는 경우에는 가중치가 '1'이라고 생각하면 된다.

<img src="http://drive.google.com/uc?export=view&amp;id=1D6kLxGspvuEpGdEmlsTrDxvD0U2Gs25O" style="zoom:50%;" />

__가중치__ 는

* 한 정점에서 다른 정점으로 이동하는데 소요되는 시간, 소모 비용, 거리 등이 될 수 있다.

___

## Graph에서 사용하는 용어

1. 경로

   1. 한 정점(시작점)에서 다른 정점(도착점)으로 가는 연속된 간선들.

   2. __최단 경로__ 가 중요하다.

      <img src="http://drive.google.com/uc?export=view&id=1pVQJ3DYTVmU8XB_UH98jJXB_I36x7Scw" style="zoom:50%;" />

       * 정점 1에서 5까지 가는 경로
          * 1 -> 2 -> 3 -> 4 -> 5
          * 1 -> 2 -> 4 -> 5
          * 1 -> 3 -> 4 -> 5
          * 1 -> 3 -> 5
          * 1 -> 4 -> 5

   3. __단순 경로__

      * 같은 정점을 두 번 이상 방문하지 않는 경로다.

2. 사이클
   1. 시작점과 도착점이 같은 경로

      <img src="http://drive.google.com/uc?export=view&amp;id=1kvqN8dv10vdgY9CN9Nt8scugwabkURAp" style="zoom:50%;" />

       *  정점 3에서 다시 3으로 돌아오는 경로
          	*  3 -> 4 -> 1 -> 2 -> 3
              	*  3 -> 4 -> 1 -> 3

   2. __단순 사이클__

      * 같은 정점을 두 번 이상 방문하지 않는 사이클이다.

3. 차수

   1. 정점과 연결되어 있는 간선의 개수를 나타낸다.

        <img src="http://drive.google.com/uc?export=view&amp;id=1Z3YKlp_-KTX0fVvfiKrB5Qa7OHjalEeB" style="zoom:50%;" />

      * 정점 3의 차수 : 4
      * 정점 5의 차수 : 2

   2. 방향 그래프의 경우

      * In-degree(들어오는)와 Out-degree(나가는)로 나누어서 계산.

         <img src="http://drive.google.com/uc?export=view&id=1pVQJ3DYTVmU8XB_UH98jJXB_I36x7Scw" style="zoom:50%;" />

        * 4의 In-degree : 3
        * 4의 Out-degree : 1

___


## 그래프의 표현

그래프는 __인접 행렬(adjacent matrix)__ 혹은 __인접 리스트(adjacent list)__ 를 이용해서 표현 할 수 있다.



### 인접 행렬

​	정점의 개수를 V라고 했을 때, V×V 크기의 이차원 배열을 이용한다.

​	<img src="http://drive.google.com/uc?export=view&amp;id=1Z3YKlp_-KTX0fVvfiKrB5Qa7OHjalEeB" style="zoom:50%;" />

|       |  1   |  2   |  3   |  4   |  5   |
| :---: | :--: | :--: | :--: | :--: | :--: |
| __1__ |  0   |  1   |  1   |  1   |  0   |
| __2__ |  1   |  0   |  1   |  0   |  0   |
| __3__ |  1   |  1   |  0   |  1   |  1   |
| __4__ |  1   |  0   |  1   |  0   |  1   |
| __5__ |  0   |  0   |  1   |  1   |  0   |

​	이처럼 정점을 연결하는 간선이 __있는 경우에는 1__ , __없는 경우에는 0__ 으로 나타낸다.



 #### * 가중치 그래프인 경우

​	<img src="http://drive.google.com/uc?export=view&amp;id=1IrI1j0ZEn8ePGwJ30nRcwXPcGXI2cH8x" style="zoom:50%;" />

|       |  1   |  2   |  3   |  4   |  5   |
| :---: | :--: | :--: | :--: | :--: | :--: |
| __1__ |  0   |  1   |  6   |  3   |  0   |
| __2__ |  1   |  0   |  5   |  0   |  0   |
| __3__ |  6   |  5   |  0   |  4   |  2   |
| __4__ |  3   |  0   |  4   |  0   |  3   |
| __5__ |  0   |  0   |  2   |  3   |  0   |

​	v 정점에서 x 정점의 가중치를 넣어주면 된다.



### 인접 리스트

​	정점 V와 연결된 정점들을 리스트로 표현한다.

​	<img src="http://drive.google.com/uc?export=view&amp;id=1Z3YKlp_-KTX0fVvfiKrB5Qa7OHjalEeB" style="zoom:50%;" />

​			__A[1]__	2	3	4

​			__A[2]__	1	3

​			__A[3]__	1	2	4	5

​			__A[4]__	1	3	5

​			__A[5]__	3	4

		* 이때, 저장된 정점의 순서는 중요하지 않다.
		* 리스트의 크기는 동적으로 변경할 수 있어야 하므로 C++의 vector나 JAVA의 ArrayList가 구현에 용이하다.



#### 	* 가중치 그래프인 경우

​	<img src="http://drive.google.com/uc?export=view&amp;id=1IrI1j0ZEn8ePGwJ30nRcwXPcGXI2cH8x" style="zoom:50%;" />

​			__A[1]__	(2,1)	(3,6)	(4,3)

​			__A[2]__	(1,1)	(3,5)

​			__A[3]__	(1,6)	(2,5)	(4,4)	(5,2)

​			__A[4]__	(1,3)	(3,4)	(5,3)

​			__A[5]__	(3,2)	(4,3)



	* 위와 같이 (연결된 정점, 가중치)의 쌍을 리스트에 포함하면 된다.



### 인접 행렬과 인접 리스트의 비교

* 공간 복잡도
  * 인접 행렬 : O(V^2)
    * 인접 행렬은 정점의 개수(V)×정점의 개수(V) 크기의 행렬이니까.
  * 인접 리스트 : O(E)
    * 간선만 저장하면 된다. 즉, 간선의 개수 만큼



<cite>인접 리스트가 일반적으로 공간이 적게 들텐데...그러면 인접 행렬은 언제 쓰는 거지?</cite>



1. 정점 u, v를 잇는 간선의 존재 여부를 찾을 때
   * A[u] [v]가 0인지 아닌지만 확인하면 된다. O(1)이 된다.
   * 하지만, 리스트에서는 A[u]를 모두 찾아서 v가 있는지 확인해야 한다.
2. 방향 그래프에서 u->v의 반대 방향이 있는지 찾을 때
   * A[v] [u]가 0인지 아닌지만 확인하면 된다. O(1)이 된다.
   * 하지만, 리스트에서는 A[v]를 모두 찾아서 u가 있는지 확인해야 한다.
3. 완전 그래프인 경우
   * 완전 그래프에서 간선의 개수는
     * E = V(V-1)/2가 된다.
     * 따라서, 이때는 인접 행렬이 더 편하다.



### 추가적인 표현 방법

​	만약, 역량 평가 시험장에서 library를 쓰지 못하게 하거나, c만 써야하는 경우!

​	나는 C++, JAVA 잘 몰라요~하는 경우!

​	정말로 linked list를 구현해야 하는 경우!

​	이럴 때는 어떻게 하느냐!



1. __간선에 대한 정보를 모두 저장__ 한다.

<img src="http://drive.google.com/uc?export=view&amp;id=1Z3YKlp_-KTX0fVvfiKrB5Qa7OHjalEeB" style="zoom:50%;" />

​		E[0] = 1 2

​		E[1] = 1 3

​		E[2] = 1 4

​		E[3] = 2 1

​		E[4] = 2 3

​		E[5] = 3 1

​		E[6] = 3 2

​		E[7] = 3 4

​		E[8] = 3 5

​		E[9] = 4 1

​		E[10] = 4 3

​		E[11] = 4 5

​		E[12] = 5 3

​		E[13] = 5 4



2. 간선의 앞 정점을 기준으로 개수를 센다.

   |      i       |  0   |  1   |  2   |  3   |  4   |  5   |
   | :----------: | :--: | :--: | :--: | :--: | :--: | :--: |
   | __count[i]__ |  0   |  3   |  2   |  4   |  3   |  2   |

3. 숫자를 누적한다.

   |      i       |  0   |  1   |  2   |   3   |    4    |     5     |
   | :----------: | :--: | :--: | :--: | :---: | :-----: | :-------: |
   | __count[i]__ |  0   |  3   | 3+2  | 3+2+4 | 3+2+4+3 | 3+2+4+3+2 |

   |      i       |  0   |  1   |  2   |  3   |  4   |  5   |
   | :----------: | :--: | :--: | :--: | :--: | :--: | :--: |
   | __count[i]__ |  0   |  3   |  5   |  9   |  12  |  14  |

   * 이렇게 하면 정점 n에 저장된 간선들은 E[count[n-1]]~E[count[n]-1]에 있음을 쉽게 알 수 있다.
     * 정점 1과 관련된 간선들은 E[0]~E[2]
     * 정점 3과 관련된 간선들은 E[5]~E[8]


<html>
{% include default_mention.html %}
</html>

---
title: "Graph - 연결 요소"
comments: true
header:
  teaser: 'http://drive.google.com/uc?export=view&id=1n6duP4g7uTjn9px4R1OC927Z9a_u58il'
categories:
  - data structure
  - 백준 문제
tags:
  - 자료구조
  - data structure
  - graph
  - DFS
  - BFS
  - 연결 요소
  - 그래프 응용
show_date: true
last_modified_at: 2020-09-07
---

## 연결 요소(Connected Component)

<img src='http://drive.google.com/uc?export=view&id=1dCkAwAed4jd8llumiZ30hpvnweK6W2kO' style="zoom:50%;" />

위의 이미지는 그래프가 1개 일까 2개 일까??

정답은 1개와 2개 모두 맞다.

1개라면 단지 연결하는 간선이 없는 그래프이고

2개라면 우연히 정점이 겹치지 않는 각각의 그래프이다.

<img src='http://drive.google.com/uc?export=view&id=1n6duP4g7uTjn9px4R1OC927Z9a_u58il' style="zoom:50%;" />

그래프가 1개라면, __나누어진 각각의 그래프를 연결 요소__라고 한다.

즉, 위의 그림으로 보자면 노란색 연결 요소 하나 파란색 연결 요소하나 이렇게 총 2개의 연결요소로 이루어진 그래프가 되는 것이다.



## 연결 요소의 조건

* 연결 요소에 속한 모든 정점들은 끊어지면 안되고, 서로 연결 되어 있어야 한다.
* 다른 연결 요소에 속한 정점과 연결되는 간선이 있어선 안된다.



## 연결 요소 문제

DFS나 BFS 탐색을 이용하여 구할 수 있다.

* 문제

  <a href="https://www.acmicpc.net/problem/11724" target="_blank">백준 11724번 - 연결요소의 개수</a>

* 풀이

  1. dfs(재귀함수) 이용 - 연결리스트

     <div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div><div style="line-height:130%">24</div><div style="line-height:130%">25</div><div style="line-height:130%">26</div><div style="line-height:130%">27</div><div style="line-height:130%">28</div><div style="line-height:130%">29</div><div style="line-height:130%">30</div><div style="line-height:130%">31</div><div style="line-height:130%">32</div><div style="line-height:130%">33</div><div style="line-height:130%">34</div><div style="line-height:130%">35</div><div style="line-height:130%">36</div><div style="line-height:130%">37</div><div style="line-height:130%">38</div><div style="line-height:130%">39</div><div style="line-height:130%">40</div><div style="line-height:130%">41</div><div style="line-height:130%">42</div><div style="line-height:130%">43</div><div style="line-height:130%">44</div><div style="line-height:130%">45</div><div style="line-height:130%">46</div><div style="line-height:130%">47</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0086b3">#include</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>cstdio<span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0086b3">#include</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>algorithm<span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0086b3">#include</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span><span style="color:#4be6fa">vector</span><span style="color:#ff3399">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">using</span>&nbsp;<span style="color:#ff3399">namespace</span>&nbsp;<span style="color:#4be6fa">std</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">int</span>&nbsp;component&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">0</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">vector</span><span style="color:#ff3399">&lt;</span><span style="color:#4be6fa">int</span><span style="color:#ff3399">&gt;</span>&nbsp;list[<span style="color:#c10aff">1001</span>];</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">bool</span>&nbsp;check[<span style="color:#c10aff">1001</span>];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">void</span>&nbsp;dfs(<span style="color:#4be6fa">int</span>&nbsp;v)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;check[v]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">true</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>&nbsp;(<span style="color:#4be6fa">int</span>&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">0</span>;&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>&nbsp;list[v].<span style="color:#4be6fa">size</span>();&nbsp;i<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span><span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">int</span>&nbsp;next&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;list[v][i];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>&nbsp;(<span style="color:#aaffaa"></span><span style="color:#ff3399">!</span>check[next])&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dfs(next);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">int</span>&nbsp;main()&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">int</span>&nbsp;n,&nbsp;m;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">scanf</span>(<span style="color:#ffd500">"%d&nbsp;%d"</span>,&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span>n,&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span>m);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>&nbsp;(<span style="color:#4be6fa">int</span>&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">0</span>;&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>&nbsp;m;&nbsp;i<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span><span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">int</span>&nbsp;u,&nbsp;v;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">scanf</span>(<span style="color:#ffd500">"%d&nbsp;%d"</span>,&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span>u,&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span>v);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;list[u].<span style="color:#4be6fa">push_back</span>(v);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;list[v].<span style="color:#4be6fa">push_back</span>(u);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>&nbsp;(<span style="color:#4be6fa">int</span>&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">1</span>;&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;n;&nbsp;i<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span><span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sort(list[i].<span style="color:#4be6fa">begin</span>(),&nbsp;list[i].<span style="color:#4be6fa">end</span>());</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>&nbsp;(<span style="color:#4be6fa">int</span>&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">1</span>;&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;n;&nbsp;i<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span><span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>&nbsp;(<span style="color:#aaffaa"></span><span style="color:#ff3399">!</span>check[i])&nbsp;{&nbsp;<span style="color:#999999">//false일&nbsp;때(방문&nbsp;하지&nbsp;않았을&nbsp;때)</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span><span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dfs(i);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">printf</span>(<span style="color:#ffd500">"%d"</span>,&nbsp;component);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

     * 굳이 sort 할 필요 없는데(어느 정점부터 방문 할 것인지랑은 상관 없어서) 그냥 sort 쓰고 싶어서 추가해봤어요....ㅎ
   * __38~43의 for문__ : 정점 1번부터 n번째 정점까지 반복문을 사용해서 해당 정점을 방문했는지 아닌지 파악한다. 이때 방문하지 않았다면, dfs 탐색을 시작한다. dfs는 재귀함수로 구현되어 있으므로, 탐색이 끝나면 다시 반복문으로 돌아온다. 그리고 반복문을 통해 방문하지 않은 정점이 있는지 파악한다. 방문하지 않은 정점은 이전에 탐색되지 않은 새로운 연결 요소의 시작이므로 component 변수에 +1을 해준다.

2. bfs 이용 - 연결리스트

     <div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div><div style="line-height:130%">24</div><div style="line-height:130%">25</div><div style="line-height:130%">26</div><div style="line-height:130%">27</div><div style="line-height:130%">28</div><div style="line-height:130%">29</div><div style="line-height:130%">30</div><div style="line-height:130%">31</div><div style="line-height:130%">32</div><div style="line-height:130%">33</div><div style="line-height:130%">34</div><div style="line-height:130%">35</div><div style="line-height:130%">36</div><div style="line-height:130%">37</div><div style="line-height:130%">38</div><div style="line-height:130%">39</div><div style="line-height:130%">40</div><div style="line-height:130%">41</div><div style="line-height:130%">42</div><div style="line-height:130%">43</div><div style="line-height:130%">44</div><div style="line-height:130%">45</div><div style="line-height:130%">46</div><div style="line-height:130%">47</div><div style="line-height:130%">48</div><div style="line-height:130%">49</div><div style="line-height:130%">50</div><div style="line-height:130%">51</div><div style="line-height:130%">52</div><div style="line-height:130%">53</div><div style="line-height:130%">54</div><div style="line-height:130%">55</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0086b3">#include</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>cstdio<span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0086b3">#include</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>algorithm<span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0086b3">#include</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span><span style="color:#4be6fa">vector</span><span style="color:#ff3399">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#0086b3">#include</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span><span style="color:#4be6fa">queue</span><span style="color:#ff3399">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">using</span>&nbsp;<span style="color:#ff3399">namespace</span>&nbsp;<span style="color:#4be6fa">std</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">int</span>&nbsp;component&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">0</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">vector</span><span style="color:#ff3399">&lt;</span><span style="color:#4be6fa">int</span><span style="color:#ff3399">&gt;</span>&nbsp;list[<span style="color:#c10aff">1001</span>];</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">bool</span>&nbsp;check[<span style="color:#c10aff">1001</span>];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">queue</span><span style="color:#ff3399">&lt;</span><span style="color:#4be6fa">int</span><span style="color:#ff3399">&gt;</span>&nbsp;q;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">void</span>&nbsp;bfs(<span style="color:#4be6fa">int</span>&nbsp;v)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;check[v]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">true</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;q.push(v);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">while</span>&nbsp;(<span style="color:#aaffaa"></span><span style="color:#ff3399">!</span>q.empty())&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">int</span>&nbsp;current&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;q.<span style="color:#4be6fa">front</span>();</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>&nbsp;(<span style="color:#4be6fa">int</span>&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">0</span>;&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>&nbsp;list[current].<span style="color:#4be6fa">size</span>();&nbsp;i<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span><span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">int</span>&nbsp;next&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;list[current][i];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>&nbsp;(<span style="color:#aaffaa"></span><span style="color:#ff3399">!</span>check[next])&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;check[next]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">true</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;q.push(next);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;q.<span style="color:#4be6fa">pop</span>();</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">int</span>&nbsp;main()&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">int</span>&nbsp;n,&nbsp;m;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">scanf</span>(<span style="color:#ffd500">"%d&nbsp;%d"</span>,&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span>n,&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span>m);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>&nbsp;(<span style="color:#4be6fa">int</span>&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">0</span>;&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>&nbsp;m;&nbsp;i<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span><span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">int</span>&nbsp;u,&nbsp;v;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">scanf</span>(<span style="color:#ffd500">"%d&nbsp;%d"</span>,&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span>u,&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span>v);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;list[u].<span style="color:#4be6fa">push_back</span>(v);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;list[v].<span style="color:#4be6fa">push_back</span>(u);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>&nbsp;(<span style="color:#4be6fa">int</span>&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">1</span>;&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;n;&nbsp;i<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span><span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sort(list[i].<span style="color:#4be6fa">begin</span>(),&nbsp;list[i].<span style="color:#4be6fa">end</span>());</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>&nbsp;(<span style="color:#4be6fa">int</span>&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">1</span>;&nbsp;i&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;n;&nbsp;i<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span><span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>&nbsp;(<span style="color:#aaffaa"></span><span style="color:#ff3399">!</span>check[i])&nbsp;{&nbsp;<span style="color:#999999">//false일&nbsp;때(방문&nbsp;하지&nbsp;않았을&nbsp;때)</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span><span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;bfs(i);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">printf</span>(<span style="color:#ffd500">"%d"</span>,&nbsp;component);</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

     * __47~50의 for문__ : 정점 1번부터 n번째 정점까지 반복문을 사용해서 해당 정점을 방문했는지 아닌지 파악한다. 이때 방문하지 않았다면, bfs 탐색을 시작한다. bfs는 queue가 빌 때까지 진행되므로, 탐색이 끝나면 다시 반복문으로 돌아온다. 그리고 반복문을 통해 방문하지 않은 정점이 있는지 파악한다. 방문하지 않은 정점은 이전에 탐색되지 않은 새로운 연결 요소의 시작이므로 component 변수에 +1을 해준다.

     <html>
     {% include default_mention.html %}
     </html>     
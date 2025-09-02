# ACM (6 = 1 + 2 + 1 + 2)


## 基础算法




输入输出处理：
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strconv"
	"strings"
)

var (
	in  = bufio.NewReader(os.Stdin)
	out = bufio.NewWriter(os.Stdout)
)

func readString() string {
	line, _ := in.ReadString('\n')
	line = strings.TrimSpace(line)
	return line
}

// 读取一行并拆分为字符串数组
func readLine() []string {
	line := readString()
	return strings.Split(line, " ")
}

// 读取一个整数
func readInt() int {
	line := readString()
	val, _ := strconv.Atoi(line)
	return val
}

// 读取一行多个整数
func readInts() []int {
	line := readString()
	fields := strings.Fields(line)
	res := make([]int, len(fields))
	for i, f := range fields {
		res[i], _ = strconv.Atoi(f)
	}
	return res
}

func readInt64() int64 {
	line := readString()
	val, _ := strconv.ParseInt(line, 10, 64)
	return val
}

func readInt64s() []int64 {
	line := readString()
	fields := strings.Fields(line)
	res := make([]int64, len(fields))
	for i, f := range fields {
		res[i], _ = strconv.ParseInt(f, 10, 64)
	}
	return res
}

func writeInts(arr []int) {
	strArr := make([]string, len(arr))
	for i, v := range arr {
		strArr[i] = strconv.FormatInt(v, 10) // int64 -> string
	}
	fmt.Fprintln(out, strings.Join(strArr, " "))
}

func writeInt64s(arr []int64) {
	strArr := make([]string, len(arr))
	for i, v := range arr {
		strArr[i] = strconv.FormatInt(v, 10) // int64 -> string
	}
	fmt.Fprintln(out, strings.Join(strArr, " "))
}

func main() {
	defer out.Flush()

	// 示例：读取 n, m
	nm := readInts()
	n, m := nm[0], nm[1]
	fmt.Fprintln(out, "n =", n, "m =", m)

	// 示例：读取一行 n 个数
	arr := readInts()
	fmt.Fprintln(out, "arr =", arr)
}
```




### 大数运算
```go
// 内置大数运算
type BigInt struct {
	value *big.Int
}

// NewBigInt 从 int64 或字符串初始化
func NewBigInt(val interface{}) *BigInt {
	b := &BigInt{value: big.NewInt(0)}
	switch v := val.(type) {
	case int:
		b.value.SetInt64(int64(v))
	case int64:
		b.value.SetInt64(v)
	case string:
		b.value.SetString(v, 10) // 默认十进制
	case *big.Int:
		b.value.Set(v)
	default:
		panic("unsupported type")
	}
	return b
}

// 加法
func (a *BigInt) Add(b *BigInt) *BigInt {
	return &BigInt{value: new(big.Int).Add(a.value, b.value)}
}

// 减法
func (a *BigInt) Sub(b *BigInt) *BigInt {
	return &BigInt{value: new(big.Int).Sub(a.value, b.value)}
}

// 乘法
func (a *BigInt) Mul(b *BigInt) *BigInt {
	return &BigInt{value: new(big.Int).Mul(a.value, b.value)}
}

// 除法（整除）
func (a *BigInt) Div(b *BigInt) *BigInt {
	return &BigInt{value: new(big.Int).Div(a.value, b.value)}
}

// 取模
func (a *BigInt) Mod(b *BigInt) *BigInt {
	return &BigInt{value: new(big.Int).Mod(a.value, b.value)}
}

// 幂运算 (a^n)
func (a *BigInt) Pow(n int64) *BigInt {
	return &BigInt{value: new(big.Int).Exp(a.value, big.NewInt(n), nil)}
}

// 比较
func (a *BigInt) Cmp(b *BigInt) int {
	return a.value.Cmp(b.value) // -1:小于, 0:等于, 1:大于
}

// 转字符串
func (a *BigInt) String() string {
	return a.value.String()
}

func main() {
	a := NewBigInt("123456789012345678901234567890")
	b := NewBigInt(987654321)

	sum := a.Add(b)
	diff := a.Sub(b)
	prod := a.Mul(b)
	quot := a.Div(NewBigInt(10))
	power := b.Pow(5)

	fmt.Println("a + b =", sum)
	fmt.Println("a - b =", diff)
	fmt.Println("a * b =", prod)
	fmt.Println("a / 10 =", quot)
	fmt.Println("b^5 =", power)
}
```

### 排序

### 搜索


#### DFS

#### BFS


### 贪心


### 双指针


### 二分查找


#### 第一个 >= target
```go
func lowerBound(nums []int, target int) int {
	l, r := 0, len(nums)-1
	for l <= r {
		mid := l + (r-l)/2
		if nums[mid] >= target {
			r = mid - 1
		} else {
			l = mid + 1
		}
	}
	return l
}
```


#### 最后一个 <= target
```go
func lowerBoundLast(nums []int, target int) int {
	l, r := 0, len(nums)-1
	for l <= r {
		mid := l + (r-l)/2
		if nums[mid] <= target {
			l = mid + 1
		} else {
			r = mid - 1
		}
	}
	return r
}
```


#### 第一个 > target
```go
func upperBound(nums []int, target int) int {
	l, r := 0, len(nums)-1
	for l <= r {
		mid := l + (r-l)/2
		if nums[mid] > target {
			r = mid - 1
		} else {
			l = mid + 1
		}
	}
	return l
}
```


### 分治


### 前缀和


### 离散化
```go
package main

import (
	"fmt"
	"sort"
)

// Discretize 将数组进行离散化
// 返回: 离散化后的数组 + 原值到新编号的映射函数
func Discretize(nums []int) ([]int, func(int) int) {
	// 1. 拷贝并排序去重
	tmp := append([]int(nil), nums...)
	sort.Ints(tmp)
	tmp = unique(tmp)

	// 2. 建立映射：值 -> 下标（去重后数组）
	idx := make(map[int]int, len(tmp))
	for i, v := range tmp {
		idx[v] = i
	}

	// 3. 返回映射函数
	getID := func(x int) int {
		return idx[x]
	}

	return tmp, getID
}

// 去重函数（得先排序）
func unique(a []int) []int {
	if len(a) == 0 {
		return a
	}
	res := a[:1]
	for _, v := range a[1:] {
		if v != res[len(res)-1] {
			res = append(res, v)
		}
	}
	return res
}

func main() {
	arr := []int{100, 500, 100, 200, 1000, 500}

	coords, getID := Discretize(arr)

	fmt.Println("去重排序后的值:", coords) // [100 200 500 1000]

	for _, v := range arr {
		fmt.Printf("值 %d -> 离散化ID %d\n", v, getID(v))
	}
}
/*
    去重排序后的值: [100 200 500 1000]
    值 100 -> 离散化ID 0
    值 500 -> 离散化ID 2
    值 100 -> 离散化ID 0
    值 200 -> 离散化ID 1
    值 1000 -> 离散化ID 3
    值 500 -> 离散化ID 2
*/
```



### 差分


### 倍增



### 分块

Sqrt Decomposition，块状数组


#### 单点修改 & 区间求和
```go
package main

import (
	"fmt"
	"math"
)

type SqrtDecomp struct {
	n     int     // 数组长度
	block int     // 块大小
	num   int     // 块数量
	arr   []int   // 原数组 (0~n-1)
	sum   []int   // 每个块的和（可换成 max/min）
}

func NewSqrtDecomp(arr []int) *SqrtDecomp {
	n := len(arr)
	block := int(math.Sqrt(float64(n)))
	if block == 0 {
		block = 1
	}
	// 保证块数 > 0
	num := (n + block - 1) / block
	sum := make([]int, num)

	for i := 0; i < n; i++ {
		sum[i/block] += arr[i]
	}

	return &SqrtDecomp{
		n:     n,
		block: block,
		num:   num,
		arr:   arr,
		sum:   sum,
	}
}

// 单点修改：arr[idx] = val
func (s *SqrtDecomp) Update(idx, val int) {
	// 计算块位置
	b := idx / s.block
	s.sum[b] += val - s.arr[idx]
	s.arr[idx] = val
}

// 区间求和
func (s *SqrtDecomp) Query(l, r int) int {
	res := 0
	for l <= r {
		// 如果 l 在块头且整个块在 [l,r] 内，直接用块的 sum
		if l%s.block == 0 && l+s.block-1 <= r {
			res += s.sum[l/s.block]
			l += s.block
		} else {
			res += s.arr[l]
			l++
		}
	}
	return res
}
```


#### 区间加法 + 区间求和
```go
type LazySqrt struct {
	n     int
	block int
	num   int
	arr   []int
	sum   []int
	lazy  []int // 懒加载数组优化
}

func NewLazySqrt(arr []int) *LazySqrt {
	n := len(arr)
	block := int(math.Sqrt(float64(n)))
	if block == 0 {
		block = 1
	}
	num := (n + block - 1) / block
	sum := make([]int, num)
	lazy := make([]int, num)

	for i := 0; i < n; i++ {
		sum[i/block] += arr[i]
	}

	return &LazySqrt{n, block, num, arr, sum, lazy}
}

// 区间加
func (s *LazySqrt) Add(l, r, val int) {
	for i := l; i <= r; {
		if i%s.block == 0 && i+s.block-1 <= r {
			b := i / s.block
			s.lazy[b] += val
			s.sum[b] += val * s.block
			i += s.block
		} else {
			b := i / s.block
			s.arr[i] += val
			s.sum[b] += val
			i++
		}
	}
}

// 区间和
func (s *LazySqrt) Query(l, r int) int {
	res := 0
	for i := l; i <= r; {
		if i%s.block == 0 && i+s.block-1 <= r {
			b := i / s.block
			res += s.sum[b]
			i += s.block
		} else {
			b := i / s.block
			res += s.arr[i] + s.lazy[b]
			i++
		}
	}
	return res
}
```



### 离线


#### 莫队



### 随机



## 数据结构




golang常用Map哈希表来实现Set集合
```go
// 定义一个 Set，元素是 int
type Set map[int]struct{}

// 添加
func (s Set) Add(x int) {
	s[x] = struct{}{}
}

// 删除
func (s Set) Remove(x int) {
	delete(s, x)
}

// 是否存在
func (s Set) Has(x int) bool {
	_, ok := s[x]
	return ok
}

// 大小
func (s Set) Size() int {
	return len(s)
}
```


### 链表


### 堆
```go
package main

import (
	"container/heap"
	"fmt"
)

// 泛型堆，T 必须可比较
type Heap[T any] struct {
	data []T
	less func(a, b T) bool // 比较函数：返回 true 表示 a 应该在 b 前面
}

func NewHeap[T any](less func(a, b T) bool) *Heap[T] {
	return &Heap[T]{less: less}
}

// heap.Interface 实现
func (h Heap[T]) Len() int            { return len(h.data) }
func (h Heap[T]) Less(i, j int) bool  { return h.less(h.data[i], h.data[j]) }
func (h Heap[T]) Swap(i, j int)       { h.data[i], h.data[j] = h.data[j], h.data[i] }

func (h *Heap[T]) Push(x any) { h.data = append(h.data, x.(T)) }
func (h *Heap[T]) Pop() any {
	old := h.data
	n := len(old)
	x := old[n-1]
	h.data = old[:n-1]
	return x
}

// Heap使用方法

// 入堆
func (h *Heap[T]) PushHeap(x T) { heap.Push(h, x) }

// 出堆
func (h *Heap[T]) PopHeap() T { return heap.Pop(h).(T) }

// 查看堆顶
func (h *Heap[T]) Top() T { return h.data[0] }

// 堆大小
func (h *Heap[T]) Size() int { return len(h.data) }

// 是否为空
func (h *Heap[T]) Empty() bool {
	return len(h.data) == 0
}

func main() {
	// 最小堆
	minH := NewHeap[int](func(a, b int) bool { return a < b })
	heap.Init(minH)
	minH.PushHeap(5)
	minH.PushHeap(2)
	minH.PushHeap(8)
	minH.PushHeap(1)
	fmt.Println("最小堆堆顶:", minH.Top()) // 1
	fmt.Println(minH.PopHeap())           // 1
	fmt.Println(minH.PopHeap())           // 2

	// 最大堆
	maxH := NewHeap[int](func(a, b int) bool { return a > b })
	heap.Init(maxH)
	maxH.PushHeap(5)
	maxH.PushHeap(2)
	maxH.PushHeap(8)
	maxH.PushHeap(1)
	fmt.Println("最大堆堆顶:", maxH.Top()) // 8
	fmt.Println(maxH.PopHeap())           // 8
	fmt.Println(maxH.PopHeap())           // 5
}
```




### 栈
```go
// 简单栈实现
// st := Stack[int]{}
type Stack[T any] struct {
	data []T
}

// 入栈
func (s *Stack[T]) Push(x T) {
	s.data = append(s.data, x)
}

// 出栈（并返回栈顶元素）
// 调用前要保证栈非空
func (s *Stack[T]) Pop() T {
	n := len(s.data)
    // 切片操作
	top := s.data[n-1]
	s.data = s.data[:n-1]
	return top
}

// 查看栈顶元素（不弹出）
// 调用前要保证栈非空
func (s *Stack[T]) Top() T {
	return s.data[len(s.data)-1]
}

// 栈是否为空
func (s *Stack[T]) Empty() bool {
	return len(s.data) == 0
}

// 栈大小
func (s *Stack[T]) Size() int {
	return len(s.data)
}
```


### 队列
```go
// q := Queue[int]{}
type Queue[T any] struct {
	data []T
}

// 入队
func (q *Queue[T]) Push(x T) {
	q.data = append(q.data, x)
}

// 出队（调用前确保非空）
func (q *Queue[T]) Pop() T {
	front := q.data[0]
	q.data = q.data[1:]
	return front
}

// 查看队首
func (q *Queue[T]) Front() T {
	return q.data[0]
}

// 是否为空
func (q *Queue[T]) Empty() bool {
	return len(q.data) == 0
}

// 队列大小
func (q *Queue[T]) Size() int {
	return len(q.data)
}
```



### 二叉树



### 并查集
```go
type UnionFind struct {
	parent []int
	rank   []int
	size   int // 当前连通分量数量
}

// 初始化 n 个元素（0..n-1）
func NewUnionFind(n int) *UnionFind {
	uf := &UnionFind{
		parent: make([]int, n),
		rank:   make([]int, n),
		size:   n, // 初始每个元素自己一个集合
	}
	for i := 0; i < n; i++ {
		uf.parent[i] = i
		uf.rank[i] = 1
	}
	return uf
}

// 查找根节点（路径压缩）
func (uf *UnionFind) Find(x int) int {
	if uf.parent[x] != x {
		uf.parent[x] = uf.Find(uf.parent[x])
	}
	return uf.parent[x]
}

// 合并两个集合（按秩合并）
func (uf *UnionFind) Union(x, y int) {
	rootX := uf.Find(x)
	rootY := uf.Find(y)
	if rootX == rootY {
		return
	}
	if uf.rank[rootX] < uf.rank[rootY] {
		rootX, rootY = rootY, rootX
	}
	uf.parent[rootY] = rootX
	if uf.rank[rootX] == uf.rank[rootY] {
		uf.rank[rootX]++
	}
	uf.size-- // 合并后集合总数减 1
}

// 判断是否在同一个集合
func (uf *UnionFind) Connected(x, y int) bool {
	return uf.Find(x) == uf.Find(y)
}

// 获取当前集合总数
func (uf *UnionFind) Count() int {
	return uf.size
}
```


### ST表
```go
package main

import (
	"fmt"
	"math"
)

// SparseTable 支持最小值、最大值、GCD 等幂运算
type SparseTable struct {
	data [][]int
	log  []int // 预处理log对数运算
}

// 构造 ST 表，arr 必须是不可修改的数组
func NewSparseTable(arr []int) *SparseTable {
	n := len(arr)
	K := int(math.Log2(float64(n))) + 1

	st := &SparseTable{
		data: make([][]int, n),
		log:  make([]int, n+1),
	}

	// 预处理 log
	st.log[1] = 0
	for i := 2; i <= n; i++ {
		st.log[i] = st.log[i/2] + 1
	}

	// 初始化 0 层
	for i := 0; i < n; i++ {
		st.data[i] = make([]int, K)
		st.data[i][0] = arr[i]
	}

	// DP 预处理
	for j := 1; j < K; j++ {
		for i := 0; i+(1<<j) <= n; i++ {
			// RMQ: 最小值
			st.data[i][j] = min(st.data[i][j-1], st.data[i+(1<<(j-1))][j-1])
		}
	}

	return st
}

// 查询区间 [l, r] 的最小值
func (st *SparseTable) Query(l, r int) int {
	j := st.log[r-l+1]
	return min(st.data[l][j], st.data[r-(1<<j)+1][j])
}

// 区间操作
func min(a, b int) int {
	if a < b {
		return a
	}
	return b
}

// ========== 示例 ==========
func main() {
	arr := []int{1, 3, 2, 7, 9, 11, 3, 5}
	st := NewSparseTable(arr)

	fmt.Println(st.Query(0, 2)) // 1
	fmt.Println(st.Query(1, 5)) // 2
	fmt.Println(st.Query(3, 6)) // 3
}
```



### 树状数组
```go
package main

import "fmt"

type BIT struct {
	n    int
	tree []int
}

// 初始化大小为 n 的树状数组
func NewBIT(n int) *BIT {
	return &BIT {
		n:    n,
		tree: make([]int, n+1), // 注意 BIT 通常从 1 开始
	}
}

// 单点更新：给 index 加 delta
func (bit *BIT) Add(index, delta int) {
	for i := index; i <= bit.n; i += i & -i {
		bit.tree[i] += delta
	}
}

// 查询前缀和 [1..index]
func (bit *BIT) Query(index int) int {
	res := 0
	for i := index; i > 0; i -= i & -i {
		res += bit.tree[i]
	}
	return res
}

// 查询区间和 [l..r]
func (bit *BIT) RangeQuery(l, r int) int {
	return bit.Query(r) - bit.Query(l-1)
}

// ========== 示例 ==========
func main() {
	arr := append([]int{0}, []int{1, 2, 3, 4, 5}) // 从 1 开始，0 填充
	n := len(arr) - 1

	bit := NewBIT(n)
	for i := 1; i <= n; i++ {
		bit.Add(i, arr[i])
	}

	fmt.Println(bit.Query(3))      // 前缀和 1+2+3=6
	fmt.Println(bit.RangeQuery(2,4)) // 区间和 2+3+4=9

	bit.Add(3, 5) // arr[3] += 5
	fmt.Println(bit.Query(3)) // 1+2+8=11
}
```



### 线段树
```go
package main

import "fmt"

type SegmentTree struct {
	n    int
	data []int
	tree []int
}

// 构造线段树
func NewSegmentTree(arr []int) *SegmentTree {
	n := len(arr)
	tree := &SegmentTree{
		n:    n,
		data: make([]int, n),
		tree: make([]int, 4*n), // 线段树数组大小一般开4倍
	}
	copy(tree.data, arr)
	tree.build(1, 0, n-1)
	return tree
}

// 构建
func (st *SegmentTree) build(node, l, r int) {
	if l == r {
		st.tree[node] = st.data[l]
		return
	}
	mid := (l + r) / 2
	st.build(2*node, l, mid)
	st.build(2*node+1, mid+1, r)
	st.tree[node] = st.merge(st.tree[2*node], st.tree[2*node+1])
}

// 合并函数（这里默认求和，可改为 min/max）
func (st *SegmentTree) merge(a, b int) int {
	return a + b
}

// 区间查询 [ql, qr]
func (st *SegmentTree) Query(node, l, r, ql, qr int) int {
	if ql <= l && r <= qr {
		return st.tree[node]
	}
	mid := (l + r) / 2
	res := 0 // merge 单位元（求和为0，最小值可用 INF）
	if ql <= mid {
		res = st.merge(res, st.Query(2*node, l, mid, ql, qr))
	}
	if qr > mid {
		res = st.merge(res, st.Query(2*node+1, mid+1, r, ql, qr))
	}
	return res
}

// 单点更新 index -> val
func (st *SegmentTree) Update(node, l, r, index, val int) {
	if l == r {
		st.tree[node] = val
		return
	}
	mid := (l + r) / 2
	if index <= mid {
		st.Update(2*node, l, mid, index, val)
	} else {
		st.Update(2*node+1, mid+1, r, index, val)
	}
	st.tree[node] = st.merge(st.tree[2*node], st.tree[2*node+1])
}

// ========== 示例 ==========
func main() {
	arr := []int{1, 2, 3, 4, 5}
	st := NewSegmentTree(arr)

	fmt.Println(st.Query(1, 0, st.n-1, 1, 3)) // 2+3+4=9

	st.Update(1, 0, st.n-1, 2, 10)           // arr[2]=10
	fmt.Println(st.Query(1, 0, st.n-1, 1, 3)) // 2+10+4=16
}
```



## 字符串


### 哈希

### 字典树



### KMP


### Manacher



## 动态规划



### 线性DP

### 背包DP



### 区间DP


### 状压DP


### 数位DP


### 树形DP

### 环形DP




## 图论


### 图


#### 图的存储

##### 邻接矩阵
```go
const INF = 1e9
var n int
var g [510][510]int

// 初始化
for i := 0; i < n; i++ {
    for j := 0; j < n; j++ {
        if i == j {
            g[i][j] = 0
        } else {
            g[i][j] = INF
        }
    }
}

// 添加边 u -> v 权值 w
g[u][v] = w
g[v][u] = w // 无向图
```


##### 邻接表
```go
// 存边
type Edge struct {
    to, w int
}

var n int
var g [][]Edge

// 初始化
g = make([][]Edge, n)

// 添加边 u -> v 权值 w
g[u] = append(g[u], Edge{v, w})
g[v] = append(g[v], Edge{u, w}) // 无向图


// 存点
var g [][]int
g = make([][]int, n)
g[u] = append(g[u], v)
g[v] = append(g[v], u) // 无向图
```

Adjacency List


##### 边集



### 树



## 数学



### 数论

#### 快速幂
```go
func pow(a, b int64) int64 {
    res := int64(1)
    for b > 0 {
        if b&1 == 1 { // 当前位为1
            res *= a
        }
        a *= a        // a = a^2
        b >>= 1       // b = b/2
    }
    return res
}
```




### 离散数学




### 博弈论



### 计算几何
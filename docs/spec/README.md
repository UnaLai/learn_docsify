# 系統 SPEC
## 關聯表
```graphviz
digraph hierarchy {
  # 起始與結尾
  start [label="開始"]
  end [label="結束"]

  # 過程
  node[shape=box]
  a [label="a",shape=diamond]
  b [label="b"]
  c [label="c"]

  # 連線邏輯
  start->a
  a->b [label="a至b的描述"]
  a->c [label="a至c的描述"]
  c->end
}
```


```graphviz
digraph hierarchy {
  rankdir=LR;
  node [ shape=record ];

  order [label="資料表: 訂單 |
      <id>id 單號 |
      <created_at>created_at 建立日期 |
      <creater>creater 建立人 |
      <order_details>order_details 訂單細節 "];
  
   member [label="資料表: 會員 |
      <id>id 單號"];

   order_details [label="資料表: 訂單細節 |
      <id>id 單號 |
      <order_id>order_id 訂單單號 |
      <quantity>quantity 數量 |
      <price>price 價格 |
      <product_id>product_id 產品 "];

   order:creater->member:id
   order:order_details->order_details:id[label="1..n"]

}
```

## 甘特圖
```mermaid
gantt
   title A Gantt Diagram
   dateFormat  YYYY-MM-DD
   section Section
   A task           :a1, 2014-01-01, 2014-01-04
   Another task     :after a1  , 20d
   section Another
   Task in sec      :2014-01-12  , 12d
   another task      : 24d
```

## 子圖
```mermaid
graph LR
  subgraph 子圖A
      A --- B  --- C
  end
  
  C --> D
```

## 箭頭
```mermaid
graph LR
  A --- B
  C --> D
  E -.- F
  G -.-> H
  I === J
```

### 帶有文字


```mermaid
graph LR
  A-- 文字 ---B
  C-- 文字 --> D
  E -. 文字 .- F
  G -. 文字 .-> H
  I == 文字 ==> J
```

```mermaid
graph LR
  A-- 文字 ---B
  C-- 文字 --> D
  E -. 文字 .- F
  G -. 文字 .-> H
  I == 文字 ==> J
```

### CSS 樣式
```mermaid
graph LR
   id1[方框]-- 文字 ---id2(帶有圓角的方框)

style id1 fill:#f6e6a1,stroke:#a1cdf6,stroke-width:4px
```

## 方向

```mermaid
graph LR
   id1[方框]     
   id2(帶有圓角的方框)
   id3([體育場形狀])
   id4[[子例程]]
   id5[(圓柱狀)]
   id6((圓形))
   id7>非對稱形狀]
   id8{菱形}
   id9{{六角形}}
   id10[/平行四邊形1/]
   id11[\平行四邊形2\]
   id12[/梯形1\]
   id13[\梯形2/]
```

一對相對側具有半圓形的矩形構成的二維幾何形狀

### 範例

```mermaid
graph TD
   id1[A] --> id2{B}
   id2{B} -- YES --> id3[C]
   id2{B} -- NO --> id4{D}
   id4{D} -- YES --> id5[E]
   id4{D} -- NO --> id6[F]
```

```mermaid
graph LR
   id1([開始]) --> id2[B] --> id3{C}
   subgraph block
      id3{C} -- NO --> id2[B]
      id3{C} -- YES --> id4[D]
   end
   id4[D] --> id5([結束])
```
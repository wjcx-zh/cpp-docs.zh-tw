---
title: "seed_seq 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1::seed_seq"
  - "std::tr1::seed_seq"
  - "tr1.seed_seq"
  - "seed_seq"
  - "std.tr1.seed_seq"
  - "random/std::tr1::seed_seq"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "seed_seq 類別"
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
caps.latest.revision: 19
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# seed_seq 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

儲存不帶正負號的整數值的向量，可以提供亂數引擎的隨機化種子。  
  
## 語法  
  
```  
class seed_seq  
{  
public:  
    // types  
    typedef unsigned int result_type;  
  
    // constructors  
    seed_seq();  
  
    template<class T>  
    seed_seq(initializer_list<T> initlist);  
  
    template<class InputIterator>  
    seed_seq(InputIterator begin, InputIterator end);  
  
    // generating functions  
    template<class RandomAccessIterator>  
    void generate(RandomAccessIterator begin, RandomAccessIterator end);  
  
    // property functions  
    size_t size() const;  
  
    template<class OutputIterator>  
    void param(OutputIterator dest) const;  
  
    // no copy functions  
    seed_seq(const seed_seq&) = delete;  
    void operator=(const seed_seq&) = delete;  
};  
```  
  
## 類型  
 `typedef unsigned int result_type;`   
種子序列的項目類型。 32 位元不帶正負號的整數類型。  
  
## 建構函式  
 `seed_seq();`   
預設建構函式，初始化具有空的內部序列。  
  
 `template<class T>`   
 `seed_seq(initializer_list<T> initlist);`   
使用 `initlist` 設定內部序列。  
`T` 必須是整數類型。  
  
 `template<class InputIterator>`   
 `seed_seq(InputIterator begin, InputIterator end);`   
初始化內部序列使用提供的輸入迭代器範圍中所有項目。  
`iterator_traits<InputIterator>::value_type` 必須是整數類型。  
  
## Members  
  
### 產生函式  
 `template<class RandomAccessIterator> void generate(RandomAccessIterator begin, RandomAccessIterator end);`   
會使用內部演算法所提供序列的項目中填入。 此演算法會受到內部序列 `seed_seq` 已初始化。  
不做任何動作如果 `begin == end`。  
  
### 屬性函式  
 `size_t size() const;`   
傳回數字中的項目 `seed_seq`。  
  
 `template<class OutputIterator> void param(OutputIterator dest) const;`   
將內部序列複製至輸出迭代器 `dest`。  
  
## 範例  
 下列程式碼範例會執行這三個建構函式，並在指派給陣列時從產生的 `seed_seq` 執行個體產生輸出。 如需範例，會使用 `seed_seq` 隨機號碼產生器，請參閱 [\<random\>](../standard-library/random.md)。  
  
```cpp  
#include <iostream>  
#include <random>  
#include <string>  
#include <array>  
  
using namespace std;  
  
void test(const seed_seq& sseq) {  
    cout << endl << "seed_seq::size(): " << sseq.size() << endl;  
  
    cout << "seed_seq::param(): ";  
    ostream_iterator<unsigned int> out(cout, " ");  
    sseq.param(out);  
    cout << endl;  
  
    cout << "Generating a sequence of 5 elements into an array: " << endl;  
    array<unsigned int, 5> seq;  
    sseq.generate(seq.begin(), seq.end());  
    for (unsigned x : seq) { cout << x << endl; }  
}  
  
int main()  
{  
    seed_seq seed1;  
    test(seed1);  
  
    seed_seq seed2 = { 1701, 1729, 1791 };  
    test(seed2);  
  
    string sstr = "A B C D"; // seed string  
    seed_seq seed3(sstr.begin(), sstr.end());  
    test(seed3);  
}  
```  
  
## 輸出  
  
```Output  
  
seed_seq::size(): 0 seed_seq::param()︰ 產生 5 個元素陣列的序列︰ 505382999 163489202 3932644188 763126080 73937346 seed_seq::size(): 3 seed_seq::param(): 1701年 1729年 1791年產生 5 個元素陣列的序列︰ 1730669648 1954224479 2809786021 1172893117 2393473414 seed_seq::size(): 7 seed_seq::param(): 65 32 66 32 67 32 68 產生 5 個元素陣列的序列: 3139879222 3775111734 1084804564 2485037668 1985355432  
```  
  
## 備註  
 這個類別的成員函式不會擲回例外狀況。  
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)
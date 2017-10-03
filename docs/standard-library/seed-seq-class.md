---
title: "seed_seq 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::seed_seq
- random/std::seed_seq::result_type
- random/std::seed_seq::generate
- random/std::seed_seq::size
- random/std::seed_seq::param
dev_langs:
- C++
helpviewer_keywords:
- std::seed_seq [C++]
- std::seed_seq [C++], result_type
- std::seed_seq [C++], generate
- std::seed_seq [C++], size
- std::seed_seq [C++], param
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 7083c7ef1de370d4faeef3344e4e78418e36a731
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="seedseq-class"></a>seed_seq 類別
儲存不帶正負號的整數值的向量，可以提供亂數引擎的隨機化種子。  
  
## <a name="syntax"></a>語法  
```  
class seed_seq  
   {  
public:  
   // types  
   typedef unsigned int result_type;  

   // constructors  
   seed_seq();
   template <class T>  
      seed_seq(initializer_list<T> initlist);
   template <class InputIterator>  
      seed_seq(InputIterator begin, InputIterator end);

   // generating functions  
   template <class RandomAccessIterator>  
      void generate(RandomAccessIterator begin, RandomAccessIterator end);

   // property functions  
   size_t size() const;
   template <class OutputIterator>  
      void param(OutputIterator dest) const;

   // no copy functions  
   seed_seq(const seed_seq&) = delete;  
   void operator=(const seed_seq&) = delete;  
   };  
```  
## <a name="types"></a>類型  
 `typedef unsigned int result_type;`   
種子序列的項目類型。 32 位元不帶正負號的整數類型。  
  
## <a name="constructors"></a>建構函式  
 `seed_seq();`   
預設的建構函式，會初始化以具備空的內部序列。  
  
 `template<class T>`   
 `seed_seq(initializer_list<T> initlist);`   
使用 `initlist` 設定內部序列。                   
`T` 必須是整數類型。  
  
 `template<class InputIterator>`   
 `seed_seq(InputIterator begin, InputIterator end);`   
使用輸入迭代器範圍中提供的所有元素，來初始化內部序列。                  
`iterator_traits<InputIterator>::value_type` 必須是整數類型。  
  
## <a name="members"></a>Members  
  
### <a name="generating-functions"></a>產生函式  
 `template<class RandomAccessIterator> void generate(RandomAccessIterator begin,          RandomAccessIterator end);`   
使用內部演算法，以填入所提供序列的元素。 已初始化 `seed_seq` 的內部序列會影響此演算法。                          
如果 `begin == end`，則不會有任何動作。  
  
### <a name="property-functions"></a>屬性函式  
 `size_t size() const;`   
傳回 `seed_seq` 中項目的數目。  
  
 `template<class OutputIterator> void param(OutputIterator dest) const;`   
將內部序列複製至輸出迭代器 `dest`。  
  
## <a name="example"></a>範例  
 下列程式碼範例會執行這三個建構函式，並在指派給陣列時從產生的 `seed_seq` 執行個體產生輸出。 如需搭配亂數產生器使用 `seed_seq` 的範例，請參閱 [\<random>](../standard-library/random.md)。  
  
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
  
```Output  
seed_seq::size(): 0  
seed_seq::param():  
Generating a sequence of 5 elements into an array:  
505382999  
163489202  
3932644188  
763126080  
73937346  
  
seed_seq::size(): 3  
seed_seq::param(): 1701 1729 1791  
Generating a sequence of 5 elements into an array:  
1730669648  
1954224479  
2809786021  
1172893117  
2393473414  
  
seed_seq::size(): 7  
seed_seq::param(): 65 32 66 32 67 32 68  
Generating a sequence of 5 elements into an array:  
3139879222  
3775111734  
1084804564  
2485037668  
1985355432  
```  
  
## <a name="remarks"></a>備註  
 此類別的成員函式不會擲回例外狀況。  
  
## <a name="requirements"></a>需求  
 **標頭：**\<random>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [\<random>](../standard-library/random.md)




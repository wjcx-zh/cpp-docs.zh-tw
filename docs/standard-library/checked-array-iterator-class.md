---
title: "checked_array_iterator 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "iterator/checked_array_iterator"
  - "checked_array_iterator"
  - "std::checked_array_iterator"
  - "std.checked_array_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "checked_array_iterator"
  - "checked_array_iterator 類別"
  - "checked_array_iterator, 語法"
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# checked_array_iterator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`checked_array_iterator` 類別可讓您將陣列或指標轉換為已檢查的迭代器。  使用這個類別做為原始指標或陣列的包裝函式 \(使用 [make\_checked\_array\_iterator](../Topic/make_checked_array_iterator.md) 函式\)，做為提供檢查以及管理未檢查指標警告的目標方式，而非全域的關閉這些警告訊息。  如果需要，您可以使用這個類別的未檢查版本 [unchecked\_array\_iterator](../standard-library/unchecked-array-iterator-class.md)。  
  
> [!NOTE]
>  這個類別是 Standard C\+\+ 程式庫的 Microsoft 擴充功能。  透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C\+\+ Standard 建置環境。  關於如何撰寫不需要使用這個類別的程式碼範例，請參閱下列第二個範例。  
  
## 語法  
  
```  
template <class _Iterator>  
    class checked_array_iterator;  
```  
  
## 備註  
 這個類別是在 [stdext](../standard-library/stdext-namespace.md) 命名空間中定義的。  
  
 如需已檢查的迭代器功能的詳細資訊和範例程式碼，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。  
  
## 範例  
 下列範例示範如何定義和使用已檢查的陣列迭代器。  
  
 如果目的地不夠大，無法容納所有複製的項目，例如變更以下程式行的情況：  
  
```cpp  
copy(a, a + 5, checked_array_iterator<int*>(b, 5));  
```  
  
 與  
  
```cpp  
copy(a, a + 5, checked_array_iterator<int*>(b, 4));  
```  
  
 會發生執行階段錯誤。  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
using namespace stdext;  
  
int main() {  
   int a[]={0, 1, 2, 3, 4};  
   int b[5];  
   copy(a, a + 5, checked_array_iterator<int*>(b, 5));  
  
   cout << "(";  
   for (int i = 0 ; i < 5 ; i++)  
      cout << " " << b[i];  
   cout << " )" << endl;  
  
   // constructor example  
   checked_array_iterator<int*> checked_out_iter(b, 5);  
   copy(a, a + 5, checked_out_iter);  
  
   cout << "(";  
   for (int i = 0 ; i < 5 ; i++)  
      cout << " " << b[i];  
   cout << " )" << endl;  
}  
```  
  
  **\( 0 1 2 3 4 \)**  
**\( 0 1 2 3 4 \)**   
## 範例  
 若要避免使用 Standard C\+\+ 程式庫演算法時對 `checked_array_iterator` 類別的需求，請考慮使用 `vector` 而非動態配置的陣列。  下列範例示範如何進行這項操作。  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
  
#include <algorithm>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main()  
{  
    std::vector<int> v(10);  
    int *arr = new int[10];  
    for (int i = 0; i < 10; ++i)  
    {  
        v[i] = i;  
        arr[i] = i;  
    }  
  
    // std::copy(v.begin(), v.end(), arr); will result in  
    // warning C4996. To avoid this warning while using int *,  
    // use the Microsoft extension checked_array_iterator.  
    std::copy(v.begin(), v.end(),  
              stdext::checked_array_iterator<int *>(arr, 10));  
  
    // Instead of using stdext::checked_array_iterator and int *,  
    // consider using std::vector to encapsulate the array. This will  
    // result in no warnings, and the code will be portable.  
    std::vector<int> arr2(10);    // Similar to int *arr = new int[10];  
    std::copy(v.begin(), v.end(), arr2.begin());  
  
    for (int j = 0; j < arr2.size(); ++j)  
    {  
        cout << " " << arr2[j];  
    }  
    cout << endl;  
  
    return 0;  
}  
```  
  
  **0 1 2 3 4 5 6 7 8 9**   
### 建構函式  
  
|||  
|-|-|  
|[checked\_array\_iterator](../Topic/checked_array_iterator::checked_array_iterator.md)|從基底迭代器建構預設的 `checked_array_iterator` 或 `checked_array_iterator`。|  
  
### Typedefs  
  
|||  
|-|-|  
|[difference\_type](../Topic/checked_array_iterator::difference_type.md)|類型，提供兩個參考同一容器內項目的 `checked_array_iterator` 之間的差異。|  
|[指標](../Topic/checked_array_iterator::pointer.md)|類型，提供指向 `checked_array_iterator` 定址的項目之指標。|  
|[參考](../Topic/checked_array_iterator::reference.md)|類型，提供指向 `checked_array_iterator` 定址的項目之參考。|  
  
### 成員函式  
  
|||  
|-|-|  
|[基底](../Topic/checked_array_iterator::base.md)|從其 `checked_array_iterator` 復原基礎迭代器。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\=\=](../Topic/checked_array_iterator::operator==.md)|測試兩個 `checked_array_iterator` 是否相等。|  
|[operator\!\=](../Topic/checked_array_iterator::operator!=.md)|測試兩個 `checked_array_iterator` 是否不等。|  
|[運算子 \<](../Topic/checked_array_iterator::operator%3C.md)|測試運算子左邊的 `checked_array_iterator` 是否小於右邊的 `checked_array_iterator`。|  
|[運算子 \>](../Topic/checked_array_iterator::operator%3E.md)|測試運算子左邊的 `checked_array_iterator` 是否大於右邊的 `checked_array_iterator`。|  
|[運算子 \<\=](../Topic/checked_array_iterator::operator%3C=.md)|測試運算子左邊的 `checked_array_iterator` 是否小於或等於右邊的 `checked_array_iterator`。|  
|[運算子 \>\=](../Topic/checked_array_iterator::operator%3E=.md)|測試運算子左邊的 `checked_array_iterator` 是否大於或等於右邊的 `checked_array_iterator`。|  
|[運算子 \*](../Topic/checked_array_iterator::operator*.md)|傳回 `checked_array_iterator` 定址的項目。|  
|[operator\-\>](../Topic/checked_array_iterator::operator-%3E.md)|傳回由 `checked_array_iterator` 定址的項目之指標。|  
|[operator\+\+](../Topic/checked_array_iterator::operator++.md)|遞增 `checked_array_iterator` 至下一個項目。|  
|[operator\-\-](../Topic/checked_array_iterator::operator--.md)|遞減 `checked_array_iterator` 至上一個項目。|  
|[operator\+\=](../Topic/checked_array_iterator::operator+=.md)|加入指定位移至 `checked_array_iterator`。|  
|[operator\+](../Topic/checked_array_iterator::operator+.md)|將位移新增至迭代器，並傳回新的 `checked_array_iterator`，定址在新的位移位置中插入的項目。|  
|[operator\-\=](../Topic/checked_array_iterator::operator-=.md)|從 `checked_array_iterator` 減去指定的位移。|  
|[operator\-](../Topic/checked_array_iterator::operator-.md)|從迭代器中遞減位移，並傳回新的 `checked_array_iterator`，其將插入的項目定址在新的位移位置中。|  
|[operator&#91;&#93;](../Topic/checked_array_iterator::operator.md)|以指定的位置數目，從 `checked_array_iterator` 定址的項目傳回項目位移的參考。|  
  
## 需求  
 **標頭：**\<iterator\>  
  
 **命名空間：**stdext  
  
## 請參閱  
 [\<iterator\>](../standard-library/iterator.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)
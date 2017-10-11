---
title: "Lambda 運算式語法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 9daa1ce8d7b55f71113dcf7559394715bd93c604
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="lambda-expression-syntax"></a>Lambda 運算式語法
本文示範 Lambda 運算式的語法和結構化項目。 如需 lambda 運算式的說明，請參閱[Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)。  
  
## <a name="function-objects-vs-lambdas"></a>函式物件與Lambda  
 當您撰寫程式碼時，您可能會使用函式指標和函式物件解決問題，以及執行計算，特別是當您使用[c + + 標準程式庫演算法](../cpp/algorithms-modern-cpp.md)。 函式指標和函式物件各有優缺點。例如，函式指標的語法額外負荷最小，但是無法在範圍內保留狀態，而函式物件則可以維護狀態但無法避免需要定義類別的語法額外負荷。  
  
 Lambda 結合了函式指標和函式物件的優點並避免其缺點。 Lambda 像函式物件一樣具有彈性並可以維護狀態，但不同於函式物件，由於語法精簡，因此不需要明確類別定義。 使用 Lambda 時，您可以撰寫相對函式物件而言較不麻煩且較不容易發生錯誤的程式碼。  
  
 下列範例比較使用函式物件與使用 Lambda。 第一個範例使用 Lambda 將 `vector` 物件中每個偶數和奇數項目列印到主控台。 第二個範例使用函式物件完成相同的工作。  
  
## <a name="example-1-using-a-lambda"></a>範例 1：使用 Lambda  
 此範例將 Lambda 傳遞至 `for_each` 函式。 Lambda 會列印結果，其陳述 `vector` 物件中的每個項目是偶數還是奇數。  
  
### <a name="code"></a>程式碼  
  
```cpp  
// even_lambda.cpp  
// compile with: cl /EHsc /nologo /W4 /MTd  
#include <algorithm>  
#include <iostream>  
#include <vector>  
using namespace std;  
  
int main()   
{  
   // Create a vector object that contains 10 elements.  
   vector<int> v;  
   for (int i = 1; i < 10; ++i) {  
      v.push_back(i);  
   }  
  
   // Count the number of even numbers in the vector by   
   // using the for_each function and a lambda.  
   int evenCount = 0;  
   for_each(v.begin(), v.end(), [&evenCount] (int n) {  
      cout << n;  
      if (n % 2 == 0) {  
         cout << " is even " << endl;  
         ++evenCount;  
      } else {  
         cout << " is odd " << endl;  
      }  
   });  
  
   // Print the count of even numbers to the console.  
   cout << "There are " << evenCount   
        << " even numbers in the vector." << endl;  
}  
```  
  
### <a name="output"></a>輸出  
  
```Output  
1 is odd  
2 is even  
3 is odd  
4 is even  
5 is odd  
6 is even  
7 is odd  
8 is even  
9 is odd  
There are 4 even numbers in the vector.  
  
```  
  
### <a name="comments"></a>註解  
 在此範例中，`for_each` 函式的第三個引數是 Lambda。 `[&evenCount]` 組件指定運算式的擷取子句、`(int n)` 指定參數清單，而其餘組件則指定運算式的主體。  
  
## <a name="example-2-using-a-function-object"></a>範例 2：使用函式物件  
 有時候，Lambda 的靈巧度較差，因此擴充程度無法超越上一個範例。 下一個範例不使用 Lambda，而是使用函式物件搭配 `for_each` 函式產生和範例 1 相同的結果。 這兩個範例都會將偶數計數儲存在 `vector` 物件中。 為了維護作業的狀態，`FunctorClass` 類別會以傳址方式儲存 `m_evenCount` 變數做為成員變數。 `FunctorClass` 會實作函式呼叫運算子 `operator()` 以執行此作業。 Visual C++ 編譯器會產生與範例 1. 中 Lambda 程式碼大小和效能相當的程式碼。 就本文所述此類基礎問題而言，較簡單的 Lambda 設計應該比函式物件的設計好。 不過，如果您認為未來可能會需要大幅擴充，那麼使用函式物件設計會讓程式碼較容易維護。  
  
 如需有關`operator()`，請參閱[函式呼叫](../cpp/function-call-cpp.md)。 如需有關`for_each`函式，請參閱[for_each](../standard-library/algorithm-functions.md#for_each)。  
  
### <a name="code"></a>程式碼  
  
```cpp  
// even_functor.cpp  
// compile with: /EHsc  
#include <algorithm>  
#include <iostream>  
#include <vector>  
using namespace std;  
  
class FunctorClass  
{  
public:  
    // The required constructor for this example.  
    explicit FunctorClass(int& evenCount)  
        : m_evenCount(evenCount) { }  
  
    // The function-call operator prints whether the number is  
    // even or odd. If the number is even, this method updates  
    // the counter.  
    void operator()(int n) const {  
        cout << n;  
  
        if (n % 2 == 0) {  
            cout << " is even " << endl;  
            ++m_evenCount;  
        } else {  
            cout << " is odd " << endl;  
        }  
    }  
  
private:  
    // Default assignment operator to silence warning C4512.  
    FunctorClass& operator=(const FunctorClass&);  
  
    int& m_evenCount; // the number of even variables in the vector.  
};  
  
int main()  
{  
    // Create a vector object that contains 10 elements.  
    vector<int> v;  
    for (int i = 1; i < 10; ++i) {  
        v.push_back(i);  
    }  
  
    // Count the number of even numbers in the vector by   
    // using the for_each function and a function object.  
    int evenCount = 0;  
    for_each(v.begin(), v.end(), FunctorClass(evenCount));  
  
    // Print the count of even numbers to the console.  
    cout << "There are " << evenCount  
        << " even numbers in the vector." << endl;  
}  
  
```  
  
## <a name="output"></a>輸出  
  
```Output  
1 is odd  
2 is even  
3 is odd  
4 is even  
5 is odd  
6 is even  
7 is odd  
8 is even  
9 is odd  
There are 4 even numbers in the vector.  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)   
 [Lambda 運算式的範例](../cpp/examples-of-lambda-expressions.md)   
 [產生](../standard-library/algorithm-functions.md#generate)   
 [generate_n](../standard-library/algorithm-functions.md#generate_n)   
 [for_each](../standard-library/algorithm-functions.md#for_each)   
 [例外狀況規格 (throw)](../cpp/exception-specifications-throw-cpp.md)   
 [編譯器警告 （層級 1） C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)   
 [Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)

---
title: 範圍架構 for 陳述式 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0edf350289d04824dc2e06e4e11144a4f3141770
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407029"
---
# <a name="range-based-for-statement-c"></a>以範圍為基礎的 for 陳述式 (C++)
對於 `statement` 中的每個項目，重複且循序地執行 `expression`。  
  
## <a name="syntax"></a>語法  
  
```  
for ( for-range-declaration : expression )  
   statement   
```  
  
## <a name="remarks"></a>備註  
 使用範圍架構**for**陳述式來建構必須透過 「 範圍 」，這定義為任何項目，您可以逐一執行的迴圈 — 比方說， `std::vector`，或任何其他 c + + 標準程式庫序列的範圍由此`begin()`和`end()`。 名稱中所宣告`for-range-declaration`部分是在本機**如**陳述式，且無法重新宣告中`expression`或`statement`。 請注意，[自動](../cpp/auto-cpp.md)關鍵字會偏好`for-range-declaration`陳述式部分。 

 **Visual Studio 2017 的新功能：** 範圍式 for 迴圈不再需要 begin （） 和 end （） 傳回相同類型的物件。 這可讓 end() 傳回 sentinel 物件，例如 Ranges-V3 提案中所定義範圍使用的物件。 如需詳細資訊，請參閱 [Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) (一般化範圍架構的 For 迴圈) 和 [range-v3 library on GitHub](https://github.com/ericniebler/range-v3) (GitHub 上的 range-v3 程式庫)。
  
 此程式碼示範如何使用範圍型**針對**迴圈來逐一查看陣列和向量：  
  
```cpp  
// range-based-for.cpp  
// compile by using: cl /EHsc /nologo /W4  
#include <iostream>  
#include <vector>  
using namespace std;  
  
int main()   
{  
    // Basic 10-element integer array.  
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  
  
    // Range-based for loop to iterate through the array.  
    for( int y : x ) { // Access by value using a copy declared as a specific type.   
                       // Not preferred.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    // The auto keyword causes type inference to be used. Preferred.  
  
    for( auto y : x ) { // Copy of 'x', almost always undesirable  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( auto &y : x ) { // Type inference by reference.  
        // Observes and/or modifies in-place. Preferred when modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( const auto &y : x ) { // Type inference by const reference.  
        // Observes in-place. Preferred when no modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
    cout << "end of integer array test" << endl;  
    cout << endl;  
  
    // Create a vector object that contains 10 elements.  
    vector<double> v;  
    for (int i = 0; i < 10; ++i) {  
        v.push_back(i + 0.14159);  
    }  
  
    // Range-based for loop to iterate through the vector, observing in-place.  
    for( const auto &j : v ) {  
        cout << j << " ";  
    }  
    cout << endl;  
    cout << "end of vector test" << endl;  
}  
```  
  
 輸出如下：  

```Output
 1 2 3 4 5 6 7 8 9 10  
  
 1 2 3 4 5 6 7 8 9 10  
  
 1 2 3 4 5 6 7 8 9 10  
  
 1 2 3 4 5 6 7 8 9 10  
  
 `end of integer array test`  
  
 `0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159`  
  
 `end of vector test`  
```

 以範圍為基礎**for**迴圈終止時其中一種在`statement`執行：[中斷](../cpp/break-statement-cpp.md)，[傳回](../cpp/return-statement-cpp.md)，或[goto](../cpp/goto-statement-cpp.md)要加上標籤外部範圍為基礎的陳述式**針對**迴圈。 A[繼續](../cpp/continue-statement-cpp.md)陳述式中以範圍為基礎**如**迴圈終止只有目前的反覆項目。  
  
 請記住這些事項的相關範圍型**針對**:  
  
-   自動辨識陣列。  
  
-   辨識具有 `.begin()` 和 `.end()` 的容器。  
  
-   使用與引數相依的查閱 `begin()` 和 `end()` 以取得任何其他項目。  
  
## <a name="see-also"></a>另請參閱  
 [自動](../cpp/auto-cpp.md)   
 [反覆運算陳述式](../cpp/iteration-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [while 陳述式 (C++)](../cpp/while-statement-cpp.md)   
 [do-while 陳述式 (C++)](../cpp/do-while-statement-cpp.md)   
 [for 陳述式 (C++)](../cpp/for-statement-cpp.md)
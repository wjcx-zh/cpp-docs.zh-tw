---
title: "參考類型函式傳回 |Microsoft 文件"
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
- function return types [C++], reference type
- data types [C++], function return types
- functions [C++], return types
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1cadf01b1af0bac4fb76d0146a51b789b5ddc6e5
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="reference-type-function-returns"></a>參考類型函式傳回
函式可宣告為傳回參考類型。 進行此類宣告有兩個原因：  
  
-   傳回的資訊是一個夠大的物件，因此傳回參考比傳回複本更有效率。  
  
-   函式的類型必須是左值。  
  
-   傳回函式時，referred-to 物件不會超出範圍。  
  
 就像它可以是傳遞大型物件比較有效率*至*函式所參考，它也可以更有效率的方式傳回大型物件*從*所參考的函式。 使用參考傳回通訊協定就不需要在傳回之前將物件複製到暫存位置。  
  
 當函式必須評估為左值時，參考傳回類型可能也會很有用。 大部分的多載運算子都屬於此類，特別是指派運算子。 中涵蓋多載運算子[多載運算子](../cpp/operator-overloading.md)。  
  
## <a name="example"></a>範例  
 請考量 `Point` 範例：  
  
```  
// refType_function_returns.cpp  
// compile with: /EHsc  
  
#include <iostream>  
using namespace std;  
  
class Point  
{  
public:  
// Define "accessor" functions as  
//  reference types.  
unsigned& x();  
unsigned& y();  
private:  
// Note that these are declared at class scope:  
unsigned obj_x;   
unsigned obj_y;   
};  
  
unsigned& Point :: x()  
{  
return obj_x;  
}  
unsigned& Point :: y()  
{  
return obj_y;  
}  
  
int main()  
{  
Point ThePoint;  
// Use x() and y() as l-values.  
ThePoint.x() = 7;  
ThePoint.y() = 9;  
  
// Use x() and y() as r-values.  
cout << "x = " << ThePoint.x() << "\n"  
<< "y = " << ThePoint.y() << "\n";  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
x = 7  
y = 9  
```  
  
 請注意，函式 `x` 和 `y` 已宣告為傳回參考類型。 這些函式可在指派陳述式的任一邊使用。  
  
 也請注意，在 main 中，Point 物件保持在範圍內，因此其參考成員仍然存在且可以安全地存取。  
  
 除了下列情況下之外，參考類型的宣告必須包含初始設定式：  
  
-   明確宣告 `extern`  
  
-   類別成員的宣告  
  
-   類別中的宣告  
  
-   函式引數或函式傳回類型的宣告  
  
## <a name="caution-returning-address-of-local"></a>傳回區域變數位址注意事項  
 如果您宣告區域範圍的物件，則會在傳回函式時終結該物件。 如果函式傳回該物件的參考，則呼叫端嘗試使用 null 參考時，該參考可能會在執行階段造成存取違規。  
  
```  
// C4172 means Don’t do this!!!  
Foo& GetFoo()  
{  
    Foo f;  
    ...  
    return f;  
} // f is destroyed here  
```  
  
 編譯器會發出警告，以在此情況下： `warning C4172: returning address of local variable or temporary`。 在簡單程式中，如果呼叫端在覆寫記憶體位置之前存取參考，則可能偶爾不會發生存取違規。 這純粹只是幸運。 請留意警告。  
  
## <a name="see-also"></a>另請參閱  
 [參考](../cpp/references-cpp.md)

---
title: "函式呼叫 （c + +） |Microsoft 文件"
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
- function calls, C++ functions
- functions [C++], calling
- operator overloading [C++], function calls
- function overloading [C++], function-call operator
- function calls, operator
- operators [C++], overloading
- operator overloading [C++], examples
- function call operator ()
ms.assetid: 5094254a-045b-46f7-8653-69bc91e80dce
caps.latest.revision: 7
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
ms.openlocfilehash: e066ab4c154c04c0c1a39b7f8d0164881a0a96cc
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="function-call-c"></a>函式呼叫 (C++)
使用括號叫用的函式呼叫運算子是二元運算子。  
  
## <a name="syntax"></a>語法  
  
```  
  
primary-expression ( expression-list )  
```  
  
## <a name="remarks"></a>備註  
 在此內容中，`primary-expression` 是第一個運算元，而 `expression-list` (可能空白的引數清單) 是第二個運算元。 函式呼叫運算子用於需要一些參數的運算。 這不會有問題，因為 `expression-list` 是清單，而不是單一運算元。 函式呼叫運算子必須是非靜態成員函式。  
  
 函數呼叫運算子在多載時，不會修改呼叫函式的方式；而是會修改運算子在套用到特定類別類型的物件時如何解譯。 例如，下列程式碼通常會沒有意義：  
  
```  
Point pt;  
pt( 3, 2 );  
```  
  
 但若是有適當多載的函式呼叫運算子，此語法可以用來將 `x` 座標偏移 3 個單位，`y` 座標偏移 2 個單位。 下列程式碼表示此定義：  
  
```  
// function_call.cpp  
class Point  
{  
public:  
    Point() { _x = _y = 0; }  
    Point &operator()( int dx, int dy )  
        { _x += dx; _y += dy; return *this; }  
private:  
    int _x, _y;  
};  
  
int main()  
{  
   Point pt;  
   pt( 3, 2 );  
}  
```  
  
 請注意，函式呼叫運算子會套用到物件的名稱，而不是函式的名稱。  
  
 您也可以使用函式指標 (而不是函式本身) 來多載函式呼叫運算子。  
  
```cpp  
typedef void(*ptf)();  
void func()  
{  
}  
struct S  
{  
   operator ptf()  
   {  
      return func;  
   }  
};  
  
int main()  
{  
   S s;  
   s();//operates as s.operator ptf()()  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [運算子多載](../cpp/operator-overloading.md)

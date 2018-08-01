---
title: 指派 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6343d7be23e633fe383343bd7f154d5cc9bb234
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407607"
---
# <a name="assignment"></a>指派
指派運算子 (**=**) 嚴格來說，是二元運算子。 它的宣告與任何其他二元運算子相同，但有下列例外狀況：  
  
-   它必須為非靜態成員函式。 否**運算子 =** 可以宣告為非成員函式。  
  
-   衍生類別不會進行繼承。  
  
-   預設值**運算子 =** 可以針對類別類型編譯器所產生函式，如果不存在。  
  
 下列範例說明如何宣告指派運算子：  
  
```cpp 
// assignment.cpp  
class Point  
{  
public:  
   Point &operator=( Point & );  // Right side is the argument.  
   int _x, _y;  
};  
  
// Define assignment operator.  
Point &Point::operator=( Point &ptRHS )  
{  
   _x = ptRHS._x;  
   _y = ptRHS._y;  
  
   return *this;  // Assignment operator returns left side.  
}  
  
int main()  
{  
}  
```  
  
 請注意，所提供的引數是在運算式的右方。 運算子會傳回物件以保留指派運算子的行為，而該運算子會在指派完成後傳回左方的值。 如此會允許執行下列寫入陳述式：  
  
```cpp 
pt1 = pt2 = pt3;  
```  
  
## <a name="see-also"></a>另請參閱  
 [運算子多載](../cpp/operator-overloading.md)
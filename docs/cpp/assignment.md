---
title: "指派 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4c11664b5a7089187099898fa375cd612e92a83b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="assignment"></a>指派
指派運算子 (**=**) 嚴格來說，是二元運算子。 它的宣告與任何其他二元運算子相同，但有下列例外狀況：  
  
-   它必須為非靜態成員函式。 不可將 `operator=` 宣告為非成員函式。  
  
-   衍生類別不會進行繼承。  
  
-   如果函式不存在，編譯器可以產生類別類型的預設 `operator=` 函式  (如需有關預設`operator=`函式，請參閱[成員指派和初始化](http://msdn.microsoft.com/en-us/94048213-8b49-4416-8069-b1b7a6f271f9)。)  
  
 下列範例說明如何宣告指派運算子：  
  
```  
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
  
```  
pt1 = pt2 = pt3;  
```  
  
## <a name="see-also"></a>請參閱  
 [運算子多載](../cpp/operator-overloading.md)
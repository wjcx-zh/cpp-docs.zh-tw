---
title: 函式樣板的明確特製化 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e35eda35a7d2474826ce151292121be224955420
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="explicit-specialization-of-function-templates"></a>函式樣板的明確特製化
透過函式樣板，您可以提供該類型的明確特製化 (覆寫) 函式樣板，來定義該特定類型的特殊行為。 例如:   
  
```cpp
template<> void MySwap(double a, double b);  
```  
  
 這個宣告可讓您定義不同的函式**double**變數。 像非樣板函式，標準類型轉換 (例如類型的變數提升**float**至**double**) 會套用。  
  
## <a name="example"></a>範例  
  
```cpp
// explicit_specialization.cpp  
template<class T> void f(T t)  
{  
};  
  
// Explicit specialization of f with 'char' with the  
// template argument explicitly specified:  
//  
template<> void f<char>(char c)  
{  
}  
  
// Explicit specialization of f with 'double' with the  
// template argument deduced:  
//  
template<> void f(double d)  
{  
}  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [函式樣板](../cpp/function-templates.md)

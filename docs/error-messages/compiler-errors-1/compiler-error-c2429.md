---
title: "編譯器錯誤 C2429 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2429
dev_langs:
- C++
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
caps.latest.revision: 9
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: eb0c1bf407d1478451c246cf615d031ef6c45bf9
ms.openlocfilehash: 7d2c27ccdba28720596984c46c9d24f9d29c7b15
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2429"></a>編譯器錯誤 C2429
'*語言功能*'需要編譯器旗標'*編譯器選項*'  
  
語言功能需要支援特定的編譯器選項。  
  
錯誤 C2429︰ 語言功能 '巢狀命名空間-定義' 需要編譯器旗標 '/ std:c + + 最新' 如果您嘗試定義就會產生*複合的命名空間*，包含一或多個範圍巢狀命名空間名稱，從 Visual Studio 2015 Update 3 的命名空間。 複合命名空間定義 c + + 中不允許在 C + +&17; 之前。 編譯器支援複合的命名空間定義當[/std:c + + 最新](../../build/reference/std-specify-language-standard-version.md)編譯器選項指定︰  
```cpp  
// C2429a.cpp  
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.  
                          // Use /std:c++latest to fix, or do this:  
// namespace a { namespace b { int i; }}  
  
int main() {  
   a::b::i = 2;  
}  
```  

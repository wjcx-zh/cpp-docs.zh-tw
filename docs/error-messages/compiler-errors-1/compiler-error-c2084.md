---
title: "編譯器錯誤 C2084 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
caps.latest.revision: 7
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 653dc7a4a5d330efc89942fbe4ddd07bff81f770
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2084"></a>編譯器錯誤 C2084
函式 '*函式*' 已有內文  
  
 已定義的函式。  
  
 在 Visual c + +，Visual Studio 2002 之前, 的版本  
  
-   雖然可能永遠不會使用其他定義，編譯器會接受多個解析為相同的實際類型的樣板特製化。 編譯器現在會偵測這些多個定義。  
  
-   `__int32`和`int`被視為個別的型別。 編譯器現在會將`__int32`同義`int`。 這表示如果同時針對多載函式，編譯器偵測到多個定義`__int32`和`int`並時發生錯誤。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2084:  
  
```cpp  
// C2084.cpp  
void Func(int);  
void Func(int) {}   // define function  
void Func(int) {}   // C2084 second definition  
```  
  
若要更正這個錯誤，請移除重複定義︰  
  
```  
// C2084b.cpp  
// compile with: /c  
void Func(int);  
void Func(int) {}  
```

---
title: "編譯器警告 （層級 1） C4190 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
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
translationtype: Machine Translation
ms.sourcegitcommit: 4ac033535632e94a365aa8dafd849f2ab28a3af7
ms.openlocfilehash: bf45c0737f52da93f93c1f95d313771f0e92a10e
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4190"></a>編譯器警告 （層級 1） C4190
「 identifier1 」 具有 C 連結指定，但會傳回 UDT 'identifier2' C 與不相容  
  
 函式或函式指標 UDT （使用者定義型別，也就是類別、 結構、 列舉或等位） 傳回型別具有和`extern`「 C 」 連結。 這是合法的如果︰  
  
-   這個函式的所有呼叫都都由 c + +。  
  
-   函式定義為 c + + 中。  
  
## <a name="example"></a>範例  
  
```cpp  
// C4190.cpp  
// compile with: /W1 /LD  
struct X  
{  
   int i;  
   X ();  
   virtual ~X ();  
};  
  
extern "C" X func ();   // C4190  
```

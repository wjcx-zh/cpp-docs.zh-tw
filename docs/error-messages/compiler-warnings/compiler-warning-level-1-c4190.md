---
title: "編譯器警告 （層級 1） C4190 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4190
dev_langs: C++
helpviewer_keywords: C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 127eb4327826412d605f2a4a008e411880998073
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4190"></a>編譯器警告 （層級 1） C4190
'identifier1' 具有 C 連結指定，但傳回 UDT 與 C 不相容的 ' identifier2'  
  
 函式或函式指標具有 UDT （使用者定義類型，這是類別、 結構、 列舉或等位） 做為傳回型別和`extern`"C"連結。 這是合法的如果：  
  
-   此函式的所有呼叫都都從 c + +。  
  
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
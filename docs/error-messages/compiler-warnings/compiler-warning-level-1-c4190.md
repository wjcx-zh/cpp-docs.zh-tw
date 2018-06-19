---
title: 編譯器警告 （層級 1） C4190 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e62f6bcfaa499338d5fde1d09cb91574241ce8a0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277890"
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
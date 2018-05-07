---
title: 編譯器警告 （層級 4） C4204 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4204
dev_langs:
- C++
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a803c81ea0f2fd6ce4b5a8f26eb626e89a32a9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4204"></a>編譯器警告 (層級 4) C4204
使用非標準擴充： 非常數的彙總初始設定式  
  
 搭配 Microsoft 擴充功能 (/Ze)，您可以初始化彙總類型 （陣列、 結構、 等位和類別），且不是常數的值。  
  
## <a name="example"></a>範例  
  
```  
// C4204.c  
// compile with: /W4  
int func1()  
{  
   return 0;  
}  
struct S1  
{  
   int i;  
};  
  
int main()  
{  
   struct S1 s1 = { func1() };   // C4204  
   return s1.i;  
}  
```  
  
 這類初始化是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。
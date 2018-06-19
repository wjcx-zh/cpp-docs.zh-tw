---
title: 編譯器錯誤 C3204 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3204
dev_langs:
- C++
helpviewer_keywords:
- C3204
ms.assetid: 06e578da-0262-48c8-b2ae-be1cd6d28884
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66b02701629904c73045a3850db5fe73adf58a75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248392"
---
# <a name="compiler-error-c3204"></a>編譯器錯誤 C3204
無法從 catch 區塊呼叫 '_alloca'  
  
 當您在 catch 區塊內使用 [_alloca](../../c-runtime-library/reference/alloca.md) 呼叫時，會發生這個錯誤。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3204：  
  
```  
// C3204.cpp  
// compile with: /EHsc  
#include <malloc.h>  
  
void ShowError(void)  
{  
   try  
   {  
   }  
   catch(...)  
   {  
      _alloca(1);   // C3204  
   }  
}  
```
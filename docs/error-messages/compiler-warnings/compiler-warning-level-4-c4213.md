---
title: 編譯器警告 （層級 4） C4213 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4213
dev_langs:
- C++
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 407fac636ea33c8cbd31104460442e5ac2aaec65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302902"
---
# <a name="compiler-warning-level-4-c4213"></a>編譯器警告 (層級 4) C4213
使用非標準擴充： 轉換值 （l-value）  
  
 您可以使用預設的 Microsoft 擴充功能 (/Ze) 中，轉換在指派陳述式的左半部。  
  
## <a name="example"></a>範例  
  
```  
// C4213.c  
// compile with: /W4  
void *a;  
void f()  
{  
   int   i[3];  
   a = &i;  
   *(( int * )a )++ = 3;  // C4213  
}  
  
int main()  
{  
}  
```  
  
 這類轉換是 ANSI 相容性無效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。
---
title: "編譯器警告 （層級 4） C4213 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4213
dev_langs:
- C++
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: abe563bd91736c9dfb6c0efc6507763b03a329cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
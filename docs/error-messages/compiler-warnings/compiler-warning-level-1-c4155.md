---
title: 編譯器警告 （層級 1） C4155 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4155
dev_langs:
- C++
helpviewer_keywords:
- C4155
ms.assetid: ba233353-09e3-4195-8127-13a27ddd8d70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 798d16beb6d14f0cec7d618c3b7fc9567861204b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275044"
---
# <a name="compiler-warning-level-1-c4155"></a>編譯器警告 (層級 1) C4155
刪除陣列運算式沒有使用陣列形式的 'delete'  
  
 陣列形式的 **delete** 應該用於刪除陣列。 這個警告只會在遵守 ANSI 相容性 (/Za) 時發生。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4155：  
  
```  
// C4155.cpp  
// compile with: /Za /W1  
#include <stdio.h>  
  
int main(void)  
{  
    int (*array)[ 10 ] = new int[ 5 ] [ 10 ];  
    array[0][0] = 8;  
  
    printf_s("%d\n", array[0][0]);  
  
   delete array;   // C4155  
    // try the following line instead  
    // delete [] array;   // C4155  
}  
```
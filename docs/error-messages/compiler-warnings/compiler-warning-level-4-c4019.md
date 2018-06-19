---
title: 編譯器警告 （層級 4） C4019 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4019
dev_langs:
- C++
helpviewer_keywords:
- C4019
ms.assetid: 4ecfe85d-673f-4334-8154-36fe7f0b3444
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d015b5674ad8f64a68b86979ce93313fa098c867
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296503"
---
# <a name="compiler-warning-level-4-c4019"></a>編譯器警告 (層級 4) C4019
在全域範圍有空的陳述式  
  
 全域範圍的分號前面沒有陳述式。  
  
 如果您移除多餘的分號，可能即會修正這個警告。  
  
## <a name="example"></a>範例  
  
```  
// C4019.c  
// compile with: /Za /W4  
#define declint( varname ) int varname;  
declint( a );   // C4019, int a;;  
declint( b )   // OK, int b;  
  
int main()  
{  
}  
```
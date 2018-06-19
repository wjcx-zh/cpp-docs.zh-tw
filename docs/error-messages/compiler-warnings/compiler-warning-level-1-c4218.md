---
title: 編譯器警告 （層級 1） C4218 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4218
dev_langs:
- C++
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88b27af84c390760274bb20665eec4452c8e7072
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279746"
---
# <a name="compiler-warning-level-1-c4218"></a>編譯器警告 (層級 1) C4218
使用非標準擴充： 必須指定至少一個儲存類別或類型  
  
 具有預設的 Microsoft 擴充功能 (/Ze) 中，您可以將變數宣告但未指定類型或存放裝置的類別。 預設類型為 `int`。  
  
## <a name="example"></a>範例  
  
```  
// C4218.c  
// compile with: /W4  
i;  // C4218  
  
int main()  
{  
}  
```  
  
 這類宣告不正確 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。
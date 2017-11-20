---
title: "編譯器警告 （層級 1） C4218 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4218
dev_langs: C++
helpviewer_keywords: C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 19552c6e836b3fa3f0111b8ab33bc11d33a5699a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
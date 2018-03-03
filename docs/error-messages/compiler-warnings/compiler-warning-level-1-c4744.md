---
title: "編譯器警告 (層級 1) C4744 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4744
dev_langs:
- C++
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b6fa95f8477f889aa8664d2b6d99c753cb9848d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4744"></a>編譯器警告 (層級 1) C4744
'var' 具有 'file1' 和 'file2' 中的不同類型: 'type1' 和 'type2'  
  
 外部變數參考，或在兩個檔案中定義了不同類型，這些檔案中。  若要解決，讓型別定義相同，或是變更其中一個檔案中的變數名稱。  
  
 只有當檔案以 /gl 編譯時，就會發出 C4744  如需詳細資訊，請參閱 [/GL (整個程式最佳化)](../../build/reference/gl-whole-program-optimization.md)。  
  
> [!NOTE]
>  因為 c + + 中的變數名稱都有型別資訊 C4744 通常會發生 C （非 c + +） 檔案中。  當範例 （如下） 是編譯為 c + + 時，您會取得連結器錯誤 LNK2019。  
  
## <a name="example"></a>範例  
 此範例包含的第一個定義。  
  
```  
// C4744.c  
// compile with: /c /GL  
int global;  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C4744。  
  
```  
// C4744b.c  
// compile with: C4744.c /GL /W1  
// C4744 expected  
#include <stdio.h>  
  
extern unsigned global;  
  
main()   
{  
    printf_s("%d\n", global);  
}  
```
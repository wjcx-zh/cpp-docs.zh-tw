---
title: 編譯器警告 （層級 1） C4005 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4005
dev_langs:
- C++
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a06ea88dab6ac7e89f7d53351b54593fd7bd232
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4005"></a>編譯器警告 （層級 1） C4005
'identifier': 巨集重新定義  
  
 巨集識別項定義了兩次。 編譯器會使用第二個巨集定義。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  在命令列上的程式碼中定義巨集`#define`指示詞。  
  
2.  從包含檔案匯入巨集。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  請移除其中一個定義。  
  
2.  使用[#undef](../../preprocessor/hash-undef-directive-c-cpp.md)指示詞之前的第二個定義。  
  
 下列範例會產生 C4005:  
  
```  
// C4005.cpp  
// compile with: /W1 /EHsc  
#include <iostream>  
using namespace std;  
  
#define TEST "test1"  
#define TEST "test2"   // C4005 delete or rename to resolve the warning  
  
int main() {  
   cout << TEST << endl;  
}  
```
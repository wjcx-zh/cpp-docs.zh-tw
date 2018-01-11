---
title: "編譯器警告 （層級 1） C4835 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4835
dev_langs: C++
helpviewer_keywords: C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92e2d17ada58773a34d8c2d14424dd88e74a06d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4835"></a>編譯器警告 (層級 1) C4835
'variable': 匯出資料的初始設定式將不會執行，直到主機組件中第一次執行受管理的程式碼  
  
 當存取受管理的元件之間的資料，建議您不使用原生 c + + 匯入和匯出機制。 相反地，宣告您的 managed 型別內的資料成員和參考中繼資料與`#using`的用戶端中。 如需詳細資訊，請參閱[#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4835。  
  
```  
// C4835.cpp  
// compile with: /W1 /clr /LD  
int f() { return 1; }  
int n = 9;  
  
__declspec(dllexport) int m = f();   // C4835  
__declspec(dllexport) int *p = &n;   // C4835  
```  
  
## <a name="example"></a>範例  
 下列範例會使用在上一個範例中，顯示變數的值未如預期地建置的元件。  
  
```  
// C4835_b.cpp  
// compile with: /clr C4835.lib  
#include <stdio.h>  
__declspec(dllimport) int m;  
__declspec(dllimport) int *p;  
  
int main() {  
   printf("%d\n", m);  
   printf("%d\n", p);  
}  
```  
  
```Output  
0  
268456008  
```
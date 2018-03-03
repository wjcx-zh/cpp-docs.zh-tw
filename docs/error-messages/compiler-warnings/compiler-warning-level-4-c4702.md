---
title: "編譯器警告 （層級 4） C4702 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4702
dev_langs:
- C++
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9ef7420f3699363d33d195e2455ab9fddf88de40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4702"></a>編譯器警告 (層級 4) C4702
無法連線到程式碼  
  
 這項警告是針對 Visual Studio.NET 2003年所進行的編譯器一致性工作的結果： 無法連線到程式碼。 當編譯器 （後端） 偵測到無法連線到程式碼時，它將會產生 C4702，層級 4 警告。  
  
 有效的 Visual c + + 的 Visual Studio.NET 2003年和 Visual Studio.NET 版本中的程式碼，移除無法到達的程式碼，或確保所有原始程式碼都都可到達的某些工作流程的執行。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4702。  
  
```  
// C4702.cpp  
// compile with: /W4  
#include <stdio.h>  
  
int main() {  
   return 1;  
   printf_s("I won't print.\n");   // C4702 unreachable  
}  
```  
  
## <a name="example"></a>範例  
 編譯時**/GX**， **/EHc**， **/EHsc**，或**/EHac**和使用 extern C 函式，程式碼可能會變得無法連線到因為 extern C函式假設不會擲回，所以不可以連線的 catch 區塊。  如果您認為這項警告不正確，因為函式可以擲回，以編譯**/EHa**或**/EHs**，取決於擲回的例外狀況。  
  
 如需詳細資訊，請參閱[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md)如需詳細資訊。  
  
 下列範例會產生 C4702。  
  
```  
// C4702b.cpp  
// compile with: /W4 /EHsc  
#include <iostream>  
  
using namespace std;  
extern "C" __declspec(dllexport) void Function2(){}  
  
int main() {  
   try {  
      Function2();  
   }  
   catch (...) {  
      cout << "Exp: Function2!" << endl;   // C4702  
   }  
}  
```
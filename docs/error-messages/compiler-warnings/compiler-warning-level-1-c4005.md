---
title: "編譯器警告 (層級 1) C4005 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4005"
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 巨集重複定義  
  
 巨集識別項定義了兩次。  編譯器 \(Compiler\) 使用第二個巨集定義。  
  
### 若要修正，請檢查下列可能原因  
  
1.  在命令列上定義巨集且程式碼中使用了 `#define` 指示詞。  
  
2.  從包含檔匯入巨集。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  移除其中一個定義。  
  
2.  在第二個定義前使用 [\#undef](../../preprocessor/hash-undef-directive-c-cpp.md) 指示詞。  
  
 下列範例會產生 C4005：  
  
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
---
title: "編譯器警告 (層級 1) C4258 | Microsoft Docs"
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
  - "C4258"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4258"
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4258
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable' : 已忽略來自 for 迴圈的定義; 使用封閉範圍的定義  
  
 在 [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) 和 [\/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 之下，[for](../../cpp/for-statement-cpp.md) 迴圈 \(Loop\) 中定義的變數在 **for** 迴圈結束時超出範圍。  如果變數與迴圈變數的名稱相同，但是是在封閉迴圈中定義的，而在包含 **for** 迴圈的範圍中再度被使用，就會發生此錯誤。  例如：  
  
```  
// C4258.cpp  
// compile with: /Zc:forScope /W1  
int main()  
{  
   int i;  
   {  
      for (int i =0; i < 1; i++)  
         ;  
      i = 20;   // C4258 i (in for loop) has gone out of scope  
   }  
}  
```
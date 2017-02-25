---
title: "編譯器警告 (層級 1) C4744 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4744"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4744"
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 1) C4744
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' 在 'file1' 和 'file2' 中有不同的型別: 'type1' 和 'type2'  
  
 在兩個檔案中參考或定義的外部變數在這兩個檔案中有不同的型別。若要解決這個問題，可讓型別定義相同，或在其中一個檔案裡變更變數名稱。  
  
 只有當檔案是以 \/GL 編譯時，才會發出 C4744。如需詳細資訊，請參閱[\/GL \(整個程式最佳化\)](../../build/reference/gl-whole-program-optimization.md)。  
  
> [!NOTE]
>  C4744 一般是發生在 C \(而不是 C\+\+\) 檔案中，因為在 C\+\+ 中，變數名稱是以型別資訊加以裝飾。當 \(下面\) 範例是編譯為 C\+\+ 時，您會接到連結器錯誤 LNK2019。  
  
## 範例  
 這個範例包含第一個定義。  
  
```  
// C4744.c  
// compile with: /c /GL  
int global;  
```  
  
## 範例  
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
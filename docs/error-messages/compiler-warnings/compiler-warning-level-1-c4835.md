---
title: "編譯器警告 (層級 1) C4835 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4835"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4835"
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器警告 (層級 1) C4835
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable' : 所匯出資料的初始設定式，必須等到 Managed 程式碼在主機組件中第一次執行之後才會執行  
  
 在 Managed 元件之間存取資料時，建議您不要使用原生 C\+\+ 匯入和匯出機制。  而要改在 Managed 型別中宣告資料成員，並在用戶端中以 `#using` 參考中繼資料。  如需詳細資訊，請參閱[\#using 指示詞](../../preprocessor/hash-using-directive-cpp.md)。  
  
## 範例  
 下列範例會產生 C4835。  
  
```  
// C4835.cpp  
// compile with: /W1 /clr /LD  
int f() { return 1; }  
int n = 9;  
  
__declspec(dllexport) int m = f();   // C4835  
__declspec(dllexport) int *p = &n;   // C4835  
```  
  
## 範例  
 以下範例會使用來自前一個範例中的元件組建，顯示變數的值並非必須有的值。  
  
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
  
  **0**  
**268456008**
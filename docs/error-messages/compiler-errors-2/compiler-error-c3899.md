---
title: "編譯器錯誤 C3899 | Microsoft Docs"
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
  - "C3899"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3899"
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3899
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : initonly 資料成員不允許直接在類別 'class' 平行區域之內使用 l\-value  
  
 [initonly](../../dotnet/initonly-cpp-cli.md) 資料成員無法在 [parallel](../../parallel/openmp/reference/parallel.md) 區域中的建構函式部分內進行初始設定。這是因為編譯器進行該程式碼的內部重新配置，而有效地使得它不再是建構函式的一部分。  
  
 若要解決，請初始設定建構函式中的 initonly 資料成員，但是在平行區域之外。  
  
## 範例  
 下列範例會產生 C3899。  
  
```  
// C3899.cpp  
// compile with: /clr /openmp  
#include <omp.h>   
  
public ref struct R {  
   initonly int x;  
   R() {  
      x = omp_get_thread_num() + 1000;   // OK  
      #pragma omp parallel num_threads(5)  
      {  
         // cannot assign to 'x' here  
         x = omp_get_thread_num() + 1000;   // C3899  
         System::Console::WriteLine("thread {0}", omp_get_thread_num());  
      }  
      x = omp_get_thread_num() + 1000;   // OK  
   }  
};  
  
int main() {  
   R^ r = gcnew R;  
   System::Console::WriteLine(r->x);  
}  
```
---
title: "編譯器錯誤 C3020 | Microsoft Docs"
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
  - "C3020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3020"
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : OpenMP 'for' 迴圈的索引變數不可在迴圈主體內修改  
  
 OpenMP `for` 迴圈不可以修改 `for` 迴圈主體中的索引 \(迴圈計數器\)。  
  
 下列範例會產生 C3020：  
  
```  
// C3020.cpp  
// compile with: /openmp  
int main() {  
   int i = 0, n = 3;  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      for (i = 0; i < 10; i += n)  
         i *= 2;   // C3020  
         // try the following line instead  
         // n++;  
   }  
}  
```  
  
 以 [lastprivate](../../parallel/openmp/reference/lastprivate.md) 宣告的變數不可以用來當做並列迴圈之內的索引。  
  
 下列範例為第二個 lastprivate 提供 C3020，因為該 lastprivate 會將觸發寫入至迴圈最外面之內的 idx\_a 中。  第一個 lastprivate 不會產生錯誤，因為 lastprivate 會觸發寫入至迴圈最外面之外的 idx\_a \(就技術上而言，是在最後反覆運算法的最尾端\)。  下列範例會產生 C3020。  
  
```  
// C3020b.cpp  
// compile with: /openmp /c  
float a[100][100];  
int idx_a, idx_b;  
void test(int first, int last)  
{  
   #pragma omp parallel for lastprivate(idx_a)  
   for (idx_a = first; idx_a <= last; ++idx_a) {  
      #pragma omp parallel for lastprivate(idx_a)   // C3020  
      for (idx_b = first; idx_b <= last; ++idx_b) {  
         a[idx_a][idx_b] += 1.0f;  
      }  
   }  
}  
```  
  
 下列範例示範可能的解決方式：  
  
```  
// C3020c.cpp  
// compile with: /openmp /c  
float a[100][100];  
int idx_a, idx_b;  
void test(int first, int last)  
{  
   #pragma omp parallel for lastprivate(idx_a)  
   for (idx_a = first; idx_a <= last; ++idx_a) {  
      #pragma omp parallel for lastprivate(idx_b)  
      for (idx_b = first; idx_b <= last; ++idx_b) {  
         a[idx_a][idx_b] += 1.0f;  
      }  
   }  
}  
```
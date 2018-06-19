---
title: 編譯器錯誤 C3020 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3020
dev_langs:
- C++
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a9c942f6b1459cbdb88561b749290eb47d3cfb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245364"
---
# <a name="compiler-error-c3020"></a>編譯器錯誤 C3020
'var': OpenMP 'for' 迴圈索引變數不可修改迴圈主體中  
  
 OpenMP`for`迴圈也許不能修改的本文中的索引 （迴圈計數器）`for`迴圈。  
  
 下列範例會產生 C3020:  
  
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
  
 宣告變數[lastprivate](../../parallel/openmp/reference/lastprivate.md)不能當做平行化迴圈內的索引。  
  
 下列範例會提供 C3020 的第二個 lastprivate，因為該 lastprivate 將會觸發寫入 idx_a 內最外層迴圈。 第一個 lastprivate 不會產生錯誤，因為該 lastprivate 觸發寫入外部最外層 idx_a for 迴圈 （技術上來說，在最後一個反覆項目的結尾）。 下列範例會產生 C3020。  
  
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
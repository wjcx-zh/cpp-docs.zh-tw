---
title: "noalias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "noalias"
  - "noalias_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], noalias"
  - "noalias __declspec 關鍵字"
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# noalias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 `noalias` 表示函式呼叫不修改也不參考可見的全域狀態，只會修改指標參數指向 `directly` 的記憶體 \(第一層間接取值\)。  
  
 如果函式標註為 `noalias`，則除了參數本身外，最佳化程式可以假設函式內只參考或修改指標參數的第一層間接取值。  這個可見的全域狀態是在編譯範圍外未定義或未參考的所有資料，而且不會採用其位址。  編譯範圍是所有原始程式檔 \([\/LTCG \(連結時間產生程式碼\)](../build/reference/ltcg-link-time-code-generation.md) 建置\) 或單一原始程式檔 \(非**\/LTCG** 建置\)。  
  
## 範例  
 下列範例示範使用 `__declspec(restrict)` 和 `__declspec(noalias)`。  通常，從 `malloc` 傳回的記憶體是 `restrict` 和 `noalias`，因為已適當地裝飾 CRT 標頭。  
  
 不過，在本範例中，`mempool` 和 `memptr`  指標是全域的，所以編譯器不保證記憶體不受別名限制。  裝飾以 `__declspec(restrict)` 傳回指標的函式可讓編譯器知道傳回值所指向的記憶體沒有別名。  
  
 裝飾範例中以 `__declspec(noalias)` 存取記憶體的函式可讓編譯器知道，除了透過其參數清單中的指標外，此函式不會干擾全域狀態。  
  
```  
// declspec_noalias.c   
#include <stdio.h>  
#include <stdlib.h>  
  
#define M 800  
#define N 600  
#define P 700  
  
float * mempool, * memptr;  
  
__declspec(restrict) float * ma(int size)  
{  
    float * retval;  
    retval = memptr;  
    memptr += size;  
    return retval;  
}  
  
__declspec(restrict) float * init(int m, int n)  
{  
    float * a;  
    int i, j;  
    int k=1;  
  
    a = ma(m * n);  
    if (!a) exit(1);  
    for (i=0; i<m; i++)  
        for (j=0; j<n; j++)  
            a[i*n+j] = 0.1/k++;  
    return a;  
}  
  
__declspec(noalias) void multiply(float * a, float * b, float * c)  
{  
    int i, j, k;  
  
    for (j=0; j<P; j++)  
        for (i=0; i<M; i++)  
            for (k=0; k<N; k++)  
                c[i * P + j] =   
                          a[i * N + k] *   
                          b[k * P + j];  
}  
  
int main()  
{  
    float * a, * b, * c;  
  
    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));  
  
    if (!mempool)   
    {  
        puts("ERROR: Malloc returned null");  
        exit(1);  
    }  
  
    memptr = mempool;  
    a = init(M, N);  
    b = init(N, P);  
    c = init(M, P);  
  
    multiply(a, b, c);  
}  
```  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)
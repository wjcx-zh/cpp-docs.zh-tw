---
title: "_mm_insert_si64、_mm_inserti_si64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_inserti_si64"
  - "_mm_insert_si64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insertq 指令"
  - "內建 _mm_insert_si64"
  - "內建 _mm_inserti_si64"
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _mm_insert_si64、_mm_inserti_si64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生`insertq`指令，從第二個運算元中插入第一個運算元的位元。  
  
## 語法  
  
```  
__m128i _mm_insert_si64(  
   __m128i Source1,  
   __m128i Source2  
);  
__m128i _mm_inserti_si64(  
   __m128i Source1,  
   __m128i Source2  
   int Length,  
   int Index  
);  
```  
  
#### 參數  
 \[in\]`Source1`  
 在其下方的 64 位元欄位插入輸入資料有 128 位元欄位。  
  
 \[in\] `Source2`  
 若要在其低位元中插入資料的 128 位元欄位。  對於`_mm_insert_si64`，也會包含在其高的位元欄位描述元。  
  
 \[in\] `Length`  
 整數常數，指定要插入的欄位的長度。  
  
 \[in\] `Index`  
 將指定的資料插入的欄位的最小顯著性位元索引的整數常數。  
  
## 傳回值  
 128 位元欄位，其較低的 64 位元會包含原始低 64 位元的`Source1`與指定的位元欄位被取代的低位元的`Source2`。  傳回值的較高的 64 位元是未定義的。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_mm_insert_si64`|SSE4a|  
|`_mm_inserti_si64`|SSE4a|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建會產生`insertq`指令來插入位元`Source2`到`Source1`。  有內建的這兩個版本： `_mm_inserti_si64`，是立即的版本，以及`_mm_insert_si64`是一個非直接。  每個版本從 Source2 中擷取到指定長度的位元欄位，並將它插入 source1，而使得。  已解壓縮的位元是 Source2 的最小顯著性位元。  Source1，而欄位使得這些位元插入是由長度和定義其最小顯著性的位元的索引。  長度與索引值取自 mod 64，因此 127\-1 之間會被解譯為 63。  如果 \(精簡\) 位元索引和 \(精簡\) 的欄位長度的總和大於 64，結果會是未定義。  欄位長度為零的值會解譯為 64。  如果欄位長度和位元索引的這兩個零，位元 63:0 `Source2`就會插入`Source1`。  如果欄位長度為零，但位元索引為非零，則結果為未定義。  
  
 在呼叫 \_mm\_insert\_si64 時，欄位長度都包含在 \[位元 77:72 的 Source2 和位元 69:64 中的索引。  
  
 如果您呼叫`_mm_inserti_si64`使用編譯器無法判斷是整數常數的引數，則編譯器會產生程式碼，將封裝插入 xmm 暫存器的那些值，然後呼叫`_mm_insert_si64`。  
  
 若要判斷硬體支援`insertq`指令呼叫`__cpuid`與內建`InfoType=0x80000001` ，並檢查位元 6 的`CPUInfo[2] (ECX)`。  這個位元會支援指令時，若為 1 和 0 否則。  如果您執行的程式碼會使用此內建不支援的硬體上`insertq`指令時，結果會發生無法預期。  
  
## 範例  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source1, source2, source3, result1, result2, result3;  
  
int  
main()  
{  
  
    __int64 mask;  
  
    source1.ui64[0] = 0xffffffffffffffffll;  
    source2.ui64[0] = 0xfedcba9876543210ll;  
    source2.ui64[1] = 0xc10;  
    source3.ui64[0] = source2.ui64[0];  
  
    result1.m = _mm_insert_si64 (source1.m, source2.m);  
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);  
    mask = 0xffff << 12;  
    mask = ~mask;  
    result3.ui64[0] = (source1.ui64[0] & mask) |  
                      ((source2.ui64[0] & 0xffff) << 12);  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
  
}  
```  
  
  **result1 \= 0xfffffffff3210fff result2 \= 0xfffffffff3210fff result3 \= 0xfffffffff3210fff**   
## 結束 Microsoft 特定  
 藉由收益進階微裝置，及版權 2007年.人所有之商標。  重製與收益進階微裝置，及來自的使用權限.  
  
## 請參閱  
 [\_mm\_extract\_si64，\_mm\_extracti\_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
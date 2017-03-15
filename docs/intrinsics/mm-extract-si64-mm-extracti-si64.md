---
title: "_mm_extract_si64，_mm_extracti_si64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_extracti_si64"
  - "_mm_extract_si64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "extrq 指令"
  - "_mm_extracti_si64 指令"
  - "_mm_extract_si64 指令"
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mm_extract_si64，_mm_extracti_si64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生`extrq`用來從低的 64 位元的第一個引數擷取指定的位元的指令。  
  
## 語法  
  
```  
__m128i _mm_extract_si64(  
   __m128i Source,  
   __m128i Descriptor  
);  
__m128i _mm_extracti_si64(  
   __m128i Source,  
   int Length,  
   int Index  
);  
```  
  
#### 參數  
 \[in\]`Source`  
 在其下方的 64 位元的輸入資料有 128 位元欄位。  
  
 \[in\] `Descriptor`  
 128 位元欄位，描述要擷取的位元欄位。  
  
 \[in\] `Length`  
 指定要擷取的欄位長度的整數。  
  
 \[in\] `Index`  
 此整數用以指定要擷取的欄位索引  
  
## 傳回值  
 128 位元欄位與擷取的欄位，其最小顯著性的位元數。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`_mm_extract_si64`|SSE4a|  
|`_mm_extracti_si64`|SSE4a|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 此內建會產生`extrq`指令來擷取位元`Source`。有內建的這兩個版本： `_mm_extracti_si64`是立即的版本，以及`_mm_extract_si64`是一個非直接。  從擷取每個版本`Source`由其長度和其最小顯著性的位元的索引定義一個位元欄位。  長度與索引值取自 mod 64，因此 127\-1 之間會被解譯為 63。  如果索引 \(精簡\) 和 \(精簡\) 的欄位長度的總和大於 64，結果會是未定義。  欄位長度為零的值會解譯為 64。  如果欄位長度和位元索引的這兩個零，位元 63:0 `Source`會解壓縮。  如果欄位長度為零，但位元索引為非零，則結果為未定義。  
  
 在呼叫 \_mm\_extract\_si64， `Descriptor`包含位元 13: 8 以及欄位的長度要 bits 5: 0 中擷取的資料中的索引。.  
  
 如果您呼叫`_mm_extracti_si64`引數，編譯器無法判斷是整數常數編譯器會產生程式碼，將封裝插入 xmm 暫存器的那些值 \(`Descriptor`\) 以及呼叫`_mm_extract_si64`。  
  
 若要判斷硬體支援`extrq`指令，請打`__cpuid`與內建`InfoType=0x80000001` ，並檢查位元 6 的`CPUInfo[2] (ECX)`。  這個位元會支援指令時，若為 1 和 0 否則。  如果您執行程式碼所使用的不支援此內建硬體`extrq`指令時，結果會發生無法預期。  
  
## 範例  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source, descriptor, result1, result2, result3;  
  
int  
main()  
{  
    source.ui64[0] =     0xfedcba9876543210ll;  
    descriptor.ui64[0] = 0x0000000000000b1bll;  
  
    result1.m = _mm_extract_si64 (source.m, descriptor.m);  
    result2.m = _mm_extracti_si64(source.m, 27, 11);  
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
}  
```  
  
  **result1 \= 0x30eca86 result2 \= 0x30eca86 result3 \= 0x30eca86**   
## 結束 Microsoft 特定  
 藉由收益進階微裝置，及版權 2007年.人所有之商標。  重製與收益進階微裝置，及來自的使用權限.  
  
## 請參閱  
 [\_mm\_insert\_si64、\_mm\_inserti\_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
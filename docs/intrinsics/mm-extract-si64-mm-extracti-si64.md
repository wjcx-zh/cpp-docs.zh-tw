---
title: "_mm_extract_si64，_mm_extracti_si64 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mm_extracti_si64
- _mm_extract_si64
dev_langs: C++
helpviewer_keywords:
- extrq instruction
- _mm_extracti_si64 intrinsic
- _mm_extract_si64 intrinsic
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cc28de10a2a0d53ee87920d511ea894ad517a79a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mmextractsi64-mmextractisi64"></a>_mm_extract_si64，_mm_extracti_si64
**Microsoft 特定的**  
  
 會產生`extrq`指令，以便從其第一個引數的 64 低位元擷取指定的位元。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 [輸入] `Source`  
 具有輸入資料中其較低的 64 位元的 128 位元欄位。  
  
 [in]`Descriptor`  
 128 位元欄位，描述要擷取的位元欄位。  
  
 [in]`Length`  
 整數，指定要擷取之欄位的長度。  
  
 [in]`Index`  
 整數，指定要擷取之欄位的索引  
  
## <a name="return-value"></a>傳回值  
 具有擷取欄位在其最小顯著性位元的 128 位元欄位。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_mm_extract_si64`|SSE4a|  
|`_mm_extracti_si64`|SSE4a|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此內建函式會產生`extrq`指令，以便擷取從`Source`。這兩個版本都內建：`_mm_extracti_si64`是即時的版本，和`_mm_extract_si64`是非直接。  每個版本會從擷取`Source`它的長度，以及其最小顯著性位元的索引所定義的位元欄位。 長度與索引的值取自 mod 64，因此解譯為 63 的-1 到 127 之間。 如果 （降低） 的索引和 （縮小） 的欄位長度的總和大於 64，結果會是未定義。 欄位長度為零的值會解譯為 64。 如果欄位長度和位元索引的這兩個零個、 位元 63:0`Source`會解壓縮。 如果欄位長度為零，但位元索引為非零，則結果會是未定義。  
  
 _Mm_extract_si64，呼叫`Descriptor`包含 13:8 位元長度和欄位擷取在位元 5:0 中的資料中的索引...  
  
 如果您呼叫`_mm_extracti_si64`編譯器無法判斷是整數常數的引數與編譯器會產生程式碼，將封裝這些值入的 XMM 暫存器 (`Descriptor`) 並呼叫`_mm_extract_si64`。  
  
 若要決定硬體支援的`extrq`指示，請呼叫`__cpuid`與內建`InfoType=0x80000001`並檢查位元 6 的`CPUInfo[2] (ECX)`。 此位元會支援該指令，則為 1 和 0 否則。 如果您執行程式碼會使用不支援這個內建硬體`extrq`指令，結果會產生無法預測。  
  
## <a name="example"></a>範例  
  
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
  
```Output  
result1 = 0x30eca86  
result2 = 0x30eca86  
result3 = 0x30eca86  
```  
  
**結束 Microsoft 特定的**  
 進階微裝置，inc.著作權 2007著作權所有，並保留一切權利。 重製進階微裝置，Inc.的權限。  
  
## <a name="see-also"></a>請參閱  
 [_mm_insert_si64、 _mm_inserti_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
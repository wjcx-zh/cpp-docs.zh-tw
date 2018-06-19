---
title: _mm_cvttss_si64x |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvttss_si64x
dev_langs:
- C++
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4fd8aebb3f9a4f0078c8174aa25b9abb9378f1b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333625"
---
# <a name="mmcvttsssi64x"></a>_mm_cvttss_si64x
**Microsoft 特定的**  
  
 發出延伸 x64 版本的 64 位元整數的截斷單精確度浮點號碼轉換 (`cvttss2si`) 指令。  
  
## <a name="syntax"></a>語法  
  
```  
__int64 _mm_cvttss_si64x(   
   __m128 value   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `value`  
 `__m128`結構，其中包含單精確度浮點值。  
  
## <a name="return-value"></a>傳回值  
 第一個浮點值轉換為 64 位元整數的結果。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_mm_cvttss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 內建函式的不同`_mm_cvtss_si64x`只有一個不正確的轉換會截斷趨近於零。 因為`__m128`結構表示的 XMM 暫存器，產生的指示將資料從 xmm 暫存器移至系統記憶體。  
  
 此常式僅可作為內建常式使用。  
  
## <a name="example"></a>範例  
  
```  
// _mm_cvttss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvttss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] = { 101.5, 200.75,  
                                          300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvttss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
```Output  
101  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [__m128](../cpp/m128.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
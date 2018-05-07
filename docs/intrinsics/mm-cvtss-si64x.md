---
title: _mm_cvtss_si64x |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvtss_si64x
dev_langs:
- C++
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 665c52fc0dd0645e25d3014cc28f9fdfba344e2d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x
**Microsoft 特定的**  
  
 會產生[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]擴充的版本轉換純量單一精確度浮點數為 64 位元整數 (`cvtss2si`) 指令。  
  
## <a name="syntax"></a>語法  
  
```  
__int64 _mm_cvtss_si64x(   
   __m128 value   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `value`  
 `__m128`結構，其中包含的浮動點值。  
  
## <a name="return-value"></a>傳回值  
 64 位元整數，第一個浮點值轉換成整數的結果。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_mm_cvtss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 結構值的第一個項目會轉換成整數並傳回。 在 MXCSR 捨入的控制位元用來決定捨入的行為。 預設的捨入模式為四捨五入到最接近捨入為偶數，如果的小數部分為 0.5。 因為`__m128`結構代表 xmm 暫存器的 XMM 暫存器，此內建函式會接受的值，並將它寫入至系統記憶體。  
  
 此常式僅可作為內建常式使用。  
  
## <a name="example"></a>範例  
  
```  
// _mm_cvtss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] =  
                           { 101.25, 200.75, 300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvtss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
```Output  
101  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [__m128d](../cpp/m128d.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
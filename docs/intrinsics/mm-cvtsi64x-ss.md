---
title: _mm_cvtsi64x_ss |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvtsi64x_ss
dev_langs:
- C++
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb529e8aab204df85de2da0a2fdf4c820964239
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340602"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss
**Microsoft 特定的**  
  
 會產生[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]的純量單精確度浮點值轉換的 64 位元整數的擴充的版本 (`cvtsi2ss`) 指令。  
  
## <a name="syntax"></a>語法  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `a`  
 `__m128`結構，其中包含四個單精確度浮點值。  
  
 [輸入] `b`  
 要轉換成浮點值的 64 位元整數。  
  
## <a name="return-value"></a>傳回值  
 `__m128`結構其第一個浮點值轉換的結果。 其他三個值都會複製的相同`a`。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_mm_cvtsi64x_ss`|X64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 `__m128`結構代表 xmm 暫存器，因此這個內建的允許值`b`從系統記憶體移入的 XMM 暫存器。  
  
 此常式僅可作為內建常式使用。  
  
## <a name="example"></a>範例  
  
```  
// _mm_cvtsi64x_ss.cpp  
// processor: x64  
  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtsi64x_ss)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    a.m128_f32[0] = 0;  
    a.m128_f32[1] = 0;  
    a.m128_f32[2] = 0;  
    a.m128_f32[3] = 0;  
    a = _mm_cvtsi64x_ss(a, b);  
  
    printf_s( "%lf %lf %lf %lf\n",  
              a.m128_f32[0], a.m128_f32[1],   
              a.m128_f32[2], a.m128_f32[3] );  
}  
```  
  
```Output  
54.000000 0.000000 0.000000 0.000000  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [__m128](../cpp/m128.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
---
title: __mulh |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __mulh
dev_langs:
- C++
helpviewer_keywords:
- __mulh intrinsic
ms.assetid: cd2ab093-9ef6-404d-ac34-0bee033882f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae312de1311bfe068ac48838f2720bd8a2a83e53
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mulh"></a>__mulh
**Microsoft 特定的**  
  
 傳回兩個 64 位元帶正負號整數的產品的高 64 個位元。  
  
## <a name="syntax"></a>語法  
  
```  
__int64 __mulh(   
   __int64 a,   
   __int64 b   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `a`  
 要相乘的第一個數字。  
  
 [in] `b`  
 要相乘的第二個數字。  
  
## <a name="return-value"></a>傳回值  
 相乘的 128 位元結果的 64 高位元。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__mulh`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 此常式僅可作為內建常式使用。  
  
## <a name="example"></a>範例  
  
```  
// mulh.cpp  
// processor: x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic (__mulh)  
  
int main()  
{  
    __int64 a = 0x0fffffffffffffffI64;  
    __int64 b = 0xf0000000I64;  
  
    __int64 result = __mulh(a, b); // the high 64 bits  
    __int64 result2 = a * b; // the low 64 bits  
  
    printf_s(" %#I64x * %#I64x = %#I64x%I64x\n",  
             a, b, result, result2);  
}  
```  
  
```Output  
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
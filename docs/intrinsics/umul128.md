---
title: "_umul128 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __umul128
dev_langs: C++
helpviewer_keywords: __umul128 intrinsic
ms.assetid: 13684df3-3ac7-467c-b258-a0e93bc490b5
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 81a408540d2606cb81d92a3e93cbcff888d4a3e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="umul128"></a>_umul128
**Microsoft 特定的**  
  
 將兩個作為前兩個引數傳入的 64 位元不帶正負號整數相乘，並將乘積的 64 高位元置於 `HighProduct` 所指向的 64 位元不帶正負號整數中，然後傳回乘積的 64 低位元。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned __int64 _umul128(   
   unsigned __int64 Multiplier,   
   unsigned __int64 Multiplicand,   
   unsigned __int64 *HighProduct   
);  
```  
  
#### <a name="parameters"></a>參數  
 [in] `Multiplier`  
 要相乘的第一個 64 位元整數。  
  
 [in] `Multiplicand`  
 要相乘的第二個 64 位元整數。  
  
 [輸出] `HighProduct`  
 乘積的 64 高位元。  
  
## <a name="return-value"></a>傳回值  
 乘積的 64 低位元。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|頁首|  
|---------------|------------------|------------|  
|`_umul128`|ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
  
## <a name="example"></a>範例  
  
```  
// umul128.c  
// processor: IPF, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_umul128)  
  
int main()  
{  
    unsigned __int64 a = 0x0fffffffffffffffI64;  
    unsigned __int64 b = 0xf0000000I64;  
    unsigned __int64 c, d;  
  
    d = _umul128(a, b, &c);  
  
    printf_s("%#I64x * %#I64x = %#I64x%I64x\n", a, b, c, d);  
}  
```  
  
```Output  
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000  
```  
  
**END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
---
title: __rdtsc |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtsc
dev_langs:
- C++
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81b47a76b3045465d8c3c5c21a87020ee1e74a69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="rdtsc"></a>__rdtsc
**Microsoft 特定的**  
  
 會產生`rdtsc`指令，它會傳回處理器時間戳記。 處理器時間戳記記錄自上次重設的時脈週期數目。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned __int64 __rdtsc();  
```  
  
## <a name="return-value"></a>傳回值  
 64 位元不帶正負號的整數，代表滴答計數。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__rdtsc`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 這個常式可只做為內建函式。  
  
 在這個層代的硬體 TSC 值的解譯不同於在舊版的[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]。 請參閱硬體手冊，如需詳細資訊。  
  
## <a name="example"></a>範例  
  
```  
// rdtsc.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__rdtsc)  
  
int main()  
{  
    unsigned __int64 i;  
    i = __rdtsc();  
    printf_s("%I64d ticks\n", i);  
}  
```  
  
```Output  
3363423610155519 ticks  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
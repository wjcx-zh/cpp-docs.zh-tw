---
title: _bittest，_bittest64 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _bittest64
- _bittest_cpp
- _bittest64_cpp
- _bittest
dev_langs:
- C++
helpviewer_keywords:
- _bittest intrinsic
- _bittest64 intrinsic
- bt instruction
ms.assetid: 15e62afb-abea-4ee7-a6b1-13efa2034937
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71b2259e7eecd820d35527a6ab8908f274e3e287
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334249"
---
# <a name="bittest-bittest64"></a>_bittest, _bittest64
**Microsoft 特定的**  
  
產生 `bt` 指令，該指令會檢查位址 `b` 的位置 `a` 中的位元，並傳回該位元的值。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned char _bittest(  
   long const *a,  
   long b  
);  
unsigned char _bittest64(  
   __int64 const *a,  
   __int64 b  
);  
```  
  
### <a name="parameters"></a>參數  
[輸入] `a`  
要檢查的記憶體指標。  
  
[in] `b`  
要測試的位元位置。  
  
### <a name="return-value"></a>傳回值  
位於指定位置的位元。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|頁首|  
|---------------|------------------|------------|  
|`_bittest`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
|`_bittest64`|ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
  
## <a name="remarks"></a>備註  
此常式僅可作為內建常式使用。  
  
## <a name="example"></a>範例  
  
```cpp  
// bittest.cpp  
// processor: x86, ARM, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
long num = 78002;  
  
int main()  
{  
    unsigned char bits[32];  
    long nBit;  
  
    printf_s("Number: %d\n", num);  
  
    for (nBit = 0; nBit < 31; nBit++)  
    {  
        bits[nBit] = _bittest(&num, nBit);  
    }  
  
    printf_s("Binary representation:\n");  
    while (nBit--)  
    {  
        if (bits[nBit])  
            printf_s("1");  
        else  
            printf_s("0");  
    }  
}  
```  
  
```Output  
Number: 78002  
Binary representation:  
0000000000000010011000010110010  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
[編譯器內建](../intrinsics/compiler-intrinsics.md)
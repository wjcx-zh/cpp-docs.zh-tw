---
title: "__ull_rshift |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __ull_rshift
dev_langs: C++
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c0951a930ad5baec5b293aee0fe8e70c0a38a12f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ullrshift"></a>__ull_rshift
**Microsoft 特定的**  
  
 在 x64 上將第二個參數所指定的位元數右邊的第一個參數所指定的 64 位元值。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned __int64 __ull_rshift(   
   unsigned __int64 mask,    
   int nBit   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `mask`  
 要向右移位的 64 位元整數值。  
  
 [輸入] `nBit`  
 要移位 32 在 x86、 模數和模數 x64 上的 64 位元數目。  
  
## <a name="return-value"></a>傳回值  
 遮罩移位`nBit`位元。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__ull_rshift`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 如果第二個參數大於 31 on x86 (在 x64 上為 63)，該數字會採取模數 32 (在 x64 上為 64)，來判斷要移位的位元數目。 `ull`名稱中指出`unsigned long long (unsigned __int64)`。  
  
## <a name="example"></a>範例  
  
```  
// ull_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ull_rshift)  
  
int main()  
{  
   unsigned __int64 mask = 0x100;  
   int nBit = 8;  
   mask = __ull_rshift(mask, nBit);  
   cout << hex << mask << endl;  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
1  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
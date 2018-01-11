---
title: "__ll_rshift |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
dev_langs: C++
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c0bb658051a4eab579e2c0d2fbb4d6bd525381b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="llrshift"></a>__ll_rshift
**Microsoft 特定的**  
  
 將第二個參數所指定的位元數右邊的第一個參數所指定的 64 位元值。  
  
## <a name="syntax"></a>語法  
  
```  
__int64 __ll_rshift(  
   __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `Mask`  
 要向右移位的 64 位元整數值。  
  
 [輸入] `nBit`  
 要移位模數 64，在 x64 上及模數 x86 上的 32 位元數目。  
  
## <a name="return-value"></a>傳回值  
 遮罩移位`nBit`位元。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__ll_rshift`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 如果第二個參數大於 64 x64 (在 x86 上的 32) 上，該數字會採取模數 64 (在 x86 上的 32)，來判斷要移位的位元數目。 `ll`前置詞會指示這是作業，在`long long`、 另一個名稱為`__int64`，64 位元帶正負號的整數類資料類型。  
  
## <a name="example"></a>範例  
  
```  
// ll_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_rshift)  
  
int main()  
{  
   __int64 Mask = - 0x100;  
   int nBit = 4;  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
   Mask = __ll_rshift(Mask, nBit);  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
ffffffffffffff00  
 - 100  
fffffffffffffff0  
 - 10  
```  
  
 **請注意**如果`_ull_rshift`已被使用，向右移位值的 MSB 已經是零，因此想要的結果會尚未取得在負數值的情況下。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)
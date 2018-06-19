---
title: __ll_lshift |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
dev_langs:
- C++
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94cf50287c28fe530df939488c4e707d17aede03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327368"
---
# <a name="lllshift"></a>__ll_lshift
**Microsoft 特定的**  
  
 向左移位指定位元數所提供的 64 位元值。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned __int64 __ll_lshift(  
   unsigned __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `Mask`  
 要向左移位的 64 位元整數值。  
  
 [輸入] `nBit`  
 要移位的位元數。  
  
## <a name="return-value"></a>傳回值  
 遮罩向左旋轉`nBit`位元。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__ll_lshift`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 如果您編譯程式，使用 64 位元架構和`nBit`大於 63，要移位的位元數是`nBit`模數 64。 如果您編譯程式，使用 32 位元架構和`nBit`大於 31，要移位的位元數是`nBit`模數 32。  
  
 `ll`指出的名稱中的 這是作業，在`long long`(`__int64`)。  
  
## <a name="example"></a>範例  
  
```  
// ll_lshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_lshift)  
  
int main()  
{  
   unsigned __int64 Mask = 0x100;  
   int nBit = 8;  
   Mask = __ll_lshift(Mask, nBit);  
   cout << hex << Mask << endl;  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
10000  
```  
  
 **請注意**沒有左的移位作業的不帶正負號的版本。 這是因為`__ll_lshift`已使用不帶正負號的輸入的參數。 與向右移位，不同的是沒有正負號無關的左移，因為結果中的最小顯著性位元一定會設定為零不論移位的值的正負號。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
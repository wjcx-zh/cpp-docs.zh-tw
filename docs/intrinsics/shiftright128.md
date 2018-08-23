---
title: __shiftright128 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __shiftright128
dev_langs:
- C++
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0aa5b4028863ff31084e8d01892a86b990de51fb
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42543103"
---
# <a name="shiftright128"></a>__shiftright128
**Microsoft 專屬**  
  
 移位 128 位元數量，表示兩個距離右邊達 `LowPart` 指定之位元數的 64 位元數量 `HighPart` 和 `Shift`，並傳回結果的較低 64 個位元。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned __int64 __shiftright128(   
   unsigned __int64 LowPart,   
   unsigned __int64 HighPart,   
   unsigned char Shift   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `LowPart`  
 要移位的 128 位元數量的較低 64 個位元。  
  
 [in] `HighPart`  
 要移位的 128 位元數量的較高 64 個位元。  
  
 [in] `Shift`  
 要移位的位元數。  
  
## <a name="return-value"></a>傳回值  
 結果的較低 64 個位元。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__shiftright128`|X64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 `Shift` 值一律為模數 64，使得 (舉例而言) 如果您呼叫 `__shiftright128(0, 1, 64)`，函式將向右移高部分 `0` 個位元，並傳回 `0` 而非 `1` 的低部分，因為將會預期其他值。  
  
## <a name="example"></a>範例  
 如需範例，請參閱[__shiftleft128](../intrinsics/shiftleft128.md)。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [__shiftleft128](../intrinsics/shiftleft128.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
---
title: "__shiftright128 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __shiftright128
dev_langs: C++
helpviewer_keywords: __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 228c624c5c752a7c61178b60f8e75817fff62505
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="shiftright128"></a>__shiftright128
**Microsoft 特定的**  
  
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
|`__shiftright128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 `Shift` 值一律為模數 64，使得 (舉例而言) 如果您呼叫 `__shiftright128(0, 1, 64)`，函式將向右移高部分 `0` 個位元，並傳回 `0` 而非 `1` 的低部分，因為將會預期其他值。  
  
## <a name="example"></a>範例  
 如需範例，請參閱[__shiftleft128](../intrinsics/shiftleft128.md)。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [__shiftleft128](../intrinsics/shiftleft128.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)
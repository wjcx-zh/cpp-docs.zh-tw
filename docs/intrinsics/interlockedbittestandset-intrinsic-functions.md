---
title: "_interlockedbittestandset 內建函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _interlockedbittestandset_cpp
- _interlockedbittestandset_HLEAcquire
- _interlockedbittestandset64
- _interlockedbittestandset
- _interlockedbittestandset_rel
- _interlockedbittestandset64_HLEAcquire
- _interlockedbittestandset_HLERelease
- _interlockedbittestandset_acq
- _interlockedbittestandset_nf
- _interlockedbittestandset64_cpp
- _interlockedbittestandset64_HLERelease
dev_langs:
- C++
helpviewer_keywords:
- _interlockedbittestandset intrinsic
- _interlockedbittestandset64 intrinsic
- lock_bts instruction
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 98cb5e8abdb96451de9d6cd39d1659c49ef935b1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="interlockedbittestandset-intrinsic-functions"></a>_interlockedbittestandset 內建函式
**Microsoft 特定的**  
  
 會產生檢查位址 `b` 的位元 `a` 的指令，並傳回其目前的值，再將它設定為 1。  
  
## <a name="syntax"></a>語法  
  
```  
unsigned char _interlockedbittestandset(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_acq(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_HLEAcquire(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_HLERelease(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_nf(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset_rel(  
   long *a,  
   long b  
);  
unsigned char _interlockedbittestandset64(  
   __int64 *a,  
   __int64 b  
);  
unsigned char _interlockedbittestandset64_HLEAcquire(  
   __int64 *a,  
   __int64 b  
);  
unsigned char _interlockedbittestandset64_HLERelease(  
   __int64 *a,  
   __int64 b  
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `a`  
 要檢查的記憶體指標。  
  
 [in] `b`  
 要測試的位元位置。  
  
## <a name="return-value"></a>傳回值  
 設定之前位置 `b` 的位元值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|頁首|  
|---------------|------------------|------------|  
|`_interlockedbittestandset`|x86、 ARM、 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
|`_interlockedbittestandset_acq`, `_interlockedbittestandset_nf`, `_interlockedbittestandset_rel`|ARM|\<intrin.h>|  
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h>|  
|`_interlockedbittestandset64`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h>|  
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h>|  
  
## <a name="remarks"></a>備註  
 在 x86 和 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 處理器上，這些內建函式會使用 `lock bts` 指令讀取，並將指定的位元設為 1。 此作業是不可部分完成的。  
  
 在 ARM 處理器上，搭配取得和釋放語意的 `_acq` 和 `_rel` 字尾使用內建函式，例如在重要區段的開頭和結尾處。 搭配 `_nf` (「無範圍」) 字尾的 ARM 內建函式不會當做記憶體屏障。  
  
 在支援 Hardware Lock Elision (HLE) 指令的 Intel 處理器上，搭配 `_HLEAcquire` 和 `_HLERelease` 字尾的內建函式會包含對處理器的提示，提示其可以藉由消除硬體中鎖定寫入 (lock write) 的階段以加速效能。 如果這些內建函式在不支援 HLE 的處理器上被呼叫，則會忽略提示。  
  
 這些常式僅以內建函式的形式供您使用。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)
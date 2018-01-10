---
title: "_InterlockedCompareExchangePointer 內建函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _InterlockedCompareExchangePointer_HLERelease
- _InterlockedCompareExchangePointer_rel
- _InterlockedCompareExchangePointer_acq_cpp
- _InterlockedCompareExchangePointer
- _InterlockedCompareExchangePointer_cpp
- _InterlockedCompareExchangePointer_np
- _InterlockedCompareExchangePointer_rel_cpp
- _InterlockedCompareExchangePointer_HLEAcquire
- _InterlockedCompareExchangePointer_acq
- _InterlockedCompareExchangePointer_nf
dev_langs: C++
helpviewer_keywords:
- InterlockedCompareExchangePointer_acq intrinsic
- _InterlockedCompareExchangePointer_rel intrinsic
- _InterlockedCompareExchangePointer_acq intrinsic
- InterlockedCompareExchangePointer_rel intrinsic
- InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_HLERelease intrinsic
- _InterlockedCompareExchangePointer_HLEAcquire intrinsic
- _InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_nf intrinsic
- _InterlockedCompareExchangePointer_np intrinsic
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9228422886c211bb6a7c153abdfd4d48ecca7f19
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="interlockedcompareexchangepointer-intrinsic-functions"></a>_InterlockedCompareExchangePointer 內建函式
**Microsoft 特定的**  
  
 如果 `Exchange` 與 `Destination` 相等，則執行不可部分完成作業，可將 `Comparand` 位址儲存在 `Destination` 位址中。  
  
## <a name="syntax"></a>語法  
  
```  
void * _InterlockedCompareExchangePointer (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_acq (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_HLEAcquire (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_HLERelease (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_nf (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_np (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
long _InterlockedCompareExchangePointer_rel (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
```  
  
#### <a name="parameters"></a>參數  
 [in、out] `Destination`  
 指向目的地值之指標的指標。 會忽略正負號。  
  
 [in] `Exchange`  
 交換指標。 會忽略正負號。  
  
 [in] `Comparand`  
 比較目的地的指標。 會忽略正負號。  
  
## <a name="return-value"></a>傳回值  
 傳回值是目的地的初始值。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|頁首|  
|---------------|------------------|------------|  
|`_InterlockedCompareExchangePointer`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM|\<iiintrin.h >|  
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h >|  
  
## <a name="remarks"></a>備註  
 `_InterlockedCompareExchangePointer` 執行 `Destination` 位址與`Comparand` 位址的不可部分完成比較。 如果 `Destination` 位址等於 `Comparand` 位址，`Exchange` 位址會儲存在 `Destination` 所指定的位址中。 否則，不會執行任何作業。  
  
 `_InterlockedCompareExchangePointer`提供 Win32 的編譯器內建支援[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] [_InterlockedCompareExchangePointer](http://msdn.microsoft.com/library/ff547863.aspx)函式。  
  
 如需如何使用的範例`_InterlockedCompareExchangePointer`，請參閱[_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。  
  
 在 ARM 平台上，如果您需要取得並發行語意 (例如在關鍵區段的開頭和結尾)，請使用具有 `_acq` 和 `_rel` 後置字元的內建函式。 具有 `_nf` (「沒有圍牆」) 後置字元的 ARM 內建函式不做為記憶體屏障。  
  
 具有 `_np` (「沒有預先擷取」) 後置字元的建函式會防止編譯器插入可能的預先擷取作業。  
  
 在支援 Hardware Lock Elision (HLE) 指令的 Intel 平台上，搭配 `_HLEAcquire` 和 `_HLERelease` 字尾的內建函式會包含對處理器的提示，提示其可以藉由消除硬體中鎖定寫入 (lock write) 的階段以加速效能。 如果在不支援 HLE 的平台上呼叫這些內建函式，會忽略該提示。  
  
 這些常式僅以內建函式的形式供您使用。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [關鍵字](../cpp/keywords-cpp.md)
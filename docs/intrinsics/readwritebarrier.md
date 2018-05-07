---
title: _ReadWriteBarrier |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReadWriteBarrier
dev_langs:
- C++
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 450f8d94510212a430fb5d5a6b4ece061fa8a59c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier
**Microsoft 特定的**  
  
 限制可跨呼叫點，對記憶體存取進行重新排序的編譯器最佳化作業。  
  
> [!CAUTION]
>  `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 編譯器內建物件及`MemoryBarrier` 巨集全部都已被取代，不應該再使用。 用於執行緒間通訊使用機制如[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)和[std::atomic\<T >](../standard-library/atomic.md)，定義所在[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md). 用於硬體存取[/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項，連同[volatile](../cpp/volatile-cpp.md)關鍵字。  
  
## <a name="syntax"></a>語法  
  
```  
void _ReadWriteBarrier(void);  
```  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_ReadWriteBarrier`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 `_ReadWriteBarrier` 內建物件會限制可跨呼叫點，移除記憶體存取或對其進行重新排序的編譯器最佳化作業。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_ReadBarrier](../intrinsics/readbarrier.md)   
 [_WriteBarrier](../intrinsics/writebarrier.md)   
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [關鍵字](../cpp/keywords-cpp.md)
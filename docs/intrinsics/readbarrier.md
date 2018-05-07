---
title: _ReadBarrier |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _ReadBarrier
dev_langs:
- C++
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e188089af114abb3e52ef5c0e289f5c8fa013b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="readbarrier"></a>_ReadBarrier  
  
**Microsoft 特定的**  
  
 限制可跨呼叫點，對記憶體存取作業進行重新排序的編譯器最佳化作業。  
  
> [!CAUTION]
>  `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 編譯器內建物件及`MemoryBarrier` 巨集全部都已被取代，不應該再使用。 用於執行緒間通訊使用機制如[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)和[std::atomic\<T >](../standard-library/atomic.md)中所定義[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md). 用於硬體存取[/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項，連同[volatile](../cpp/volatile-cpp.md)關鍵字。  
  
## <a name="syntax"></a>語法  
  
```  
void _ReadBarrier(void);  
```  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_ReadBarrier`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 `_ReadBarrier` 內建物件會限制可跨呼叫點，移除記憶體存取作業或對其進行重新排序的編譯器最佳化作業。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [關鍵字](../cpp/keywords-cpp.md)
---
title: _ReadWriteBarrier |Microsoft Docs
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
ms.openlocfilehash: f6c0e2e21b18b806a63a2d6ea331a84ab144a6ec
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541391"
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier
**Microsoft 專屬**  
  
 限制可跨呼叫點，對記憶體存取進行重新排序的編譯器最佳化作業。  
  
> [!CAUTION]
>  `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 編譯器內建物件及`MemoryBarrier` 巨集全部都已被取代，不應該再使用。 對於執行緒間通訊使用機制如[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)並[std:: atomic\<T >](../standard-library/atomic.md)，其定義於[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md). 對於硬體存取，請使用[/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項，並搭配[volatile](../cpp/volatile-cpp.md)關鍵字。  
  
## <a name="syntax"></a>語法  
  
```  
void _ReadWriteBarrier(void);  
```  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`_ReadWriteBarrier`|x86、x64|  
  
 **標頭檔** \<intrin.h >  
  
## <a name="remarks"></a>備註  
 `_ReadWriteBarrier` 內建物件會限制可跨呼叫點，移除記憶體存取或對其進行重新排序的編譯器最佳化作業。  
  
**結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_ReadBarrier](../intrinsics/readbarrier.md)   
 [_WriteBarrier](../intrinsics/writebarrier.md)   
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [關鍵字](../cpp/keywords-cpp.md)
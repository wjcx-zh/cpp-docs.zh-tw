---
title: _aligned_free | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_free
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- aligned_free
- _aligned_free
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: d65782fe3d381cfc8916670b3e6db1bf378a6c5d
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="alignedfree"></a>_aligned_free
釋放使用 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 或 [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md) 所配置的記憶體區塊。  
  
## <a name="syntax"></a>語法  
  
```  
void _aligned_free (  
   void *memblock  
);  
```  
  
#### <a name="parameters"></a>參數  
 `memblock`  
 傳回 `_aligned_malloc` 或 `_aligned_offset_malloc` 函式之記憶體區塊的指標。  
  
## <a name="remarks"></a>備註  
 `_aligned_free` 標記為 `__declspec(noalias)`，表示保證函式不會修改全域變數。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md)。  
  
 不同於其他 _aligned CRT 函式，此函式不會驗證其參數。 如果 `memblock` 是 `NULL` 指標，此函式不會執行任何動作。 它不會變更 `errno` 也不會叫用無效的參數處理常式。 如果因為之前未使用 _aligned 函式配置記憶體區塊致使函式發生錯誤，或因為某些無法預見的不幸致使記憶體發生不一致，函式會從 [_RPT、_RPTF、_RPTW、_RPTFW 巨集](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)產生偵錯報告。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_aligned_free`|\<malloc.h>|  
  
## <a name="example"></a>範例  
 如需詳細資訊，請參閱 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料對齊](../../c-runtime-library/data-alignment.md)

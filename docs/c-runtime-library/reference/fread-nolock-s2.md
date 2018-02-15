---
title: _fread_nolock_s2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _fread_nolock_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fread_nolock_s
- stdio/_fread_nolock_s
dev_langs:
- C++
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 438e12cd9a2a4099231e2dfb9c2ba27375811ea7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="freadnolocks"></a>_fread_nolock_s
從資料流讀取資料，但不鎖定其他執行緒。 這版的 [fread_nolock](../../c-runtime-library/reference/fread-nolock.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
```  
size_t _fread_nolock_s(   
   void *buffer,  
   size_t bufferSize,  
   size_t elementSize,  
   size_t elementCount,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>參數  
 `buffer`  
 資料的儲存位置。  
  
 `bufferSize`  
 以位元組為單位的目的緩衝區大小。  
  
 `elementSize`  
 以位元組為單位的讀取項目大小。  
  
 `elementCount`  
 要讀取項目的最大數量。  
  
 `stream`  
 `FILE` 結構的指標。  
  
## <a name="return-value"></a>傳回值  
 請參閱 [fread_s](../../c-runtime-library/reference/fread-s.md)。  
  
## <a name="remarks"></a>備註  
 這個函式為非鎖定版本的 `fread_s`。 它相當於 `fread_s` ，不同之處在於不受保護，不能免於其他執行緒的干擾。 因為它不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這個函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`_fread_nolock_s`|C：\<stdio.h>；C++：\<cstdio> 或 \<stdio.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [_read](../../c-runtime-library/reference/read.md)
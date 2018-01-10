---
title: fwrite | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fwrite
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
f1_keywords: fwrite
dev_langs: C++
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b830dfd7b0a9dace46336f8f02da14fc268daf6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fwrite"></a>fwrite
將資料寫入資料流。  
  
## <a name="syntax"></a>語法  
  
```  
size_t fwrite(  
   const void *buffer,  
   size_t size,  
   size_t count,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>參數  
 `buffer`  
 要寫入之資料的指標。  
  
 `size`  
 項目大小 (位元組)。  
  
 `count`  
 要寫入之項目的最大數量。  
  
 `stream`  
 `FILE` 結構的指標。  
  
## <a name="return-value"></a>傳回值  
 `fwrite` 會傳回實際寫入的完整項目數量，若有發生錯誤，此數量可能會少於 `count`。 此外，若發生錯誤，也無法判斷檔案位置指標。 若 `stream` 或 `buffer` 為 Null 指標，或是 Unicode 模式中指定要寫入奇數位元組，則此函示會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 0。  
  
## <a name="remarks"></a>備註  
 `fwrite` 函式會寫入最多 `count` 的項目數，且每個項目均為 `size` 的長度，並從 `buffer` 寫入至 `stream`。 與 `stream` 相關的檔案指標 (若有的話)，會隨著實際寫入的位元組數而累加。 如果`stream`開啟在文字模式下，每個換行字元會取代為歸位字元-換行字元組。 這種取代不會對傳回值產生影響。  
  
 若在 Unicode 轉譯模式中開啟 `stream`，例如，透過呼叫 `stream` 開啟 `fopen`，並使用包含 `ccs=UNICODE`、`ccs=UTF-16LE` 或 `ccs=UTF-8` 的模式參數；或者此模式已透過使用 `_setmode` 以及包含 `_O_WTEXT`、`_O_U16TEXT` 或 `_O_U8TEXT` 的模式參數變更為 Unicode 轉譯模式：則 `buffer` 會解譯為包含 UTF-16 資料之 `wchar_t` 陣列的指標。 嘗試以此模式寫入奇數位元組會導致參數驗證錯誤。  
  
 因為此函示會鎖定呼叫執行緒，這是安全執行緒。 如需非鎖定版本，請參閱 `_fwrite_nolock`。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|  
|--------------|---------------------|  
|`fwrite`|\<stdio.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [fread](../../c-runtime-library/reference/fread.md) 的範例。  
  
## <a name="see-also"></a>請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [_fwrite_nolock](../../c-runtime-library/reference/fwrite-nolock.md)   
 [_write](../../c-runtime-library/reference/write.md)
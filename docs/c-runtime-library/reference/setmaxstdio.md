---
title: _setmaxstdio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
dev_langs:
- C++
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 3c18b478c83c57a8a3bfd8238b367dbe4846d025
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="setmaxstdio"></a>_setmaxstdio
設定在 `stdio` 層級同時開啟的檔案數目上限。  
  
## <a name="syntax"></a>語法  
  
```  
int _setmaxstdio(  
   int newmax   
);  
```  
  
#### <a name="parameters"></a>參數  
 `newmax`  
 在 `stdio` 層級同時開啟之檔案數目的新上限。  
  
## <a name="return-value"></a>傳回值  
 傳回`newmax`如果成功; 否則為-1。  
  
 如果 `newmax` 小於 `_IOB_ENTRIES` 或大於作業系統中可用的處理常式數目上限，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回 -1，並將 `errno` 設為 `EINVAL`。  
  
 如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_setmaxstdio` 函式會變更可在 `stdio` 層級同時開啟之檔案數目的最大值。  
  
 C 執行階段 I/O 支援在 Win32 平台上的開啟檔案數目，現在會多於舊版本。 最多可以在 [lowio 層級](../../c-runtime-library/low-level-i-o.md)同時開啟 2,048 個檔案 (亦即，透過 `_open`、`_read`、`_write` 等系列 I/O 函式所開啟和存取)。 最多可以在 [stdio 層級](../../c-runtime-library/stream-i-o.md)同時開啟 512 個檔案 (亦即，透過 `fopen`、`fgetc`、`fputc` 等系列 I/O 函式所開啟和存取)。 透過 `_setmaxstdio` 函式，`stdio` 層級的 512 個開啟檔案限制可以增加為最大值 2,048。  
  
 因為 `stdio` 層級函式 (例如 `fopen`) 是根據 `lowio` 函式所建置，所以最大值 2,048 是透過 C 執行階段程式庫同時存取之開啟檔案數目的固定上限。  
  
> [!NOTE]
>  這個上限可能超過特定 Win32 平台和組態所支援的值。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_setmaxstdio`|\<stdio.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 如需 `_setmaxstdio` 的使用範例，請參閱 [_getmaxstdio](../../c-runtime-library/reference/getmaxstdio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)

---
title: fsetpos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fsetpos
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
- fsetpos
dev_langs:
- C++
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ceacacbe029488995c47e305682b56751347591
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="fsetpos"></a>fsetpos

設定資料流位置指標。

## <a name="syntax"></a>語法

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
**FILE** 結構的指標。

*pos*<br/>
位置指標儲存區。

## <a name="return-value"></a>傳回值

如果成功的話， **fsetpos**傳回 0。 如果失敗，此函數會傳回非零值，並設定**errno**的下列其中一個資訊清單常數 （定義於 ERRNO。H): **EBADF**，這表示無法存取檔案，或物件的*資料流*指向不是有效的檔案結構; 或**EINVAL**，這表示的值無效*資料流*或*pos*傳遞。 如果傳入無效參數，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Fsetpos**函式會將檔案位置指標*資料流*值*pos*，在先前的呼叫，以取得**fgetpos**針對*資料流*。 清除檔案結尾指標的函式，並復原任何影響[ungetc](ungetc-ungetwc.md)上*資料流*。 在呼叫**fsetpos**下, 一項作業上的*資料流*可能是輸入或輸出。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [fgetpos](fgetpos.md) 的範例。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>

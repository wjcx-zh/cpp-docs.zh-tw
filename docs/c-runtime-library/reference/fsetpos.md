---
title: fsetpos
ms.date: 11/04/2016
api_name:
- fsetpos
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fsetpos
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
ms.openlocfilehash: f44ab1b35c9e598f82dbc0af96979476ee353541
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956512"
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

*stream*<br/>
**FILE** 結構的指標。

*採購*<br/>
位置指標儲存區。

## <a name="return-value"></a>傳回值

如果成功， **fsetpos**會傳回0。 當失敗時，函數會傳回非零值，並將**errno**設定為下列其中一個資訊清單常數（定義于 errno 中。H）：**EBADF**，這表示無法存取檔案，或*資料流程*指向的物件不是有效的檔案結構;或**EINVAL**，表示傳遞了不正確*資料流程*或*pos*值。 如果傳入無效參數，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Fsetpos**函式會將*資料流程*的檔案位置指標設定為*pos*的值，這會在先前的呼叫中取得以針對*串流*進行**fgetpos** 。 函式會清除檔案結尾指標，並復原*資料流程*上的任何[ungetc](ungetc-ungetwc.md)效果。 呼叫**fsetpos**之後，*資料流程*的下一個作業可以是輸入或輸出。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [fgetpos](fgetpos.md) 的範例。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>

---
title: fsetpos
ms.date: 11/04/2016
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
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
ms.openlocfilehash: 9854c71e381da6ec9a75d440b9588e2476bada7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287569"
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

*pos*<br/>
位置指標儲存區。

## <a name="return-value"></a>傳回值

如果成功， **fsetpos**會傳回 0。 在失敗時，此函式會傳回非零值，並設定**errno**的下列其中一個資訊清單常數 （定義於 ERRNO。H):**EBADF**，這表示檔案不是可存取或物件的*資料流*指向不是有效的檔案結構; 或**EINVAL**，這表示的值為 「 無效 」*資料流*或是*pos*傳遞。 如果傳入無效參數，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Fsetpos**函式設定的檔案位置指標*串流*的值*pos*，這先前呼叫中取得**fgetpos**對抗*串流*。 函式會清除檔案結尾指標，並會復原的任何影響[ungetc](ungetc-ungetwc.md)上*串流*。 之後呼叫**fsetpos**的下一個作業*串流*可能是輸入或輸出。

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

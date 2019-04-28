---
title: _setmaxstdio
ms.date: 11/04/2016
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
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 58cffedf673e23a69c2d8040071b2e3353ff4502
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356338"
---
# <a name="setmaxstdio"></a>_setmaxstdio

設定在同時開啟的檔案數目上限**stdio**層級。

## <a name="syntax"></a>語法

```C
int _setmaxstdio(
   int newmax
);
```

### <a name="parameters"></a>參數

*newmax*<br/>
新的最大值，在同時開啟的檔案數目**stdio**層級。

## <a name="return-value"></a>傳回值

傳回*newmax*如果成功，否則為-1。

如果*newmax*是小於 **_IOB_ENTRIES**或更高的作業系統，無效參數處理常式中提供的控制代碼數目上限會叫用，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，此函數會傳回-1 和集合允許執行**errno**要**EINVAL**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Setmaxstdio**函式會變更可能會在同時開啟的檔案數目的最大值**stdio**層級。

C 執行階段 I/O 支援在 Win32 平台上的開啟檔案數目，現在會多於舊版本。 2048 的檔案最多可以同時在開啟[lowio 層級](../../c-runtime-library/low-level-i-o.md)(也就是開啟和存取透過 **_open**， **_read**， **_write**等系列 I/O 函式)。 最多 512 個檔案可以同時在開放[stdio 層級](../../c-runtime-library/stream-i-o.md)(也就是開啟和存取透過**fopen**， **fgetc**， **fputc**等系列的函式)。 限制為 512 個開啟的檔案，在**stdio**層級，可以增加為最大值 2,048 **_setmaxstdio**函式。

因為**stdio**-level 函式，例如**fopen**，之上的**lowio**函式，最大值 2,048 是固定的數目上限同時開啟存取透過 C 執行階段程式庫的檔案。

> [!NOTE]
> 這個上限可能超過特定 Win32 平台和組態所支援的值。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱[_getmaxstdio](getmaxstdio.md)如需使用的範例 **_setmaxstdio**。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>

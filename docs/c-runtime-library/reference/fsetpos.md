---
title: fsetpos
ms.date: 4/2/2020
api_name:
- fsetpos
- _o_fsetpos
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 22b8cebd0154c0dbfc3d21843380ebc9a139059a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345724"
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

*Pos*<br/>
位置指標儲存區。

## <a name="return-value"></a>傳回值

如果成功 **,fsetpos**返回 0。 發生故障時,函數返回一個非零值,並將**errno**設置到以下清單常量之一(在ERRNO中定義)。H): **EBADF**,這意味著檔不可存取或*流*指向的物件不是有效的文件結構;或**EINVAL**,這意味著*傳遞了流*或*pos*的無效值。 如果傳入無效參數，則這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。

有關這些代碼和其他返回代碼的詳細資訊[,請參閱_doserrno、errno、_sys_errlist和_sys_nerr。](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>備註

**fsetpos**函數將*串流的*檔案位置指示器設置為*pos*的值,該值是在之前對*流*對**fgetpos**的呼叫中獲得的。 該函數清除檔結尾指示器,並撤銷對*流*的任何[ungetc](ungetc-ungetwc.md)影響。 呼叫**fsetpos**後,*串流*上的下一個操作可以是輸入操作或輸出。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [fgetpos](fgetpos.md) 的範例。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>

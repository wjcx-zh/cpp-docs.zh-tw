---
title: fclose、_fcloseall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
dev_langs:
- C++
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71b98a239cd1a6504611bf436533e7b5fbe1302c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400235"
---
# <a name="fclose-fcloseall"></a>fclose、_fcloseall

關閉資料流 (**fclose**) 或關閉所有開啟的資料流 (**_fcloseall**)。

## <a name="syntax"></a>語法

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>參數

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**fclose**傳回 0，如果已成功關閉資料流。 **_fcloseall**傳回關閉的資料流總數。 這兩個函式會傳回**EOF**表示錯誤。

## <a name="remarks"></a>備註

**Fclose**函式會關閉*資料流*。 如果*資料流*是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**fclose**設定**errno**至**EINVAL**並傳回**EOF**。 建議*資料流*指標一律檢查之前呼叫這個函式。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**_Fcloseall**函式會關閉所有開啟的資料流，除了**stdin**， **stdout**， **stderr** (以及在 MS-DOS **_stdaux**和 **_stdprn**)。 它也會關閉，並刪除任何由建立暫存檔**tmpfile**。 在這兩個函式中，所有與資料流相關聯的緩衝區都會先排清再關閉。 關閉資料流時，會釋放系統配置的緩衝區。 使用使用者指派的緩衝區**setbuf**和**setvbuf**不會自動釋放。

**注意︰** 使用這些函式關閉資料流時，基礎檔案描述項和作業系統檔案控制代碼 (或通訊端) 以及資料流都會關閉。 因此，如果原先已開啟檔案為檔案處理或檔案描述項，並關閉與**fclose**，也不執行呼叫 **_close**若要關閉的檔案描述項; 請勿呼叫 Win32 函式**CloseHandle**關閉檔案控制代碼。

**fclose**和 **_fcloseall**包含程式碼，以防止其他執行緒的干擾。 如需非鎖定版本的**fclose**，請參閱 **_fclose_nolock**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [fopen](fopen-wfopen.md) 的範例。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen、wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
f[reopen、_wfreopen](freopen-wfreopen.md)<br/>

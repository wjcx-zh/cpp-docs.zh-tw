---
title: fclose、_fcloseall
ms.date: 11/04/2016
api_name:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: 215925fb16f5d51e481ae92cbb45b0270bd5ebd4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941508"
---
# <a name="fclose-_fcloseall"></a>fclose、_fcloseall

關閉資料流程（**fclose**），或關閉所有開啟的資料流程（ **_fcloseall**）。

## <a name="syntax"></a>語法

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>參數

*stream*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

如果成功關閉資料流程， **fclose**會傳回0。 **_fcloseall**會傳回已關閉的資料流程總數。 這兩個函數都會傳回**EOF**來表示錯誤。

## <a name="remarks"></a>備註

**Fclose**函數會關閉*stream*。 如果*stream*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **fclose**會將**Errno**設定為**EINVAL** ，並傳回**EOF**。 建議在呼叫此函式之前，一律先檢查*資料流程*指標。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**_Fcloseall**函式會關閉所有開啟的資料流程，但**stdin**、 **stdout**、 **stderr** （和 MS-DOS、 **_stdaux**和 **_stdprn**）除外。 它也會關閉並刪除**tmpfile**所建立的任何暫存檔案。 在這兩個函式中，所有與資料流相關聯的緩衝區都會先排清再關閉。 關閉資料流時，會釋放系統配置的緩衝區。 具有**setbuf**和**setvbuf**的使用者所指派的緩衝區不會自動釋放。

**注意：** 當這些函式用來關閉資料流程時，基礎檔案描述項和作業系統檔案控制代碼（或通訊端）會關閉，以及資料流程。 因此，如果檔案原本是以檔案控制代碼或檔案描述項的形式開啟，並使用**fclose**來關閉，則請勿同時呼叫 **_close**來關閉檔案描述項;請勿呼叫 Win32 函數**CloseHandle**來關閉檔案控制代碼。

**fclose**和 **_fcloseall**包含的程式碼可防止其他執行緒的干擾。 如需**fclose**的非鎖定版本，請參閱 **_fclose_nolock**。

## <a name="requirements"></a>需求

|函數|必要的標頭|
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

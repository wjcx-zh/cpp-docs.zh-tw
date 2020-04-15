---
title: fclose、_fcloseall
ms.date: 4/2/2020
api_name:
- fclose
- _fcloseall
- _o__fcloseall
- _o_fclose
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
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: b2ee14c5fc8bb47cc2652443c0263bd14147c90d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347496"
---
# <a name="fclose-_fcloseall"></a>fclose、_fcloseall

關閉流 (**關閉**) 或關閉所有開啟的流 (**_fcloseall**)。

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

如果流成功關閉,**則關閉**傳回 0。 **_fcloseall**返回關閉的流總數。 兩個函數返回**EOF**以指示錯誤。

## <a name="remarks"></a>備註

**封閉函**數關閉*流*。 如果*串*流為**NULL,** 則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行 **,fclose**將**errno**設定到**EINVAL**並傳回**EOF**。 建議在調用此函數之前始終檢查*流*指標。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**_fcloseall**函數關閉除**緊要**、**抖、****穩(** 和, 在 MS-DOS,_stdaux **_stdaux**和 **_stdprn)** 之外的所有開放流 。 它還關閉並刪除由**tmpfile**創建的任何暫存檔。 在這兩個函式中，所有與資料流相關聯的緩衝區都會先排清再關閉。 關閉資料流時，會釋放系統配置的緩衝區。 使用**setbuf**和**setvbuf**的使用者分配的緩衝區不會自動釋放。

**注意︰** 使用這些函式關閉資料流時，基礎檔案描述項和作業系統檔案控制代碼 (或通訊端) 以及資料流都會關閉。 因此,如果檔最初是作為檔句柄或檔描述符打開的,並且用**fclose**關閉,則不要調用 **_close**來關閉檔描述符;不要呼叫 Win32 函數**CloseHandle**關閉檔句柄。

**fclose**和 **_fcloseall**包括代碼,以防止其他線程的干擾。 有關**fclose**的非鎖定版本,請參閱 **_fclose_nolock**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [fopen](fopen-wfopen.md) 的範例。

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>

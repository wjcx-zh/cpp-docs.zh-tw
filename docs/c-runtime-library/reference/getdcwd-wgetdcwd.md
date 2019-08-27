---
title: _getdcwd、_wgetdcwd
ms.date: 11/04/2016
apiname:
- _getdcwd
- _wgetdcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
ms.openlocfilehash: 9f6ae99ae74bb21c9462abcb37e466d63b86f8af
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501021"
---
# <a name="_getdcwd-_wgetdcwd"></a>_getdcwd、_wgetdcwd

取得指定磁碟機上目前工作目錄的完整路徑。

## <a name="syntax"></a>語法

```C
char *_getdcwd(
   int drive,
   char *buffer,
   int maxlen
);
wchar_t *_wgetdcwd(
   int drive,
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>參數

*drive*<br/>
指定磁碟機的非負整數 (0 = 預設磁碟機、1 = A、2 = B，依此類推)。

如果指定的磁片磁碟機無法使用, 或是無法判斷磁片磁碟機類型 (例如, 可移動、固定、CD-ROM、RAM 磁碟或網路磁碟機機), 則會叫用無效參數處理常式。 如需詳細資訊，請參閱[參數驗證](../../c-runtime-library/parameter-validation.md)。

*buffer*<br/>
路徑的儲存位置，或 **NULL**。

如果指定了**Null** , 此函式會使用**malloc**來配置至少*maxlen*大小的緩衝區, 而 **_getdcwd**的傳回值則是所配置緩衝區的指標。 您可以呼叫**free**來釋放緩衝區, 並將指標傳遞給它。

*maxlen*<br/>
指定路徑最大長度的非零正整數 (以字元為單位): **char**代表 **_getdcwd** , 而**wchar_t**代表 **_wgetdcwd**。

如果*maxlen*小於或等於零, 則會叫用不正確參數處理常式。 如需詳細資訊，請參閱[參數驗證](../../c-runtime-library/parameter-validation.md)。

## <a name="return-value"></a>傳回值

表示指定磁片磁碟機上目前工作目錄之完整路徑的字串指標, 或為**Null**, 表示發生錯誤。

如果將*buffer*指定為**Null** , 且記憶體不足以配置*maxlen*字元, 就會發生錯誤, 而且**errno**會設定為**ENOMEM**。 如果包含結束 null 字元的路徑長度超過*maxlen*, 就會發生錯誤, 而且**errno**會設定為**ERANGE**。 如需這些錯誤碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Getdcwd**函數會取得指定磁片磁碟機上目前工作目錄的完整路徑, 並將其儲存在*buffer*。 如果目前的工作目錄設定為根目錄，字串會以反斜線 (\\) 結尾。 如果目前的工作目錄設定為根目錄以外的目錄，字串會以目錄名稱結尾，而不是反斜線。

**_wgetdcwd**是 **_getdcwd**的寬字元版本, 其*緩衝區*參數和傳回值是寬字元字串。 否則, **_wgetdcwd**和 **_getdcwd**的行為會相同。

這個函式即使相依於本身不是安全執行緒的 **GetFullPathName**，仍是安全執行緒。 不過，如果多執行緒應用程式同時呼叫這個函式和 [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew)，您可能會違反執行緒安全。

具有 **_nolock**後置字元的這個函式版本與此函式的行為相同, 不同之處在于它不是安全線程, 而且不受保護而無法防止其他執行緒的干擾。 如需詳細資訊，請參閱 [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md)。

當定義了 **_debug**和 **_CRTDBG_MAP_ALLOC**時, 對 **_getdcwd**和 **_wgetdcwd**的呼叫會被 **_getdcwd_dbg**和 **_wgetdcwd_dbg**的呼叫所取代, 讓您可以進行記憶體配置的偵錯工具。 如需詳細資訊，請參閱[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_getdrive](getdrive.md)中的範例。

## <a name="see-also"></a>另請參閱

[目錄控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>

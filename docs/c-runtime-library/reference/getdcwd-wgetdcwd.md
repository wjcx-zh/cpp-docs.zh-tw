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
ms.openlocfilehash: 464a254775d9a1d2488247d6dafb4b85cd763f10
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331827"
---
# <a name="getdcwd-wgetdcwd"></a>_getdcwd、_wgetdcwd

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

如果指定的磁碟機無法使用，或磁碟機的種類 （例如，卸除式、 固定、 CD-ROM、 RAM 磁碟或網路磁碟機） 無法判斷，會叫用無效參數處理常式。 如需詳細資訊，請參閱[參數驗證](../../c-runtime-library/parameter-validation.md)。

*buffer*<br/>
路徑的儲存位置，或 **NULL**。

如果**NULL**指定，則此函式至少會配置的緩衝區*maxlen*使用大小**malloc**，並傳回值 **_getdcwd**是所配置緩衝區的指標。 可以藉由呼叫釋放緩衝區**免費**並將其傳遞指標。

*maxlen*<br/>
非零正整數，以字元為單位指定路徑的最大長度： **char**如 **_getdcwd**並**wchar_t**如 **_wgetdcwd**.

如果*maxlen*小於或等於零，會叫用無效參數處理常式。 如需詳細資訊，請參閱[參數驗證](../../c-runtime-library/parameter-validation.md)。

## <a name="return-value"></a>傳回值

表示在指定的磁碟機上的目前工作目錄的完整路徑的字串指標，或是**NULL**，以表示錯誤。

如果*緩衝區*指定為**NULL** ，而且沒有記憶體不足，無法配置*maxlen*字元，則會發生錯誤並**errno**是設定為**ENOMEM**。 如果路徑包含結束的 null 字元的長度超過*maxlen*，發生錯誤，並**errno**設定為**ERANGE**。 如需這些錯誤碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Getdcwd**函式會取得在指定的磁碟機上的目前工作目錄的完整路徑，並將其儲存在*緩衝區*。 如果目前的工作目錄設定為根目錄，字串會以反斜線 (\\) 結尾。 如果目前的工作目錄設定為根目錄以外的目錄，字串會以目錄名稱結尾，而不是反斜線。

**_wgetdcwd**是寬字元版本的 **_getdcwd**，並將其*緩衝區*參數與傳回值均為寬字元字串。 否則，請 **_wgetdcwd**並 **_getdcwd**運作方式完全相同。

這個函式即使相依於本身不是安全執行緒的 **GetFullPathName**，仍是安全執行緒。 不過，您可能會違反執行緒安全多執行緒的應用程式呼叫此函式和[GetFullPathNameA](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)。

這個函式具有新版 **_nolock**行為完全相同後, 置詞對這個函式不同之處在於它不是安全執行緒，並不受干擾其他執行緒。 如需詳細資訊，請參閱 [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md)。

時 **_DEBUG**並 **_CRTDBG_MAP_ALLOC**所定義，但呼叫 **_getdcwd**並 **_wgetdcwd**會取代藉由呼叫 **_getdcwd_dbg**並 **_wgetdcwd_dbg** ，讓您可以偵錯記憶體配置。 如需詳細資訊，請參閱[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md)。

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

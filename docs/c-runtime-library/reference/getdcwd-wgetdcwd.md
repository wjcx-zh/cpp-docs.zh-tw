---
title: _getdcwd、_wgetdcwd
ms.date: 4/2/2020
api_name:
- _getdcwd
- _wgetdcwd
- _o__getdcwd
- _o__wgetdcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3a4ca8ff3f1153893282c65bc4c2becd687138ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344391"
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

*驅動*<br/>
指定磁碟機的非負整數 (0 = 預設磁碟機、1 = A、2 = B，依此類推)。

如果指定的驅動器不可用,或者無法確定驅動器類型(例如,可移動、固定、CD-ROM、RAM 磁碟或網路驅動器),則調用無效參數處理程式。 如需詳細資訊，請參閱[參數驗證](../../c-runtime-library/parameter-validation.md)。

*緩衝區*<br/>
路徑的儲存位置，或 **NULL**。

如果指定**NULL,** 則此函數透過使用**malloc**分配至少*最大大小的*緩衝區,**並且_getdcwd**的返回值是指向已分配的緩衝區的指標。 可以通過調用**空閒**並傳遞指標來釋放緩衝區。

*馬克斯倫*<br/>
指定路徑最大長度的非零正整數,以字元表示 **:_getdcwd****的字元****wchar_t****,_wgetdcwdwchar_t。**

如果*maxlen*小於或等於零,則調用無效參數處理程式。 如需詳細資訊，請參閱[參數驗證](../../c-runtime-library/parameter-validation.md)。

## <a name="return-value"></a>傳回值

指向表示指定驅動器上當前工作目錄的完整路徑的字串的指標,或**NULL**,指示錯誤。

如果*緩衝區*指定**NULL,** 並且記憶體不足以分配*maxlen*字元,則會發生錯誤並將**errno**設定為**ENOMEM**。 如果路徑的長度(包括終止空字元)超過*maxlen,* 則會發生錯誤,並將**errno**設定為**ERANGE**。 如需這些錯誤碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_getdcwd**函數獲取指定驅動器上當前工作目錄的完整路徑並將其存儲在*緩衝區*中。 如果目前的工作目錄設定為根目錄，字串會以反斜線 (\\) 結尾。 如果目前的工作目錄設定為根目錄以外的目錄，字串會以目錄名稱結尾，而不是反斜線。

**_wgetdcwd**是 **_getdcwd**的寬字元版本,其*緩衝區*參數和返回值是寬字元字串。 否則 **,_wgetdcwd**和 **_getdcwd**行為相同。

這個函式即使相依於本身不是安全執行緒的 **GetFullPathName**，仍是安全執行緒。 不過，如果多執行緒應用程式同時呼叫這個函式和 [GetFullPathName](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamew)，您可能會違反執行緒安全。

具有 **_nolock**後綴的此函數的版本與此函數行為相同,只不過它不是線程安全的,並且不受到其他線程的干擾。 如需詳細資訊，請參閱 [_getdcwd_nolock, _wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md)。

定義 **_DEBUG**和 **_CRTDBG_MAP_ALLOC**時,對 **_getdcwd**和 **_wgetdcwd**的呼叫將替換為對 **_getdcwd_dbg**和 **_wgetdcwd_dbg**的呼叫,以便您可以調試記憶體分配。 如需詳細資訊，請參閱[_getdcwd_dbg, _wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_getdrive](getdrive.md)中的範例。

## <a name="see-also"></a>另請參閱

[目錄控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>

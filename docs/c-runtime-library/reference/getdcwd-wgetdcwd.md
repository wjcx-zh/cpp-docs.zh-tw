---
title: _getdcwd、_wgetdcwd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- wgetdcwd
- getdcwd
- _getdcwd
- tgetdcwd
- _wgetdcwd
- _tgetdcwd
dev_langs:
- C++
helpviewer_keywords:
- wgetdcwd function
- working directory
- getdcwd function
- _getdcwd function
- _wgetdcwd function
- current working directory
- directories [C++], current working
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e3572f629a6ca9df44fb4c571e2712894d89b257
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

*磁碟機*<br/>
指定磁碟機的非負整數 (0 = 預設磁碟機、1 = A、2 = B，依此類推)。

如果指定的磁碟機無法使用，或是無法判斷磁碟機類型 (例如抽取式、固定、CD-ROM、RAM 磁碟或網路磁碟機)，則會叫用無效參數處理常式，如 [Parameter Validation](../../c-runtime-library/parameter-validation.md)中所述。

*buffer*<br/>
路徑的儲存位置，或 **NULL**。

如果**NULL**指定，則此函式會配置的緩衝區至少*maxlen*大小使用**malloc**，和傳回值 **_getdcwd**所配置緩衝區的指標。 可以藉由呼叫釋放緩衝區**可用**並將其傳遞指標。

*maxlen*<br/>
非零正整數，以字元為單位指定路徑的最大長度： **char**如 **_getdcwd**和**wchar_t**如 **_wgetdcwd**.

如果*maxlen*不是大於零中, 所述的無效參數處理常式，[參數驗證](../../c-runtime-library/parameter-validation.md)，會叫用。

## <a name="return-value"></a>傳回值

表示指定的磁碟機上目前的工作目錄的完整路徑的字串指標或**NULL**，以表示錯誤。

如果*緩衝區*指定為**NULL** ，而且沒有記憶體不足以配置*maxlen*字元，就會發生的錯誤和**errno**是設定為**ENOMEM**。 如果路徑 （包括結束的 null 字元） 的長度超過*maxlen*，就會發生的錯誤和**errno**設**為 ERANGE**。 如需這些錯誤碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Getdcwd**函式取得目前工作目錄的完整路徑指定磁碟機，並將其儲存在*緩衝區*。 如果目前的工作目錄設定為根目錄，字串會以反斜線 (\\) 結尾。 如果目前的工作目錄設定為根目錄以外的目錄，字串會以目錄名稱結尾，而不是反斜線。

**_wgetdcwd**是寬字元版本的 **_getdcwd**，且其*緩衝區*參數和傳回值是寬字元字串。 否則， **_wgetdcwd**和 **_getdcwd**行為即會相同。

這個函式即使相依於本身不是安全執行緒的 **GetFullPathName**，仍是安全執行緒。 不過，如果多執行緒應用程式同時呼叫這個函式和 **GetFullPathName**，您可能會違反執行緒安全。 如需詳細資訊，請前往 [MSDN Library](http://go.microsoft.com/fwlink/p/?linkid=150542)，然後搜尋 **GetFullPathName**。

這個函式具有版本 **_nolock**作用完全相同後, 置詞這個函式不同之處在於它不是執行緒安全，而且不受干擾其他執行緒。 如需詳細資訊，請參閱 [_getdcwd_nolock、_wgetdcwd_nolock](getdcwd-nolock-wgetdcwd-nolock.md)。

當 **_DEBUG**和 **_CRTDBG_MAP_ALLOC**所定義，但呼叫 **_getdcwd**和 **_wgetdcwd** 呼叫來取代 **_getdcwd_dbg**和 **_wgetdcwd_dbg** ，讓您可以偵錯記憶體配置。 如需詳細資訊，請參閱 [_getdcwd_dbg、_wgetdcwd_dbg](getdcwd-dbg-wgetdcwd-dbg.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd**|**_getdcwd**|**_getdcwd**|**_wgetdcwd**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_getdcwd**|\<direct.h>|
|**_wgetdcwd**|\<direct.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

請參閱 [_getdrive](getdrive.md) 中的範例。

## <a name="see-also"></a>另請參閱

[目錄控制](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>

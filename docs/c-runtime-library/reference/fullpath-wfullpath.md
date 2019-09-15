---
title: _fullpath、_wfullpath
ms.date: 11/04/2016
api_name:
- _fullpath
- _wfullpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wfullpath
- fullpath
- _wfullpath
- _fullpath
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
ms.openlocfilehash: 30e62716c496ebb1a39b53a420f372a6e743c2c0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956273"
---
# <a name="_fullpath-_wfullpath"></a>_fullpath、_wfullpath

為指定的相對路徑名稱建立絕對路徑或完整路徑名稱。

## <a name="syntax"></a>語法

```C
char *_fullpath(
   char *absPath,
   const char *relPath,
   size_t maxLength
);
wchar_t *_wfullpath(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength
);
```

### <a name="parameters"></a>參數

*absPath*<br/>
包含絕對或完整路徑名稱之緩衝區的指標，或為**Null**。

*relPath*<br/>
相對路徑名稱。

*maxLength*<br/>
絕對路徑名稱緩衝區的最大長度（*absPath*）。 **_Fullpath**的這個長度是以位元組為單位，但以寬字元（**wchar_t**）表示 **_wfullpath**。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回包含絕對路徑名稱（*absPath*）之緩衝區的指標。 如果發生錯誤（例如，如果傳入*relPath*的值包含無效或找不到的磁碟機號，或是建立的絕對路徑名稱（*absPath*）的長度大於*maxLength*），則函式會傳回**Null**。

## <a name="remarks"></a>備註

**_Fullpath**函式會將*relPath*中的相對路徑名稱擴充為其完整或絕對路徑，並將此名稱儲存在*absPath*中。 如果*absPath*為**Null**，則會使用**malloc**來配置足夠長度的緩衝區來保存路徑名稱。 釋放這個緩衝區是呼叫端的責任。 相對路徑名稱指定從目前的位置到另一個位置的路徑 (例如目前的工作目錄：「.」)。 絕對路徑名稱是相對路徑名稱的擴充狀態，其表示從檔案系統根目錄到達所需位置的完整路徑。 不同于 **_makepath**， **_fullpath**可以用來取得相對路徑（*relPath*）的絕對路徑名稱，其中包含 "./" 或 ".。/"在其名稱中。

例如，若要使用 C 執行階段常式，應用程式必須包含具有常式宣告的標頭檔。 每個標頭檔以相對的方式包含檔案位置的陳述式參考 (從應用程式的工作目錄)︰

```C
#include <stdlib.h>
```

當檔案的絕對路徑 (實際的檔案系統位置) 可能是：

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath**會自動將多位元組字元字串引數處理為適當，並根據目前使用中的多位元組字碼頁來辨識多位元組字元序列。 **_wfullpath**是寬字元版本的 **_fullpath**; **_wfullpath**的字串引數是寬字元字串。 **_wfullpath**和 **_fullpath**的行為相同，不同之處在于 **_wfullpath**不會處理多位元組字元字串。

如果同時定義了 **_debug**和 **_CRTDBG_MAP_ALLOC** ，對 **_fullpath**和 **_wfullpath**的呼叫會被 **_fullpath_dbg**和 **_wfullpath_dbg**的呼叫所取代，以允許進行記憶體配置的偵錯工具。 如需詳細資訊，請參閱 [_fullpath_dbg、_wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md)。

如果*maxlen*小於或等於0，則此函式會叫用不正確參數處理常式（如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述）。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回**Null**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

如果*absPath*緩衝區為**Null**， **_fullpath**會呼叫[Malloc](malloc.md)來配置緩衝區，並忽略*maxLength*引數。 呼叫端必須負責視需要取消配置這個緩衝區 (使用 [free](free.md))。 如果*relPath*引數指定磁片磁碟機，則此磁片磁碟機的目前目錄會與該路徑結合。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fullpath.c
// This program demonstrates how _fullpath
// creates a full path from a partial path.

#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
#include <direct.h>

void PrintFullPath( char * partialPath )
{
   char full[_MAX_PATH];
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )
      printf( "Full path is: %s\n", full );
   else
      printf( "Invalid path\n" );
}

int main( void )
{
   PrintFullPath( "test" );
   PrintFullPath( "\\test" );
   PrintFullPath( "..\\test" );
}
```

```Output
Full path is: C:\Documents and Settings\user\My Documents\test
Full path is: C:\test
Full path is: C:\Documents and Settings\user\test
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd、_wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
[_splitpath、_wsplitpath](splitpath-wsplitpath.md)<br/>

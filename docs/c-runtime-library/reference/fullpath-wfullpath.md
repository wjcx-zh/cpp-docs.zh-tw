---
title: _fullpath、_wfullpath
ms.date: 4/2/2020
api_name:
- _fullpath
- _wfullpath
- _o__fullpath
- _o__wfullpath
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0910cf4f39e00be84e683cd6f3b9afbeb3f2a749
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345491"
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
包含絕對或完整路徑名稱的緩衝區的指標,或**NULL**。

*relPath*<br/>
相對路徑名稱。

*maxLength*<br/>
絕對路徑名稱緩衝區 *(absPath*) 的最大長度。 這個長度以位元組為單位 **_fullpath**但寬字元 **(wchar_t)** 表示 **_wfullpath**。

## <a name="return-value"></a>傳回值

每個函數返回一個指向包含絕對路徑名稱 *(absPath*) 的緩衝區的指標。 如果發生錯誤(例如, 如果*relPath*中傳遞的值包含無效或找不到的驅動器號,或如果建立的絕對路徑名稱 *(absPath)* 的長度大於*maxLength),* 則函數傳回**NULL**。

## <a name="remarks"></a>備註

**_fullpath**函數將*relPath*中的相對路徑名稱擴展到其完全限定或絕對路徑,並將此名稱存儲在*absPath*中。 如果*absPath*為**NULL,****則 malloc**用於分配足夠長度的緩衝區來保存路徑名稱。 釋放這個緩衝區是呼叫端的責任。 相對路徑名稱指定從目前的位置到另一個位置的路徑 (例如目前的工作目錄：「.」)。 絕對路徑名稱是相對路徑名稱的擴充狀態，其表示從檔案系統根目錄到達所需位置的完整路徑。 **與_makepath****不同,_fullpath**可用於獲取包含"./"或"的相對路徑 *(relPath)* 的絕對路徑名稱。/" 以他們的名字。

例如，若要使用 C 執行階段常式，應用程式必須包含具有常式宣告的標頭檔。 每個標頭檔以相對的方式包含檔案位置的陳述式參考 (從應用程式的工作目錄)︰

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <stdlib.h>
```

當檔案的絕對路徑 (實際的檔案系統位置) 可能是：

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath**根據需要自動處理多位元位元串參數,根據當前使用的多位元節代碼頁識別多位元組位元序列。 **_wfullpath**是 **_fullpath**的寬字元版本;要 **_wfullpath**的字串參數是寬字元字串。 **_wfullpath****和_fullpath**行為相同,只是 **_wfullpath**不處理多位元組位元串。

如果定義了 **_DEBUG**和 **_CRTDBG_MAP_ALLOC,** 則對 **_fullpath**和 **_wfullpath**的調用將替換為對 **_fullpath_dbg**和 **_wfullpath_dbg**的調用,以允許調試記憶體分配。 如需詳細資訊，請參閱 [_fullpath_dbg、_wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md)。

如果*maxlen*小於或等於 0,則此函數調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,此函數將**errno**設定到**EINVAL**並傳回**NULL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

如果*absPath*緩衝區為**NULL,_fullpath**呼叫[malloc](malloc.md)來分配緩衝區並忽略**NULL***maxLength 參數*。 呼叫端必須負責視需要取消配置這個緩衝區 (使用 [free](free.md))。 如果*relPath*參數指定磁碟驅動器,則此驅動器的當前目錄將與路徑合併。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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

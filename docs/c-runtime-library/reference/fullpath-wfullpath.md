---
title: _fullpath、_wfullpath
ms.date: 11/04/2016
apiname:
- _fullpath
- _wfullpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: aeacaf581b7f33ee893754c192ae547376ce73ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550393"
---
# <a name="fullpath-wfullpath"></a>_fullpath、_wfullpath

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
包含絕對路徑或完整路徑名稱之緩衝區的指標或**NULL**。

*relPath*<br/>
相對路徑名稱。

*MaxLength*<br/>
絕對路徑名稱緩衝區的最大長度 (*absPath*)。 這個長度是以位元組為單位 **_fullpath**但是寬字元 (**wchar_t**) 的 **_wfullpath**。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回包含絕對路徑名稱之緩衝區的指標 (*absPath*)。 如果發生錯誤 (例如，如果傳入的值時，才*relPath*包含磁碟機代號無效或找不到，或如果建立的絕對路徑名稱的長度 (*absPath*) 大於*maxLength*)，則函數會傳回**NULL**。

## <a name="remarks"></a>備註

**_Fullpath**函式會擴展中的相對路徑名稱*relPath*其完整或絕對路徑，並將此名稱在儲存*absPath*。 如果*absPath*是**NULL**， **malloc**用來配置足夠長度儲存路徑名稱的緩衝區。 釋放這個緩衝區是呼叫端的責任。 相對路徑名稱指定從目前的位置到另一個位置的路徑 (例如目前的工作目錄：「.」)。 絕對路徑名稱是相對路徑名稱的擴充狀態，其表示從檔案系統根目錄到達所需位置的完整路徑。 不同於 **_makepath**， **_fullpath**可用來取得相對路徑的絕對路徑名稱 (*relPath*)，包括 「。 / 「 或 」.../ 」 在其名稱中。

例如，若要使用 C 執行階段常式，應用程式必須包含具有常式宣告的標頭檔。 每個標頭檔以相對的方式包含檔案位置的陳述式參考 (從應用程式的工作目錄)︰

```C
#include <stdlib.h>
```

當檔案的絕對路徑 (實際的檔案系統位置) 可能是：

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath**自動多位元組字元字串引數處理為適當，辨識多位元組字元序列，根據目前使用中的多位元組字碼頁。 **_wfullpath**是寬字元版本的 **_fullpath**; 的字串引數 **_wfullpath**是寬字元字串。 **_wfullpath**並 **_fullpath**運作方式完全相同，不同之處在於 **_wfullpath**不會處理多位元組字元字串。

如果 **_DEBUG**並 **_CRTDBG_MAP_ALLOC**兩者都已定義，來呼叫 **_fullpath**和 **_wfullpath**會取代藉由呼叫 **_fullpath_dbg**並 **_wfullpath_dbg**以便進行偵錯記憶體配置。 如需詳細資訊，請參閱 [_fullpath_dbg、_wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md)。

此函式會叫用無效參數處理常式中，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)，如果*maxlen*小於或等於 0。 如果允許繼續執行，此函式會將**errno**要**EINVAL** ，並傳回**NULL**。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

如果*absPath*緩衝區**NULL**， **_fullpath**呼叫[malloc](malloc.md)配置緩衝區，並忽略*maxLength*引數。 呼叫端必須負責視需要取消配置這個緩衝區 (使用 [free](free.md))。 如果*relPath*引數會指定磁碟機，此磁碟機的目前目錄會結合路徑。

## <a name="requirements"></a>需求

|功能|必要的標頭|
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

---
title: _creat、_wcreat
ms.date: 11/04/2016
apiname:
- _creat
- _wcreat
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
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
ms.openlocfilehash: 901a95a6a9361f95f38749dacf1a5001d97b3761
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494987"
---
# <a name="creat-wcreat"></a>_creat、_wcreat

建立新檔案。 **_creat**並 **_wcreat**已被取代; 請使用[_sopen_s、 _wsopen_s](sopen-s-wsopen-s.md)改。

## <a name="syntax"></a>語法

```C
int _creat(
   const char *filename,
   int pmode
);
int _wcreat(
   const wchar_t *filename,
   int pmode
);
```

### <a name="parameters"></a>參數

*filename*<br/>
新檔案的名稱。

*pmode*<br/>
權限設定。

## <a name="return-value"></a>傳回值

這些函式若成功，則傳回所建立檔案的檔案描述項。 否則，函式會傳回-1，並設定**errno**下表所示。

|**errno**設定|描述|
|---------------------|-----------------|
|**EACCES**|*檔名*指定現有的唯讀檔案，或指定的目錄，而非檔案。|
|**EMFILE**|沒有更多檔案描述項可用。|
|**ENOENT**|找不到指定的檔案。|

如果*檔名*是**NULL**，這些函式叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**要**EINVAL**並傳回-1。

如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Creat**函式會建立新的檔案或開啟並截斷現有。 **_wcreat**是寬字元版本的 **_creat**; *filename*引數 **_wcreat**是寬字元字串。 **_wcreat**並 **_creat**行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

如果指定的檔案*filename*不存在，新的檔案會使用指定的權限設定建立及開啟供寫入。 如果檔案已經存在，而且其權限設定允許寫入 **_creat**截斷至長度為 0，終結先前的內容檔案，並開啟以供寫入。 權限設定中， *pmode*，適用於新建立的檔案。 新檔案會在第一次關閉之後收到指定的權限設定。 整數運算式*pmode*包含一或兩個資訊清單常數 **_S_IWRITE**並 **_S_IREAD**、 SYS\Stat.h 中所定義。 時指定這兩個常數，它們會結合使用位元 or 運算子 ( **&#124;** )。 *Pmode*參數設定為下列值之一。

|值|定義|
|-----------|----------------|
|**_S_IWRITE**|允許寫入|
|**_S_IREAD**|允許讀取。|
|**_S_IREAD** &AMP;#124; **_S_IWRITE**|允許讀取和寫入。|

若沒有指定寫入權限，則檔案為唯讀。 所有檔案皆為可讀取；不可能授與僅限寫入權限。 模式 **_S_IWRITE**並 **_S_IREAD** | **_S_IWRITE**相同。 使用開啟的檔案 **_creat**永遠都相容性模式中開啟 (請參閱[_sopen](sopen-wsopen.md)) 與 **_SH_DENYNO**。

**_creat**到目前的檔案權限遮罩套用*pmode*之前設定的權限 (請參閱[_umask](umask.md))。 **_creat**提供主要目的是為了與先前的程式庫的相容性。 呼叫 **_open**具有 **_O_CREAT**並 **_O_TRUNC**中*oflag*參數相當於 **_creat**，並且適用於新的程式碼。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|
|**_wcreat**|\<io.h> 或 \<wchar.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_creat.c
// compile with: /W3
// This program uses _creat to create
// the file (or truncate the existing file)
// named data and open it for writing.

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int fh;

   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996
   // Note: _creat is deprecated; use _sopen_s instead
   if( fh == -1 )
      perror( "Couldn't create data file" );
   else
   {
      printf( "Created data file.\n" );
      _close( fh );
   }
}
```

```Output
Created data file.
```

## <a name="see-also"></a>另請參閱

[低層級 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[dup、dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>

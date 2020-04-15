---
title: _creat、_wcreat
ms.date: 4/2/2020
api_name:
- _creat
- _wcreat
- _o__creat
- _o__wcreat
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
ms.openlocfilehash: 18ecf78d2cbff3647eae912a1bb1b17d5340f185
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348329"
---
# <a name="_creat-_wcreat"></a>_creat、_wcreat

建立新檔案。 **_creat**和 **_wcreat**已被棄用;而是使用[_sopen_s,_wsopen_s。](sopen-s-wsopen-s.md)

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

*檔案名稱*<br/>
新檔案的名稱。

*pmode*<br/>
權限設定。

## <a name="return-value"></a>傳回值

這些函式若成功，則傳回所建立檔案的檔案描述項。 否則,函數返回 -1 並設置**errno,** 如下表所示。

|**errno**設定|描述|
|---------------------|-----------------|
|**EACCES**|*檔名*指定現有的唯讀檔或指定目錄而不是檔案。|
|**EMFILE**|沒有更多檔案描述項可用。|
|**埃諾恩特**|找不到指定的檔案。|

如果*檔案名稱*為**NULL,** 則這些函數將呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,這些函數將**errno**設置為**EINVAL**並返回 -1。

如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_creat**函數創建新檔或打開並截截現有檔。 **_wcreat**是 **_creat**的寬字元版本;要 **_wcreat***的檔案名*參數是寬字元字串。 **_wcreat****和_creat**行為相同。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

如果*檔案名*指定的檔不存在,則使用給定的許可權設置創建新檔,並打開以進行寫入。 如果檔已存在,並且其許可權設置允許寫入 **,_creat**將檔截長為 0,銷毀以前的內容,然後打開該檔進行寫入。 許可權設定*pmode*僅適用於新創建的檔案。 新檔案會在第一次關閉之後收到指定的權限設定。 整數運算式*pmode*包含 _S_IWRITE和 **_S_IREAD**中定義的**一**個或兩個清單常量。 當兩個常量都給出時,它們與位或運算符 **(&#124;** ) 聯接。 *pmode*參數設置為以下值之一。

|值|定義|
|-----------|----------------|
|**_S_IWRITE**|允許寫入。|
|**_S_IREAD**|允許讀取。|
|**_S_IREAD&#124;_S_IWRITE** **_S_IWRITE**|允許讀取和寫入。|

若沒有指定寫入權限，則檔案為唯讀。 所有檔案皆為可讀取；不可能授與僅限寫入權限。 然後等效 **_S_IWRITE**和 **_S_IREAD_S_IWRITE** | **_S_IWRITE**模式。 使用 **_creat**開啟的檔案始終在相容模式下開啟(請參閱[_sopen)](sopen-wsopen.md)與 **_SH_DENYNO**。

**_creat**在設定權限之前將當前文件許可權掩碼應用於*pmode(* 請參閱[_umask](umask.md))。 **提供_creat**主要是為了與以前的庫相容。 **調用在**_O_CREAT**和****_O_TRUNC**在*lag*參數中_open等效於 **_creat,** 並且對於新代碼更可取。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|
|**_wcreat**|\<io.h> 或 \<wchar.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
[_dup,_dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>

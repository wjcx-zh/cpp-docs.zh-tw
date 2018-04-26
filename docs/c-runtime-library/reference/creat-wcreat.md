---
title: _creat、_wcreat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 73ed20925501e9f797e7a5a2b7895ff0f80a5b1a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="creat-wcreat"></a>_creat、_wcreat

建立新檔案。 **_creat**和 **_wcreat**已被取代; 請使用[_sopen_s、 _wsopen_s](sopen-s-wsopen-s.md)改為。

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
|**EACCES**|*檔名*指定現有的唯讀檔案或指定的目錄，而非檔案。|
|**EMFILE**|沒有更多檔案描述項可用。|
|**ENOENT**|找不到指定的檔案。|

如果*filename*是 NULL，這些函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**至**EINVAL**並傳回-1。

如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Creat**函式會建立新的檔案或開啟並截斷一個現有。 **_wcreat**是寬字元版本的 **_creat**; *filename*引數 **_wcreat**是寬字元字串。 **_wcreat**和 **_creat**除此之外的行為相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

如果指定的檔案*filename*不存在，新的檔案建立與指定的權限設定，並開啟供寫入。 如果檔案已經存在，而且其權限設定可讓撰寫、 **_creat**截斷至長度為 0，終結之前的內容檔案，並開啟以供寫入。 權限設定中， *pmode*，套用至新建立的檔案。 新檔案會在第一次關閉之後收到指定的權限設定。 整數運算式*pmode*包含一或兩個資訊清單常數 **_S_IWRITE**和 **_S_IREAD**SYS\Stat.h 中定義。 當兩個常數時，加入與位元 or 運算子 ( **&#124;** )。 *Pmode*參數設定為下列值之一。

|值|定義|
|-----------|----------------|
|**_S_IWRITE**|允許寫入|
|**_S_IREAD**|允許讀取。|
|**_S_IREAD** &AMP;#124; **_S_IWRITE**|允許讀取和寫入。|

若沒有指定寫入權限，則檔案為唯讀。 所有檔案皆為可讀取；不可能授與僅限寫入權限。 模式 **_S_IWRITE**和 **_S_IREAD** | **_S_IWRITE**然後會相等。 使用開啟的檔案 **_creat**永遠都在相容性模式中開啟 (請參閱[_sopen](sopen-wsopen.md)) 與 **_SH_DENYNO**。

**_creat**目前檔案權限遮罩套用至*pmode*之前設定的權限 (請參閱[_umask](umask.md))。 **_creat**主要是供與先前的程式庫相容性。 呼叫 **_open**與 **_O_CREAT**和 **_O_TRUNC**中*oflag*參數相當於 **_creat**和新的程式碼時，最好。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
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

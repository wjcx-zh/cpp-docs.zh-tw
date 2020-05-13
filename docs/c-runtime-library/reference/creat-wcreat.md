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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 379a4adbf17755341fed6a48c649afe29e150fe5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912118"
---
# <a name="_creat-_wcreat"></a>_creat、_wcreat

建立新檔案。 **_creat**和 **_wcreat**已被取代;[請改用 _sopen_s，_wsopen_s](sopen-s-wsopen-s.md) 。

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

*名稱*<br/>
新檔案的名稱。

*pmode*<br/>
權限設定。

## <a name="return-value"></a>傳回值

這些函式若成功，則傳回所建立檔案的檔案描述項。 否則，函數會傳回-1 並設定**errno** ，如下表所示。

|**errno**設定|描述|
|---------------------|-----------------|
|**EACCES**|*filename*指定現有的唯讀檔案，或指定目錄而不是檔案。|
|**EMFILE**|沒有更多檔案描述項可用。|
|**ENOENT**|找不到指定的檔案。|

如果*filename*是**Null**，則這些函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**設定為**EINVAL** ，並傳回-1。

如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Creat**函式會建立新的檔案，或開啟並截斷現有的檔案。 **_wcreat**是寬字元版本的 **_creat**;**_wcreat**的*filename*引數是寬字元字串。 相反地， **_wcreat**和 **_creat**的行為相同。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

如果*filename*指定的檔案不存在，則會使用指定的許可權設定來建立新的檔案，並開啟以供寫入。 如果檔案已經存在，且其許可權設定允許寫入， **_creat**會將檔案截斷為長度0、終結先前的內容，然後開啟以供寫入。 許可權設定*pmode*僅適用于新建立的檔案。 新檔案會在第一次關閉之後收到指定的權限設定。 整數運算式*pmode*包含一或兩個資訊清單常數 **_S_IWRITE**和 **_S_IREAD**（定義于 sys\stat.h 所） 當同時指定兩個常數時，會使用位 or 運算子（ **&#124;** ）聯結。 *Pmode*參數會設定為下列其中一個值。

|值|定義|
|-----------|----------------|
|**_S_IWRITE**|允許寫入。|
|**_S_IREAD**|允許讀取。|
|**_S_IREAD** &#124; **_S_IWRITE**|允許讀取和寫入。|

若沒有指定寫入權限，則檔案為唯讀。 所有檔案皆為可讀取；不可能授與僅限寫入權限。 **_S_IWRITE**和 **_S_IREAD** | **_S_IWRITE**的模式則相等。 使用 **_creat**開啟的檔案一律會在相容性模式（請參閱[_sopen](sopen-wsopen.md)）中以 **_SH_DENYNO**開啟。

**_creat**在設定許可權之前，將目前的檔案許可權遮罩套用至*pmode* （請參閱[_umask](umask.md)）。 **_creat**的主要目的是為了與先前的程式庫相容。 在*oflag*參數中使用 **_O_CREAT**和 **_O_TRUNC**呼叫 **_open** ，相當於 **_creat** ，適用于新的程式碼。

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
[_dup，_dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>

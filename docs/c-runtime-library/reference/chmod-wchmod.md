---
title: _chmod、_wchmod
ms.date: 11/04/2016
apiname:
- _chmod
- _wchmod
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
- _chmod
- _wchmod
- wchmod
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
ms.openlocfilehash: 7f3133aac1548be5cb497fe32ae4f9f1c0e238d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595126"
---
# <a name="chmod-wchmod"></a>_chmod、_wchmod

變更檔案權限設定。

## <a name="syntax"></a>語法

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>參數

*filename*<br/>
現有檔案的名稱。

*pmode*<br/>
檔案的權限設定。

## <a name="return-value"></a>傳回值

如果成功變更權限設定，則這些函式會傳回 0。 傳回值為-1 表示失敗。 如果找不到指定的檔案， **errno**設為**ENOENT**; 如果不正確、 此參數**errno**設定為**EINVAL**。

## <a name="remarks"></a>備註

**_Chmod**函式會變更所指定之檔案的權限設定*filename*。 權限設定會控制檔案的讀取和寫入權。 整數運算式*pmode*包含一或兩個下列資訊清單常數，SYS\Stat.h 中所定義。

|*pmode*|意義|
|-|-|
**_S_IREAD**|只允許讀取。
**_S_IWRITE**|允許寫入 (實際上允許讀取和寫入)。
**_S_IREAD** &AMP;#124; **_S_IWRITE**|允許讀取和寫入。

時指定這兩個常數，它們會結合使用位元 or 運算子 (**|**)。 若沒有指定寫入權限，則檔案為唯讀。 請注意，所有檔案皆為可讀取；不可能授與僅限寫入權限。 因此，模式 **_S_IWRITE**並 **_S_IREAD** | **_S_IWRITE**相等。

**_wchmod**是寬字元版本的 **_chmod**; *filename*引數 **_wchmod**是寬字元字串。 **_wchmod**並 **_chmod**行為相同。

這個函式會驗證它的參數。 如果*pmode*不是其中一個資訊清單常數的組合或包含另一組常數，此函式只會忽略這些。 如果*檔名*是**NULL**，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行**errno**設為**EINVAL**和函式會傳回-1。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_chmod**|\<io.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|
|**_wchmod**|\<io.h> 或 \<wchar.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_chmod.c
// This program uses _chmod to
// change the mode of a file to read-only.
// It then attempts to modify the file.
//

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

// Change the mode and report error or success
void set_mode_and_report(char * filename, int mask)
{
   // Check for failure
   if( _chmod( filename, mask ) == -1 )
   {
      // Determine cause of failure and report.
      switch (errno)
      {
         case EINVAL:
            fprintf( stderr, "Invalid parameter to chmod.\n");
            break;
         case ENOENT:
            fprintf( stderr, "File %s not found\n", filename );
            break;
         default:
            // Should never be reached
            fprintf( stderr, "Unexpected error in chmod.\n" );
       }
   }
   else
   {
      if (mask == _S_IREAD)
        printf( "Mode set to read-only\n" );
      else if (mask & _S_IWRITE)
        printf( "Mode set to read/write\n" );
   }
   fflush(stderr);
}

int main( void )
{

   // Create or append to a file.
   system( "echo /* End of file */ >> crt_chmod.c_input" );

   // Set file mode to read-only:
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );

   system( "echo /* End of file */ >> crt_chmod.c_input " );

   // Change back to read/write:
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );

   system( "echo /* End of file */ >> crt_chmod.c_input " );
}
```

```Output

A line of text.

```

```Output

      A line of text.Mode set to read-only
Access is denied.
Mode set to read/write
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_access、_waccess](access-waccess.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_stat、_wstat 函式](stat-functions.md)<br/>

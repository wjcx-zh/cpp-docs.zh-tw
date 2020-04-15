---
title: _access、_waccess
ms.date: 4/2/2020
api_name:
- _access
- _waccess
- _o__access
- _o__waccess
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
- _waccess
- _access
- taccess
- waccess
- _taccess
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
ms.openlocfilehash: 98726726e14aacec75ed99adfa33016b40affd17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350866"
---
# <a name="_access-_waccess"></a>_access、_waccess

判斷檔案是否為唯讀。 這些函式有更安全的版本可用，請參閱 [_access_s、_waccess_s](access-s-waccess-s.md)。

## <a name="syntax"></a>語法

```C
int _access(
   const char *path,
   int mode
);
int _waccess(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>參數

*路徑*<br/>
檔案或目錄路徑。

*模式*<br/>
讀取/寫入屬性。

## <a name="return-value"></a>傳回值

如果檔案有指定模式，每個函式都會傳回 0。 如果命名檔不存在或沒有給定模式,則函數返回 -1;在這種情況下,`errno`如下表所示。

|||
|-|-|
`EACCES`|拒絕存取：檔案的權限設定不允許指定的存取。
`ENOENT`|找不到檔案名稱或路徑。
`EINVAL`|無效的參數。

如需這些傳回碼和其他傳回碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

當與檔一起使用時 **,_access**函數確定指定的檔或目錄是否存在,並且具有*模式*的值指定的屬性。 當與目錄一起使用時 **,_access**僅確定指定的目錄是否存在;_access在 Windows 2000 和更高版本的作業系統中,所有目錄都具有讀取和寫入訪問許可權。

|*模式*值|檢查檔案|
|------------------|---------------------|
|00|只存在|
|02|唯寫|
|04|唯讀|
|06|讀取和寫入|

此函式只檢查檔案和目錄是否為唯讀，不檢查檔案系統安全性設定。 該項作業需要存取權杖。 如需檔案系統安全性的詳細資訊，請參閱 [Access Tokens](/windows/win32/SecAuthZ/access-tokens) (存取權杖)。 ATL 類別的存在就是提供這項功能，請參閱 [CAccessToken 類別](../../atl/reference/caccesstoken-class.md)。

**_waccess**是 **_access**的寬字元版本;**_waccess的***路徑*參數是寬字元字串。 **_waccess**和 **_access**行為相同。

這個函式會驗證它的參數。 如果*路徑*為 NULL 或*模式*未指定有效模式,則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會將 `errno` 設定為 `EINVAL` 並傳回 -1。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess`|**_access**|**_access**|**_waccess**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|----------------------|
|**_access**|\<io.h>|\<errno.h>|
|**_waccess**|\<wchar.h> 或 \<io.h>|\<errno.h>|

## <a name="example"></a>範例

下面的範例使用 **_access**檢查名為crt_ACCESS的檔。C 以查看它是否存在以及是否允許寫入。

```C
// crt_access.c
// compile with: /W1
// This example uses _access to check the file named
// crt_ACCESS.C to see if it exists and if writing is allowed.

#include  <io.h>
#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    // Check for existence.
    if( (_access( "crt_ACCESS.C", 0 )) != -1 )
    {
        printf_s( "File crt_ACCESS.C exists.\n" );

        // Check for write permission.
        // Assume file is read-only.
        if( (_access( "crt_ACCESS.C", 2 )) == -1 )
            printf_s( "File crt_ACCESS.C does not have write permission.\n" );
    }
}
```

```Output
File crt_ACCESS.C exists.
File crt_ACCESS.C does not have write permission.
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_stat、_wstat 函式](stat-functions.md)

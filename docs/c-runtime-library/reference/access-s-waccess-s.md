---
title: _access_s、_waccess_s
ms.date: 4/2/2020
api_name:
- _access_s
- _waccess_s
- _o__access_s
- _o__waccess_s
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
- waccess_s
- access_s
- _waccess_s
- _access_s
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
ms.openlocfilehash: 7f16951b99eb29bcb8c39499c29be1018cb86616
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349130"
---
# <a name="_access_s-_waccess_s"></a>_access_s、_waccess_s

決定檔案的讀取/寫入權限。 這是如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之增強安全性的 [_access、_waccess](access-waccess.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t _access_s(
   const char *path,
   int mode
);
errno_t _waccess_s(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>參數

*路徑*<br/>
檔案或目錄路徑。

*模式*<br/>
權限設定。

## <a name="return-value"></a>傳回值

如果檔案有指定模式，每個函式都會傳回 0。 如果具名檔案不存在或無法在指定模式中存取，則函式會傳回錯誤碼。 在此情況下，函式會如下所示從集合傳回錯誤代碼，也會將 `errno` 設為相同的值。

|errno 值|條件|
|-|-|
`EACCES`|拒絕存取。 檔案的權限設定不允許指定的存取。
`ENOENT`|找不到檔案名稱或路徑。
`EINVAL`|無效的參數。

如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

當與檔一起使用時 **,_access_s**函數確定指定的檔是否存在,並且可以按*模式*的值指定進行訪問。 當與目錄一起使用時 **,_access_s**僅確定指定的目錄是否存在。 在 Windows 2000 和更高版本的作業系統中,所有目錄都具有讀取和寫入訪問許可權。

|模式值|檢查檔案|
|----------------|---------------------|
|00|只存在。|
|02|寫入權限。|
|04|讀取權限。|
|06|讀取和寫入權限。|

讀取或寫入檔案的權限不足以確保能夠開啟檔案。 例如,如果檔被另一個進程鎖定,即使 **_access_s**返回 0,它也可能無法訪問。

**_waccess_s**是 **_access_s**的寬字元版本 **,_waccess_s**的*路徑*參數是寬字元字串。 否則 **,_waccess_s**和 **_access_s**行為相同。

這些函式會驗證它們的參數。 如果*路徑*為 NULL 或*模式*未指定有效模式,則呼叫無效參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_access_s**|\<io.h>|\<errno.h>|
|**_waccess_s**|\<wchar.h> 或 \<io.h>|\<errno.h>|

## <a name="example"></a>範例

此示例使用 **_access_s**檢查名為 crt_access_s.c 的檔以查看是否存在,以及是否允許寫入。

```C
// crt_access_s.c

#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    errno_t err = 0;

    // Check for existence.
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )
    {
        printf_s( "File crt_access_s.c exists.\n" );

        // Check for write permission.
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )
        {
            printf_s( "File crt_access_s.c does have "
                      "write permission.\n" );
        }
        else
        {
            printf_s( "File crt_access_s.c does not have "
                      "write permission.\n" );
        }
    }
    else
    {
        printf_s( "File crt_access_s.c does not exist.\n" );
    }
}
```

```Output
File crt_access_s.c exists.
File crt_access_s.c does not have write permission.
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[_access、_waccess](access-waccess.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_stat、_wstat 函式](stat-functions.md)

---
title: _access、_waccess | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _access
- _waccess
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
- _waccess
- _access
- taccess
- waccess
- _taccess
dev_langs:
- C++
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77876aad65a06cd541949937898496f811375e58
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209599"
---
# <a name="access-waccess"></a>_access、_waccess

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

*path*  
檔案或目錄路徑。

*mode*  
讀取/寫入屬性。

## <a name="return-value"></a>傳回值

如果檔案有指定模式，每個函式都會傳回 0。 如果具名的檔案不存在或沒有指定的模式，則函數會傳回-1在此情況下，`errno`會設定為下表所示。

|||
|-|-|
`EACCES`|拒絕存取：檔案的權限設定不允許指定的存取。
`ENOENT`|找不到檔案名稱或路徑。
`EINVAL`|無效的參數。

如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

當搭配檔案使用時 **_access**函式會判斷是否指定的檔案或目錄存在並具有屬性的值所指定*模式*。 搭配目錄使用時 **_access**只判斷指定的目錄是否存在; 在 Windows 2000 和更新版本作業系統中，所有目錄有讀取和寫入權限。

|*模式*值|檢查檔案|
|------------------|---------------------|
|00|只存在|
|02|唯寫|
|04|唯讀|
|06|讀取和寫入|

此函式只檢查檔案和目錄是否為唯讀，不檢查檔案系統安全性設定。 該項作業需要存取權杖。 如需檔案系統安全性的詳細資訊，請參閱 [Access Tokens](/windows/desktop/SecAuthZ/access-tokens) (存取權杖)。 ATL 類別的存在就是提供這項功能，請參閱 [CAccessToken 類別](../../atl/reference/caccesstoken-class.md)。

**_waccess**是寬字元版本的 **_access**;*路徑*引數 **_waccess**是寬字元字串。 **_waccess**並 **_access**行為相同。

這個函式會驗證它的參數。 如果*路徑*為 NULL 或*模式*未指定有效的模式中，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則函式會將 `errno` 設定為 `EINVAL` 並傳回 -1。

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

下列範例會使用 **_access**檢查名為 crt_ACCESS 的檔案。若要查看它是否存在以及是否允許寫入 C。

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

[檔案處理](../../c-runtime-library/file-handling.md)  
[_chmod、_wchmod](chmod-wchmod.md)  
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)  
[_open、_wopen](open-wopen.md)  
[_stat、_wstat 函式](stat-functions.md)  
---
title: "_access_s、_waccess_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _access_s
- _waccess_s
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
- waccess_s
- access_s
- _waccess_s
- _access_s
dev_langs:
- C++
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 051c2e6a6b0315e2ca4ab3192f28a370d969ec5b
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="accesss-waccesss"></a>_access_s、_waccess_s
決定檔案的讀取/寫入權限。 這是如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之增強安全性的 [_access、_waccess](../../c-runtime-library/reference/access-waccess.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _access_s(   
   const char *path,   
   int mode   
);  
errno_t _waccess_s(   
   const wchar_t *path,   
   int mode   
);  
```  
  
#### <a name="parameters"></a>參數  
 `path`  
 檔案或目錄路徑。  
  
 `mode`  
 權限設定。  
  
## <a name="return-value"></a>傳回值  
 如果檔案有指定模式，每個函式都會傳回 0。 如果具名檔案不存在或無法在指定模式中存取，則函式會傳回錯誤碼。 在此情況下，函式會如下所示從集合傳回錯誤代碼，也會將 `errno` 設為相同的值。  
  
 `EACCES`  
 存取遭拒。 檔案的權限設定不允許指定的存取。  
  
 `ENOENT`  
 找不到檔案名稱或路徑。  
  
 `EINVAL`  
 無效的參數。  
  
 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 搭配檔案使用時，`_access_s` 函式會判斷指定的檔案是否存在，以及可否如指定的由 `mode` 值所存取。 搭配目錄使用時，`_access_s` 只判斷指定的目錄是否存在。 在 [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] 及更新的作業系統中，所有目錄都有讀取和寫入存取權。  
  
|模式值|檢查檔案|  
|----------------|---------------------|  
|00|只存在。|  
|02|寫入權限。|  
|04|讀取權限。|  
|06|讀取和寫入權限。|  
  
 讀取或寫入檔案的權限不足以確保能夠開啟檔案。 例如，如果檔案已由另一個處理序鎖定，即使 `_access_s` 傳回 0，也可能無法存取。  
  
 `_waccess_s` 是寬字元版本的 `_access_s`，而 `_waccess_s` 的 `path` 引數是寬字元字串。 否則 `_waccess_s` 和 `_access_s` 的行為相同。  
  
 這些函式會驗證它們的參數。 如果 `path` 是 `NULL`，或 `mode` 不指定有效的模式，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_taccess_s`|`_access_s`|`_access_s`|`_waccess_s`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_access_s`|\<io.h>|\<errno.h>|  
|`_waccess_s`|\<wchar.h> 或 \<io.h>|\<errno.h>|  
  
## <a name="example"></a>範例  
 本例會使用 `_access_s` 檢查名為 crt_access_s.c 的檔案，以查看它是否存在以及是否允許寫入。  
  
```  
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
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [_access、_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [_chmod、_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_stat、_wstat 函式](../../c-runtime-library/reference/stat-functions.md)

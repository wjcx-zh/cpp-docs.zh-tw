---
title: "_access_s、_waccess_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_access_s"
  - "_waccess_s"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "waccess_s"
  - "access_s"
  - "_waccess_s"
  - "_access_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_access_s 函式"
  - "_taccess_s 函式"
  - "_waccess_s 函式"
  - "access_s 函式"
  - "taccess_s 函式"
  - "waccess_s 函式"
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
caps.latest.revision: 28
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _access_s、_waccess_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷檔案讀取\/寫入權限。  這是 [\_access、\_waccess](../../c-runtime-library/reference/access-waccess.md) 的安全性強化版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 所述。  
  
## 語法  
  
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
  
#### 參數  
 `path`  
 檔案或目錄的路徑。  
  
 `mode`  
 使用權限設定。  
  
## 傳回值  
 如果檔案具有特定模式，每個函式會傳回 0。  如果已具名檔案不存在或在指定的模式無法存取，函式會傳回錯誤碼。  在這種情況下，函式會回傳以下集合中的錯誤碼以及將 `errno` 設為相同的值。  
  
 `EACCES`  
 存取遭拒。  檔案的使用權限設定不允許指定的權限。  
  
 `ENOENT`  
 找不到檔案名稱或路徑。  
  
 `EINVAL`  
 無效參數。  
  
 如需詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 當與檔案一同使用，`_access_s` 函式會判斷指定的檔案是否存在，而且是否可由 `mode`的值所指定的存取模式。  當與目錄一同使用，`_access_s` ，只判斷指定的目錄是否存在。  在 [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] \(含\) 以後版本的作業系統，所有目錄有讀取和寫入存取。  
  
|模式值|檢查檔案。|  
|---------|-----------|  
|00|只存在。|  
|02|寫入權限。|  
|04|讀取權限。|  
|06|讀取和寫入權限|  
  
 讀取或寫入使用權限不確保足夠開啟檔案的能力。  例如，如果檔案被其他處理序鎖定，可能無法存取，即使 `_access_s` 傳回 0。  
  
 `_waccess_s` 是 `_access_s` 的寬字元版本。而 `_waccess_s` 的 `path` 引數是寬字元字串。  否則 `_waccess_s` 和 `_access_s` 的行為相同。  
  
 這些函式會驗證它們的參數。  如果 `path` 是 `NULL` 或 `mode` 沒有指定有效的方式，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 `EINVAL`。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_taccess_s`|`_access_s`|`_access_s`|`_waccess_s`|  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_access_s`|\<io.h\>|\<errno.h\>|  
|`_waccess_s`|\<wchar.h\> or \<io.h\>|\<errno.h\>|  
  
## 範例  
 這個範例會使用 `_access_s` 檢查名為 crt\_access\_s.c 的檔案看它是否存在，還有寫入是否啟用。  
  
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
  
  **File crt\_access\_s.c exists.**  
**File crt\_access\_s.c does not have write permission.**   
## .NET Framework 對等用法  
 <xref:System.IO.FileAccess?displayProperty=fullName>  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_access、\_waccess](../../c-runtime-library/reference/access-waccess.md)   
 [\_chmod、\_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_stat、\_wstat 函式](../../c-runtime-library/reference/stat-functions.md)
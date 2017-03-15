---
title: "_access、_waccess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_access"
  - "_waccess"
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
  - "_waccess"
  - "_access"
  - "taccess"
  - "waccess"
  - "_taccess"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_access 函式"
  - "_taccess 函式"
  - "_waccess 函式"
  - "access 函式"
  - "taccess 函式"
  - "waccess 函式"
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# _access、_waccess
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要判斷檔案是否為唯讀  可用更安全的版本；請參閱 [\_access\_s、\_waccess\_s](../../c-runtime-library/reference/access-s-waccess-s.md)。  
  
## 語法  
  
```  
int _access(   
   const char *path,   
   int mode   
);  
int _waccess(   
   const wchar_t *path,   
   int mode   
);  
```  
  
#### 參數  
 `path`  
 檔案或目錄的路徑。  
  
 `mode`  
 讀取\/寫入屬性。  
  
## 傳回值  
 如果檔案具有特定模式，每個函式會傳回 0。  如果具名檔案不存在或沒有指定模式;在這種情況下，如下表所示 `errno` 設定，函式會傳回 1。  
  
 `EACCES`  
 存取遭拒:檔案的使用權限設定不允許指定的權限。  
  
 `ENOENT`  
 找不到檔案名稱或路徑。  
  
 `EINVAL`  
 無效參數。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 、和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 當使用檔案，則 `_access` 函式會判斷指定檔案或目錄是否存在且具有指定 `mode`的值的屬性。  當使用目錄 `_access` ，判斷指定的目錄是否存在;只有在 [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] \(含\) 以後版本的作業系統，所有目錄有讀取和寫入權限。  
  
|`mode` 值|檢查檔案。|  
|--------------|-----------|  
|00|只存在|  
|02|唯寫|  
|04|唯讀|  
|06|讀取和寫入|  
  
 這個函式只檢查是否檔案和目錄是唯讀的，它不會檢查檔案系統安全性設定。  對於您需要存取語彙基元。  如需檔案系統安全性的詳細資訊，請參閱 [存取語彙基元。](http://msdn.microsoft.com/library/windows/desktop/aa374909)。  ATL 類別沒有提供這項功能;請參閱 [CAccessToken Class](../../atl/reference/caccesstoken-class.md)。  
  
 `_waccess` 是 `_access` 的寬字元版本。 `_waccess` 的 `path` 引數是寬字元字串。  `_waccess` 和 `_access` 其餘行為相同。  
  
 這個函式會驗證它的參數。  如果 `path` 是 `NULL` 或 `mode` 沒有指定有效的方式，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，則函式會將 `errno` 設定為 `EINVAL`並傳回。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_taccess`|`_access`|`_access`|`_waccess`|  
  
## 需求  
  
|常式|必要的標頭|選擇性的標頭檔|  
|--------|-----------|-------------|  
|`_access`|\<io.h\>|\<errno.h\>|  
|`_waccess`|\<wchar.h\> or \<io.h\>|\<errno.h\>|  
  
## 範例  
 下列範例會使用 `_access` 檢查名為 crt\_ACCESS.C 的檔案看它是否存在，還有寫入是否啟用。  
  
```  
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
  
  **crt\_ACCESS.C 檔案存在.**  
**crt\_ACCESS.C 檔案沒有寫入權限。**   
## .NET Framework 對等用法  
 <xref:System.IO.FileAccess?displayProperty=fullName>  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_chmod、\_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_stat、\_wstat 函式](../../c-runtime-library/reference/stat-functions.md)
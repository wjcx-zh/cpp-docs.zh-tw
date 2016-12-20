---
title: "errno、_doserrno、_sys_errlist 和 _sys_nerr | Microsoft Docs"
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
  - "_errno"
apilocation: 
  - "msvcrt.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_sys_errlist"
  - "errno"
  - "_sys_nerr"
  - "_doserrno"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_doserrno 全域變數"
  - "_sys_errlist 全域變數"
  - "_sys_nerr 全域變數"
  - "doserrno 全域變數"
  - "errno 全域變數"
  - "錯誤碼, 列印"
  - "sys_errlist 全域變數"
  - "sys_nerr 全域變數"
ms.assetid: adbec641-6d91-4e19-8398-9a34046bd369
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# errno、_doserrno、_sys_errlist 和 _sys_nerr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

全域巨集，具有程式執行期間所設定的錯誤碼，以及用於顯示的錯誤碼的字串對應項目。  
  
## 語法  
  
```  
#define errno   (*_errno()) #define _doserrno   (*__doserrno()) #define _sys_errlist (__sys_errlist()) #define _sys_nerr (*__sys_nerr())  
```  
  
## 備註  
 在程式啟動期間，執行階段會將 `errno` 和 `_doserrno` 設為 0。  `errno` 設定於系統層級呼叫發生錯誤時。  由於 `errno` 保存最後將其設定的呼叫值，此值也許可以由後續的呼叫變更。  在發生錯誤時設定 `errno` 的執行階段程式庫呼叫，並不會在成功後清除 `errno`。  一律在某個可能會設定 `errno` 的呼叫之前，立即呼叫 `_set_errno(0)` 將其清除，並且在設定 errno 的呼叫之後立即檢查。  
  
 發生錯誤時，`errno` 不一定會設定為與系統呼叫傳回之錯誤碼相同的值。  `_doserrno` 會針對 I\/O 作業儲存與 `errno` 程式碼相等的作業系統錯誤碼。  對於大部分的非 I\/O 作業，`_doserrno` 的值都是未設定。  
  
 每個 `errno` 值都與 `_sys_errlist` 中的錯誤訊息相關，此錯誤訊息可以透過使用其中一個 [perror](../c-runtime-library/reference/perror-wperror.md) 函式列印出來，或是使用其中一個 [strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) 或 [strerror\_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) 函式儲存在字串中。  `perror` 和 `strerror` 函式會使用 `_sys_errlist` 陣列和 `_sys_nerr` \(`_sys_errlist` 中的項目數\) 來處理錯誤資訊。  基於程式碼的安全考量，`_sys_errlist` 和 `_sys_nerr` 已遭到取代。  建議您使用更安全且更具功能的版本，而非全域巨集，如下所示：  
  
|全域巨集|功能相同項目|  
|----------|------------|  
|`_doserrno`|[\_get\_doserrno](../c-runtime-library/reference/get-doserrno.md)、[\_set\_doserrno](../c-runtime-library/reference/set-doserrno.md)|  
|`errno`|[\_get\_errno](../c-runtime-library/reference/get-errno.md), [\_set\_errno](../c-runtime-library/reference/set-errno.md)|  
|`_sys_errlist`, `_sys_nerr`|[strerror\_s、\_strerror\_s、\_wcserror\_s、\_\_wcserror\_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|  
  
 程式庫數學常式會以呼叫 [\_matherr](../c-runtime-library/reference/matherr.md) 的方式設定 `errno`。  若要以不同方式處理算術錯誤，請根據 `_matherr` 參考描述撰寫自己的常式，並命名為 `_matherr`。  
  
 下表中的所有 `errno` 值是 \<errno.h\> 中的預先定義常數，並且與 Unix 相容。  在 ISO C99 標準中只有指定 `ERANGE`、`EILSEQ`和 `EDOM`。  
  
|常數|系統錯誤訊息|值|  
|--------|------------|-------|  
|`EPERM`|不允許操作|1|  
|`ENOENT`|無此檔案或目錄|2|  
|`ESRCH`|無此處理序|3|  
|`EINTR`|中斷的函式|4|  
|`EIO`|I\/O 錯誤|5|  
|`ENXIO`|無此裝置或位址|6|  
|`E2BIG`|引數清單太長|7|  
|`ENOEXEC`|Exec 格式錯誤|8|  
|`EBADF`|檔案編號錯誤|9|  
|`ECHILD`|沒有繁衍的處理序|10|  
|`EAGAIN`|沒有處理序或沒有足夠的記憶體或已達最大達巢狀層次|11|  
|`ENOMEM`|沒有足夠的記憶體|12|  
|`EACCES`|權限遭拒|13|  
|`EFAULT`|位址錯誤|14|  
|`EBUSY`|裝置或資源忙碌|16|  
|`EEXIST`|檔案存在|17|  
|`EXDEV`|跨裝置連結|18|  
|`ENODEV`|無此裝置|19|  
|`ENOTDIR`|不是目錄|20|  
|`EISDIR`|是目錄|21|  
|`EINVAL`|無效引數|22|  
|`ENFILE`|系統中開啟太多檔案|23|  
|`EMFILE`|開啟太多檔案|24|  
|`ENOTTY`|不適當的 I\/O 控制作業|25|  
|`EFBIG`|檔案太大|27|  
|`ENOSPC`|裝置無剩餘空間|28|  
|`ESPIPE`|無效搜尋|29|  
|`EROFS`|唯讀檔案系統|30|  
|`EMLINK`|太多連結|31|  
|`EPIPE`|管道中斷|32|  
|`EDOM`|數學引數|33|  
|`ERANGE`|結果太大|34|  
|`EDEADLK`|會發生資源死結|36|  
|`EDEADLOCK`|針對與較舊 Microsoft C 版本的相容性而言和 EDEADLK 是相同的|36|  
|`ENAMETOOLONG`|檔名太長|38|  
|`ENOLCK`|沒有鎖定可用|39|  
|`ENOSYS`|不支援的函式|40|  
|`ENOTEMPTY`|目錄非空白|41|  
|`EILSEQ`|位元組序列不正確|42|  
|`STRUNCATE`|字串遭截斷|80|  
  
## 需求  
  
|全域巨集|必要的標頭|選擇性標頭|  
|----------|-----------|-----------|  
|`errno`|\<errno.h\> 或 \<stdlib.h\>、\<cerrno\> 或 \<cstdlib\> \(C\+\+\)||  
|`_doserrno`, `_sys_errlist`, `_sys_nerr`|\<stdlib.h\>、\<cstdlib\> \(C\+\+\)|\<errno.h\>、\<cerrno\> \(C\+\+\)|  
  
 `_doserrno`、`_sys_errlist` 和 `_sys_nerr` 是 Microsoft 擴充功能。  如需詳細的相容性資訊，請參閱[相容性](../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [全域變數](../c-runtime-library/global-variables.md)   
 [errno 常數](../c-runtime-library/errno-constants.md)   
 [perror、\_wperror](../c-runtime-library/reference/perror-wperror.md)   
 [strerror、\_strerror、\_wcserror、\_\_wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)   
 [strerror\_s、\_strerror\_s、\_wcserror\_s、\_\_wcserror\_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)   
 [\_get\_doserrno](../c-runtime-library/reference/get-doserrno.md)   
 [\_set\_doserrno](../c-runtime-library/reference/set-doserrno.md)   
 [\_get\_errno](../c-runtime-library/reference/get-errno.md)   
 [\_set\_errno](../c-runtime-library/reference/set-errno.md)
---
title: "_rmdir、_wrmdir | Microsoft Docs"
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
  - "_wrmdir"
  - "_rmdir"
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
  - "trmdir"
  - "_trmdir"
  - "wrmdir"
  - "_rmdir"
  - "_wrmdir"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_rmdir 函式"
  - "_trmdir 函式"
  - "_wrmdir 函式"
  - "目錄 [C++], 刪除"
  - "目錄 [C++], 移除"
  - "rmdir 函式"
  - "trmdir 函式"
  - "wrmdir 函式"
ms.assetid: 652c2a5a-b0ac-4493-864e-1edf484333c5
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _rmdir、_wrmdir
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

刪除目錄。  
  
## 語法  
  
```  
  
      int _rmdir(  
   const char *dirname   
);  
int _wrmdir(  
   const wchar_t *dirname   
);  
```  
  
#### 參數  
 `dirname`  
 要移除的目錄路徑。  
  
## 傳回值  
 如果目錄已成功刪除，這些函式都會傳回 0。  傳回值為 \-1 表示錯誤，`errno` 會設為下列其中一個值:  
  
 **ENOTEMPTY**  
 指定的路徑不是目錄，此目錄不是空的，或者目錄是工作目錄或根目錄。  
  
 `ENOENT`  
 路徑無效。  
  
 **EACCES**  
 程式具有開啟控制代碼目錄。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 、和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 `_rmdir` 函式刪除`dirname`指定的目錄。  目錄必須是空的，所以它不能是工作目錄或根目錄。  
  
 `_wrmdir` 是 `_rmdir` 的寬字元版本。 `_wrmdir` 的 `dirname` 引數是寬字元字串。  `_wrmdir` 和 `_rmdir` 其餘行為相同。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_trmdir`|`_rmdir`|`_rmdir`|`_wrmdir`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_rmdir`|\<direct.h\>|  
|`_wrmdir`|\<direct.h\>  或 \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
 請參閱 [\_mkdir](../../c-runtime-library/reference/mkdir-wmkdir.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::IO::Directory::Delete](https://msdn.microsoft.com/en-us/library/system.io.directory.delete.aspx)  
  
## 請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [\_chdir、\_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_mkdir、\_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)
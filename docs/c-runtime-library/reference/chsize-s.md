---
title: "_chsize_s | Microsoft Docs"
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
  - "_chsize_s"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "chsize_s"
  - "_chsize_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_chsize_s 函式"
  - "chsize_s 函式"
  - "檔案 [C++], 變更大小"
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _chsize_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

改變檔案大小。  這是 [\_chsize](../../c-runtime-library/reference/chsize.md) 的安全性強化版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 所述。  
  
## 語法  
  
```  
errno_t _chsize_s(   
   int fd,  
   __int64 size   
);  
```  
  
#### 參數  
 `fd`  
 參考開啟檔案的檔案描述項。  
  
 `size`  
 新檔案的長度，以位元組為單位。  
  
## 傳回值  
 如果成功變更檔案大小，`_chsize_s` 會傳回值 0。  零以外的傳回值表示錯誤: 如果指定的檔案鎖定物件的存取，傳回值為 `EACCES` ，如果指定的檔案是唯讀或描述項無效，則為 `EBADF` ，如果裝置沒有多餘空間，則為 `ENOSPC` ，如果大小小於零，則為 `EINVAL` 。  `errno`  設定為相同值。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 、和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
## 備註  
 `_chsize_s` 函式擴充或截斷與 `fd` 相關聯之檔案至 `size`的指定長度。  檔案必須開啟允許寫入模式。  如果檔案已擴充，附加 null 字元 \('\\0'\)。  如果檔案已截斷，從縮短的檔案結尾至檔案的原始長度的任何資料將遺失。  
  
 `_chsize_s` 會將 64 位元整數做為檔案大小，因此可以處理大小大於 4 GB 的檔案。  `_chsize` 僅限於 32 位元檔案大小。  
  
 這個函式會驗證它的參數。  如果 `fd` 不是有效的檔案描述項或大小小於零，將叫用無效參數的處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_chsize_s`|\<io.h\>|\<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
  
-   [System::IO::Stream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.stream.setlength.aspx)  
  
-   [System::IO::FileStream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.filestream.setlength.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_chsize](../../c-runtime-library/reference/chsize.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)
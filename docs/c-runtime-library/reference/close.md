---
title: "_close | Microsoft Docs"
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
  - "_close"
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
  - "_close"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_close 函式"
  - "close 函式"
  - "檔案 [C++], 關閉"
ms.assetid: 4708a329-8acf-4cd9-b7b0-a952e1897247
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _close
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

關閉檔案。  
  
## 語法  
  
```  
int _close(   
   int fd   
);  
```  
  
#### 參數  
 `fd`  
 參考開啟檔案的檔案描述項。  
  
## 傳回值  
 如果檔案已成功關閉，則`_close` 會傳回 0。  回傳值為 1 表示錯誤。  
  
## 備註  
 `_close` 函式會關閉檔案相關聯的 `fd`。  
  
 檔案描述和基礎作業系統檔案控制代碼已關閉。  因此，如果檔案原本是使用Win32函式`CreateFile`開啟並使用`_open_osfhandle`轉換為檔案描述的話，則呼叫`CloseHandle`是不必要的。  
  
 這個函式會驗證它的參數。  如果 `fd` 為壞的檔案描述符，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會傳回 \-1和`errno`，並設為 `EBADF` 。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_close`|\<io.h\>|\<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
 請參閱 [\_open](../../c-runtime-library/reference/open-wopen.md) 的範例。  
  
## 請參閱  
 [低層級 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_chsize](../../c-runtime-library/reference/chsize.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_dup、\_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_unlink、\_wunlink](../../c-runtime-library/reference/unlink-wunlink.md)
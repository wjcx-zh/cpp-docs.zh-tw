---
title: "_commit | Microsoft Docs"
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
  - "_commit"
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
  - "_commit"
  - "commit"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_commit 函式"
  - "commit 函式"
  - "將檔案認可至磁碟"
  - "檔案 [C++], 清除"
  - "將檔案清除至磁碟"
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _commit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

清除檔案直接儲存到磁碟。  
  
## 語法  
  
```  
int _commit(   
   int fd   
);  
```  
  
#### 參數  
 `fd`  
 參考開啟檔案的檔案描述項。  
  
## 傳回值  
 如果檔案已成功清除至磁碟，`_commit` 會傳回 0。  回傳值為 1 表示錯誤。  
  
## 備註  
 `_commit` 函式會強制作業系統將檔案寫入 `fd` 到磁碟。  這會確保立即清除指定的檔案，而不是作業系統的酌情權。  
  
 如果 `fd` 為無效檔案描述符，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果執行允許繼續，函式會回傳\-1，並且`errno`會設定為 `EBADF`。  
  
## 需求  
  
|常式|必要的標頭|選擇性的標頭檔|  
|--------|-----------|-------------|  
|`_commit`|\<io.h\>|\<errno.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 請參閱  
 [低層級 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_read](../../c-runtime-library/reference/read.md)   
 [\_write](../../c-runtime-library/reference/write.md)
---
title: "fsetpos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fsetpos"
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
  - "fsetpos"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fsetpos 函式"
  - "資料流, 設定位置指標"
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# fsetpos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將資料流位置指示器。  
  
## 語法  
  
```  
int fsetpos(   
   FILE *stream,  
   const fpos_t *pos   
);  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標。  
  
 `pos`  
 位置指示器儲存區。  
  
## 傳回值  
 如果成功，`fsetpos` 會傳回 0。  如果失敗，則函式會傳回非零的值並將 `errno` 設定為下列資訊清單常數之一 \(定義於 ERRNO.H\): `EBADF`，表示檔案無法存取或物件的 `stream` 不是有效的檔案結構;或 `EINVAL`，表示 `stream` 或 `pos` 指定了無效的值傳遞。  如果傳入無效的參數，這些函式會呼叫無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 所述。  
  
 如需有關這些回傳碼和其他回傳碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `fsetpos` 函式會將 `stream` 的檔案位置指標到 `pos`的值*，* 在 `fgetpos` 的先前的呼叫取得物件的 `stream`*。*函式清除檔案結尾指示器並移除 [ungetc](../../c-runtime-library/reference/ungetc-ungetwc.md) 作用為 `stream`*。*在呼叫 `fsetpos`之後，可能會將 `stream` 的下一個作業或輸出。  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`fsetpos`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [fgetpos](../../c-runtime-library/reference/fgetpos.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)
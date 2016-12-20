---
title: "_get_fmode | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_fmode"
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
  - "get_fmode"
  - "_get_fmode"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_fmode 函式"
  - "檔案轉譯 [C++], 預設模式"
  - "get_fmode 函式"
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_fmode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得檔案 I\/O 作業的預設檔案傳輸模式。  
  
## 語法  
  
```  
errno_t _get_fmode(   
   int * pmode   
);  
```  
  
#### 參數  
 \[out\] `pmode`  
 要填入的整數的指標目前預設模式: `_O_TEXT` 或 `_O_BINARY`。  
  
## 傳回值  
 如果成功則回傳零，如果失敗則為錯誤碼。  如果 `pmode` 為 `NULL`，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `EINVAL`。  
  
## 備註  
 函式取得 [\_fmode](../../c-runtime-library/fmode.md) 全域變數的值。  這個變數的低階指定版本模式的預設檔案和資料流檔案 I\/O 作業，例如 `_open`、 `_pipe`、 `fopen`和 `freopen`。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_get_fmode`|\<stdlib.h\>|\<fcntl.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
 請參閱 [\_set\_fmode](../../c-runtime-library/reference/set-fmode.md)中的範例。  
  
## NET Framework 對等  
 不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [\_fmode](../../c-runtime-library/fmode.md)   
 [\_set\_fmode](../../c-runtime-library/reference/set-fmode.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)   
 [文字和二進位模式檔案 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)
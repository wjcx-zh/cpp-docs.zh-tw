---
title: "_setmaxstdio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_setmaxstdio"
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
  - "setmaxstdio"
  - "_setmaxstdio"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_setmaxstdio 函式"
  - "開啟檔案上限"
  - "開啟檔案, 最大值"
  - "setmaxstdio 函式"
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _setmaxstdio
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

同時設定開啟檔案數目的最大值在 `stdio` 層級。  
  
## 語法  
  
```  
int _setmaxstdio(  
   int newmax   
);  
```  
  
#### 參數  
 `newmax`  
 同時新增開啟檔案數目的最大值在 `stdio` 層級。  
  
## 傳回值  
 如果成功則傳回 `newmax`，否則傳回 \-1。  
  
 如果 `newmax` 小於 `_IOB_ENTRIES` 或大於然後控制代碼數目上限可用的作業系統，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這個函式會傳回 `errno`，並將 `EINVAL` 設為 \-1。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_setmaxstdio` 函式變更可能同時是在 `stdio` 層級的檔案數目的最大值。  
  
 C 執行階段 I\/O 現在支援比起舊版，在 Win32 平台的能開啟較多檔案。  2,048 檔案可以同時開啟於 [層級的 lowio](../../c-runtime-library/low-level-i-o.md) \(即開啟和存取透過 `_open`、 `_read`， `_write`，依此類推 I\/O 函式家族\)。  512 檔案可以同時開啟於 [層級的 lowio](../../c-runtime-library/stream-i-o.md) \(即開啟和存取透過 `fopen`、 `fgetc`， `fputc`，依此類推 I\/O 函式家族\)。  512 開啟檔案限制在 `stdio` 層級的可以加入最多 2,048 透過 `_setmaxstdio` 函式。  
  
 由於 `stdio`層級的函式，例如 `fopen`，它會在 `lowio` 函式上方，最多 2,048 是同時透過 C 執行階段程式庫存取開啟檔案數目的一種硬式上限。  
  
> [!NOTE]
>  這個方法可能是由特定 Win32 平台和組態支援。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_setmaxstdio`|\<stdio.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
 如需使用 [\_getmaxstdio](../../c-runtime-library/reference/getmaxstdio.md)方法的範例，請參閱 `_setmaxstdio`。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)
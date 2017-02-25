---
title: "_setmbcp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_setmbcp"
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
  - "api-ms-win-crt-locale-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_setmbcp"
  - "setmbcp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_setmbcp 函式"
  - "多位元組字碼頁"
  - "setmbcp 函式"
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _setmbcp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定新的多位元組字碼頁。  
  
## 語法  
  
```  
int _setmbcp(  
   int codepage   
);  
```  
  
#### 參數  
 `codepage`  
 與地區設定無關的多位元組常式的新的字碼頁。  
  
## 傳回值  
 如果字碼頁成功，將傳回 0。  如果無效的字碼頁值為 `codepage`提供，則會傳回– 1 和字碼頁不變。  如果記憶體配置失敗，將 `errno` 設為 `EINVAL` 。  
  
## 備註  
 `_setmbcp` 函式指定新的多位元組字碼頁。  根據預設，這個執行階段系統自動設定多位元組字碼頁為系統預設 ANSI 字碼頁。  多位元組字碼頁影響不為地區設定相關的所有多位元組常式。  不過，則指示 `_setmbcp` 為目前地區設定所定義的字碼頁 \(請參閱資訊清單常數和關聯的行為結果下列清單\)。  如需依賴地區設定字碼頁而非多位元組字碼頁多位元組常式的清單，請參閱 [多位元組字元序列的說明](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)。  
  
 多位元組字碼頁也會影響處理下列執行階段程式庫常式的多位元組字元:  
  
||||  
|-|-|-|  
|[\_exec 函式](../../c-runtime-library/exec-wexec-functions.md)|[\_mktemp](../../c-runtime-library/reference/mktemp-wmktemp.md)|[\_stat](../../c-runtime-library/reference/stat-functions.md)|  
|[\_fullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)|[\_spawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)|[\_tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[\_makepath](../../c-runtime-library/reference/makepath-wmakepath.md)|[\_splitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)|[tmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
  
 此外，接收多位元組字元 `argv` 或 `envp` 程式引數中的所有執行階段程式庫常式，當參數 \(例如 `_exec` 和 `_spawn` 家族\) 根據多位元組字碼頁處理這些資料。  因此，這些常式受變更多位元組字碼頁對 `_setmbcp` 的呼叫所影響。  
  
 `codepage` 引數可以設定為下列其中一個值。  
  
-   `_MB_CP_ANSI` 使用從作業系統取得的 ANSI 字碼頁在程式啟動。  
  
-   `_MB_CP_LOCALE` 使用先前呼叫所取得的目前地區設定的字碼頁 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
-   `_MB_CP_OEM` 使用從作業系統取得的 OEM 字碼頁在程式啟動。  
  
-   `_MB_CP_SBCS` 使用單一位元組字碼頁。  當字碼頁設定為 `_MB_CP_SBCS`時的常式，例如 [\_ismbblead](../../c-runtime-library/reference/ismbblead-ismbblead-l.md) 永遠傳回 false。  
  
-   其他的有效字碼頁值，不論的值是否為 ANSI、OEM，或者其他作業系統支援的字碼頁 \(除了 UTF\-7 及 UTF\-8，不支援\)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_setmbcp`|\<mbctype.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 請參閱  
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)
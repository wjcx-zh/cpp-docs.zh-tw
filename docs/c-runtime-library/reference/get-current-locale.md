---
title: "_get_current_locale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_current_locale"
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
  - "get_current_locale"
  - "__get_current_locale"
  - "_get_current_locale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__get_current_locale 函式"
  - "_get_current_locale 函式"
  - "get_current_locale 函式"
  - "地區設定, 取得相關資訊"
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _get_current_locale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得表示目前地區設定的地區設定物件。  
  
## 語法  
  
```  
_locale_t _get_current_locale(void);  
```  
  
## 傳回值  
 表示目前地區設定的地區設定物件。  
  
## 備註  
 `_get_current_locale` 函式加入至執行緒的目前設定的地區設定並傳回表示該地區設定的地區設定物件。  
  
 這個函式`__get_current_locale` 先前的名稱 \(與兩個前置底線\) 已被取代。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_get_current_locale`|\<locale.h \- 地區設定\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 沒有對等用法。  
  
## 請參閱  
 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale、\_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../../c-runtime-library/reference/free-locale.md)
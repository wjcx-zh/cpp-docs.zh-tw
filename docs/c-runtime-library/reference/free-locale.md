---
title: "_free_locale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_free_locale"
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
  - "__free_locale"
  - "free_locale"
  - "_free_locale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__free_locale 函式"
  - "_free_locale 函式"
  - "free_locale 函式"
  - "地區設定, 釋放"
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _free_locale
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

釋放地區設定物件。  
  
## 語法  
  
```  
void _free_locale(  
   _locale_t locale  
);  
```  
  
#### 參數  
 `locale`  
 要釋放的地區設定物件。  
  
## 備註  
 `_free_locale` 函式會用來從`_get_current_locale` 或 `_create_locale`呼叫釋放衍生的地區設定物件加入。  
  
 這個函式`__free_locale` 先前的名稱 \(與兩個前置底線\) 已被取代。  
  
## 需求  
  
|`Routine`|必要的標頭|  
|---------------|-----------|  
|`_free_locale`|\<locale.h \- 地區設定\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 沒有對等用法。  
  
## 請參閱  
 [\_get\_current\_locale](../../c-runtime-library/reference/get-current-locale.md)   
 [\_create\_locale、\_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)
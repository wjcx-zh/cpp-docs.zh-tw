---
title: "_daylight、_dstbias、_timezone 和 _tzname | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tzname"
  - "_timezone"
  - "timezone"
  - "_daylight"
  - "_tzname"
  - "daylight"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "時區"
  - "時間調整"
  - "時區變數"
  - "_tzname 函式"
  - "_daylight 函式"
  - "_timezone 函式"
  - "daylight 函式"
  - "當地時間調整"
  - "timezone 函式"
  - "tzname 函式"
  - "時區變數"
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _daylight、_dstbias、_timezone 和 _tzname
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`_daylight`、 `_dstbias`、 `_timezone`和 `_tzname` 用於一些時間和日期常式做區域的時間調整。  這些全域變數已被更安全的版本所取代，您應該使用它們。  
  
|全域變數|對等的功能|  
|----------|-----------|  
|`_daylight`|[\_get\_daylight](../c-runtime-library/reference/get-daylight.md)|  
|`_dstbias`|[\_get\_dstbias](../c-runtime-library/reference/get-dstbias.md)|  
|`_timezone`|[\_get\_timezone](../c-runtime-library/reference/get-timezone.md)|  
|`_tzname`|[\_get\_tzname](../c-runtime-library/reference/get-tzname.md)|  
  
 它們在 Time.h 如下宣告。  
  
## 語法  
  
```  
extern int _daylight;   
extern int _dstbias;   
extern long _timezone;   
extern char *_tzname[2];  
```  
  
## 備註  
 在呼叫 `_ftime`， `localtime`或 `_tzset`， `_daylight`、 `_dstbias`、 `_timezone`和 `_tzname` 的值取自 `TZ` 環境變數的值決定。  如果您未明確設定 `TZ`的值， `_tzname[0]` 和 `_tzname[1]` 分別包含「PST」和「PDT」預設值。定期管理函式 \([\_tzset](../c-runtime-library/reference/tzset.md)、 [\_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md)和 [localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md)\) 嘗試透過查詢預設值的作業系統設定 `_daylight`、 `_dstbias` 和 `_timezone` 的值每個變數。  時區全域變數值下表中所示。  
  
|變數|值|  
|--------|-------|  
|`_daylight`|如果日光節約時間 \(DST\) 區域在 `TZ` 指定或從作業系統所決定，非0;否則，則為 0。  預設值為 1。|  
|`_dstbias`|日光節約時間位移|  
|`_timezone`|差異在 Coordinated Universal Time \(UTC\) 與本地時間的秒數。  預設值為 28,800。|  
|`_tzname[0]`|從 `TZ` 環境變數衍生的時區名稱。  預設值為 "PST"。|  
|`_tzname[1]`|從 `TZ` 環境變數衍生的DST名稱。  預設值為「PDT」\(如太平洋日光節約時間\)。|  
  
## 請參閱  
 [全域變數](../c-runtime-library/global-variables.md)   
 [\_get\_daylight](../c-runtime-library/reference/get-daylight.md)   
 [\_get\_dstbias](../c-runtime-library/reference/get-dstbias.md)   
 [\_get\_timezone](../c-runtime-library/reference/get-timezone.md)   
 [\_get\_tzname](../c-runtime-library/reference/get-tzname.md)
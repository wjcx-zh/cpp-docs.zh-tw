---
title: "地區設定分類 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "LC_MAX"
  - "LC_MIN"
  - "LC_MONETARY"
  - "LC_TIME"
  - "LC_NUMERIC"
  - "LC_COLLATE"
  - "LC_CTYPE"
  - "LC_ALL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LC_ALL 常數"
  - "LC_COLLATE 常數"
  - "LC_CTYPE 常數"
  - "LC_MAX 常數"
  - "LC_MIN 常數"
  - "LC_MONETARY 常數"
  - "LC_NUMERIC 常數"
  - "LC_TIME 常數"
  - "地區設定常數"
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 地區設定分類
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <locale.h>  
  
```  
  
## 備註  
 地區設定分類為當地語系化常式所使用的資訊清單常數指定要用於程式的地區設定資訊的哪個部分。  地區設定參考位置 \(或國家\/地區\) 程式的某些層面可自訂。  與地區設定相關的類別含有，例如，日期格式或貨幣值的顯示格式。  
  
|Locale::category|受影響的程式部分|  
|----------------------|--------------|  
|`LC_ALL`|所有地區設定特定行為 \(所有分類\)|  
|`LC_COLLATE`|`strcoll` 和 `strxfrm` 函式行為|  
|`LC_CTYPE`|字元處理行為才會生效 \(除非 **isdigit**、 `isxdigit`、 `mbstowcs`和 `mbtowc`，不會受到影響\)|  
|`LC_MAX`|與 `LC_TIME` 相同|  
|`LC_MIN`|與 `LC_ALL` 相同|  
|`LC_MONETARY`|`localeconv` 函式傳回的貨幣格式資訊|  
|`LC_NUMERIC`|小數點的字元格式化輸出的常式 \(例如 `printf`\)，則資料轉換常式的和對於非貨幣的格式化資訊由 `localeconv`函式傳回。|  
|`LC_TIME`|`strftime`函式的行為|  
  
 如需範例，請參閱 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
## 請參閱  
 [localeconv](../c-runtime-library/reference/localeconv.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll 函式](../c-runtime-library/strcoll-functions.md)   
 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [全域常數](../c-runtime-library/global-constants.md)
---
title: "_daylight、_dstbias、_timezone 和 _tzname | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tzname
- _timezone
- timezone
- _daylight
- _tzname
- daylight
dev_langs: C++
helpviewer_keywords:
- time zones
- time adjustments
- timezone variables
- _tzname function
- _daylight function
- _timezone function
- daylight function
- local time adjustments
- timezone function
- tzname function
- time-zone variables
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c2c14f4bf492b18107aefc744d6e443fdeef3fec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="daylight-dstbias-timezone-and-tzname"></a>_daylight、_dstbias、_timezone 和 _tzname
有些時間和日期常式使用 `_daylight`、`_dstbias`、`_timezone` 和 `_tzname` 調整本機時間。 這些全域變數已為更安全的函式版本所取代，它們應該用來取代全域變數。  
  
|全域變數|功能相同項目|  
|---------------------|---------------------------|  
|`_daylight`|[_get_daylight](../c-runtime-library/reference/get-daylight.md)|  
|`_dstbias`|[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)|  
|`_timezone`|[_get_timezone](../c-runtime-library/reference/get-timezone.md)|  
|`_tzname`|[_get_tzname](../c-runtime-library/reference/get-tzname.md)|  
  
 它們在 Time.h 中宣告，如下所示。  
  
## <a name="syntax"></a>語法  
  
```  
extern int _daylight;   
extern int _dstbias;   
extern long _timezone;   
extern char *_tzname[2];  
```  
  
## <a name="remarks"></a>備註  
 在呼叫 `_ftime`、`localtime` 或 `_tzset` 時，`_daylight`、`_dstbias`、`_timezone` 和 `_tzname` 的值是從 `TZ` 環境變數的值決定。 如果您沒有明確設定 `TZ` 的值，`_tzname[0]` 和 `_tzname[1]` 會分別包含 "PST" 和 "PDT" 的預設設定。  時間管理函式 ([_tzset](../c-runtime-library/reference/tzset.md)、[_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) 和 [localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md)) 嘗試藉由在作業系統中查詢每個變數的預設值，設定值 `_daylight`、`_dstbias` 和 `_timezone`。 下表顯示時區全域變數值。  
  
|變數|值|  
|--------------|-----------|  
|`_daylight`|如果在 `TZ` 中指定日光節約時間 (DST) 區域，或從作業系統決定，則為非零，否則為 0。 預設值為 1。|  
|`_dstbias`|日光節約時間位移。|  
|`_timezone`|國際標準時間和本機時間之間的時差，以秒為單位。 預設值為 28,800。|  
|`_tzname[0]`|時區名稱衍生自 `TZ` 環境變數。 預設值是 "PST"。|  
|`_tzname[1]`|DST 時區名稱衍生自 `TZ` 環境變數。 預設值是 "PDT" (太平洋日光節約時間)。|  
  
## <a name="see-also"></a>另請參閱  
 [全域變數](../c-runtime-library/global-variables.md)   
 [_get_daylight](../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias](../c-runtime-library/reference/get-dstbias.md)   
 [_get_timezone](../c-runtime-library/reference/get-timezone.md)   
 [_get_tzname](../c-runtime-library/reference/get-tzname.md)
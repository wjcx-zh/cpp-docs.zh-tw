---
title: "CTimeSpan Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CTimeSpan"
  - "CTimeSpan"
  - "timespan"
  - "ATL::CTimeSpan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTimeSpan class"
  - "已耗用時間, CTimeSpan object"
  - "shared classes, CTimeSpan"
  - "time span"
  - "時間, elapsed"
  - "timespan"
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
caps.latest.revision: 17
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTimeSpan Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

時間，在內部會儲存為秒數時間。  
  
## 語法  
  
```  
class CTimeSpan  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CTimeSpan::CTimeSpan](../Topic/CTimeSpan::CTimeSpan.md)|建構 `CTimeSpan` 物件以各種方式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTimeSpan::Format](../Topic/CTimeSpan::Format.md)|轉換 `CTimeSpan` 至格式化字串。|  
|[CTimeSpan::GetDays](../Topic/CTimeSpan::GetDays.md)|傳回代表完整天數在這 `CTimeSpan`的值。|  
|[CTimeSpan::GetHours](../Topic/CTimeSpan::GetHours.md)|傳回目前日期表示時數的值 \(– 23 到 23\)。|  
|[CTimeSpan::GetMinutes](../Topic/CTimeSpan::GetMinutes.md)|傳回在目前的小時內表示分鐘數的值 \(– 59 到 59\)。|  
|[CTimeSpan::GetSeconds](../Topic/CTimeSpan::GetSeconds.md)|傳回目前分鐘內表示秒數的值 \(– 59 到 59\)。|  
|[CTimeSpan::GetTimeSpan](../Topic/CTimeSpan::GetTimeSpan.md)|傳回 `CTimeSpan` 物件的值|  
|[CTimeSpan::GetTotalHours](../Topic/CTimeSpan::GetTotalHours.md)|傳回代表完整時數總數這 `CTimeSpan`的值。|  
|[CTimeSpan::GetTotalMinutes](../Topic/CTimeSpan::GetTotalMinutes.md)|傳回代表完整分鐘總數這 `CTimeSpan`的值。|  
|[CTimeSpan::GetTotalSeconds](../Topic/CTimeSpan::GetTotalSeconds.md)|傳回代表完整的總秒數。在這個 `CTimeSpan`的值。|  
|[CTimeSpan::Serialize64](../Topic/CTimeSpan::Serialize64.md)|將資料還原序列化至檔案。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 \+ –](../Topic/CTimeSpan::operator%20+,%20-.md)|增加和減少 `CTimeSpan` 物件。|  
|[\+\=運算子 \(\=](../Topic/CTimeSpan::operator%20+=,%20-=.md)|從這個 `CTimeSpan`增加和減少 `CTimeSpan` 物件。|  
|[運算子\=\= \<等等\_.](../Topic/CTimeSpan%20Comparison%20Operators.md)|比較兩個相對時間值。|  
  
## 備註  
 `CTimeSpan` 不具有基底類別。  
  
 `CTimeSpan` 函式轉換為秒數天、小時、分鐘和秒數的各種組合。  
  
 `CTimeSpan` 物件在 **\_\_time64\_t** 結構中，則為 8 個位元組。  
  
 附屬類別， [CTime](../../atl-mfc-shared/reference/ctime-class.md)，表示絕對時間。  
  
 `CTime` 和 `CTimeSpan` 類別 \(Class\) 不可用於衍生設計。  由於具有虛擬函式 \(Virtual Function\)，兩個 `CTime` 和 `CTimeSpan` 物件大小正好是 8 個位元組。  大部分成員函式內嵌。  
  
 如需使用 `CTimeSpan`的資訊，請參閱《執行 *階段程式庫參考的*文件 [日期及時間](../../atl-mfc-shared/date-and-time.md)和 [時刻表](../../c-runtime-library/time-management.md) 。  
  
## 需求  
 **Header:** atltime.h  
  
## 請參閱  
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [\_ftime、\_ftime32、\_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime，\_localtime32，\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)
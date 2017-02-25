---
title: "CTime Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CTime"
  - "CTime"
  - "ATL::CTime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTime class"
  - "shared classes, CTime"
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CTime Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示絕對日期和時間。  
  
## 語法  
  
```  
class CTime  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CTime::CTime](../Topic/CTime::CTime.md)|建構 `CTime` 物件以各種方式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTime::Format](../Topic/CTime::Format.md)|轉換 `CTime` 物件中根據本地時區 \(的格式化字串。|  
|[CTime::FormatGmt](../Topic/CTime::FormatGmt.md)|轉換 `CTime` 物件中根據 UTC —的格式化字串。|  
|[CTime::GetAsDBTIMESTAMP](../Topic/CTime::GetAsDBTIMESTAMP.md)|轉換為相容的 <xref:System.Data.OleDb.OleDbType> Win32 結構的 `CTime` 物件儲存的時間資訊。|  
|[CTime::GetAsSystemTime](../Topic/CTime::GetAsSystemTime.md)|轉換為相容的 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) Win32 結構的 `CTime` 物件儲存的時間資訊。|  
|[CTime::GetCurrentTime](../Topic/CTime::GetCurrentTime.md)|建立表示目前時間的 `CTime` 物件 \(靜態成員函式\)。|  
|[CTime::GetDay](../Topic/CTime::GetDay.md)|傳回日期 `CTime` 由物件表示。|  
|[CTime::GetDayOfWeek](../Topic/CTime::GetDayOfWeek.md)|傳回 `CTime` 物件所表示的星期幾。|  
|[CTime::GetGmtTm](../Topic/CTime::GetGmtTm.md)|提供基礎 UTC —的元件分割 `CTime` 物件。|  
|[CTime::GetHour](../Topic/CTime::GetHour.md)|傳回 `CTime` 物件所代表的小時。|  
|[CTime::GetLocalTm](../Topic/CTime::GetLocalTm.md)|會根據本地時區的元件—分割 `CTime` 物件。|  
|[CTime::GetMinute](../Topic/CTime::GetMinute.md)|傳回 `CTime` 物件表示分鐘。|  
|[CTime::GetMonth](../Topic/CTime::GetMonth.md)|傳回 `CTime` 物件所表示的月份。|  
|[CTime::GetSecond](../Topic/CTime::GetSecond.md)|傳回 `CTime` 物件所表示的第二個。|  
|[CTime::GetTime](../Topic/CTime::GetTime.md)|傳回指定之物件的 `CTime`**\_\_time64\_t** 值。|  
|[CTime::GetYear](../Topic/CTime::GetYear.md)|傳回 `CTime` 物件所表示的年份。|  
|[CTime::Serialize64](../Topic/CTime::Serialize64.md)|將資料還原序列化至檔案。|  
  
### 運算子  
  
|||  
|-|-|  
|[運算子 \+ –](../Topic/CTime::operator%20+,%20-.md)|這些運算子增加和減少 `CTimeSpan` 和 `CTime` 物件。|  
|[\+\=運算子， – \=](../Topic/CTime::operator%20+=,%20-=.md)|這些運算子於這個物件 `CTime` 增加和減少 `CTimeSpan` 物件。|  
|[\=運算子](../Topic/CTime::operator%20=.md)|指派運算子。|  
|[運算子\=\=， \<等等\_.](../Topic/CTime%20Comparison%20Operators.md)|比較運算子。|  
  
## 備註  
 `CTime` 不具有基底類別。  
  
 `CTime` 值是以 Coordinated Universal Time \(UTC\)，以國際標準時間 \(Greenwich Mean Time， GMT\)。  請參閱 [時間管理](../../c-runtime-library/time-management.md) 關於時區的資訊決定。  
  
 當您建立 `CTime` 物件時，請設定 `nDST` 參數設定為 0 表示標準時間實際上是，或設定為大於的值 0 表示日光節約時間為作用中，或者為值低於零 C 執行階段程式庫程式碼估計標準時間或日光節約時間是否在作用中。  `tm_isdst` 為必要欄位。  如果未設定，則它的值未定義，並從 [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) 的傳回值無法預期。  如果對先前呼叫方法所傳回的 tm 結構的 `timeptr` 指向 [asctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)、 [\_gmtime\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)或 [localtime\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)， `tm_isdst` 欄位包含無效的值。  
  
 附屬類別， [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)，表示時間間隔。  
  
 `CTime` 和 `CTimeSpan` 類別 \(Class\) 不可用於衍生設計。  由於沒有虛擬函式， `CTime` 和 `CTimeSpan` 物件大小正好是 8 個位元組。  大部分成員函式內嵌。  
  
> [!NOTE]
>  表示資料限制為 12\/31\/3000。  這個下限是 1\/1\/1970 12:00: 00 AM GMT。  
  
 如需使用 `CTime`的資訊，請參閱《執行階段程式庫參考的文件 [日期及時間](../../atl-mfc-shared/date-and-time.md)和 [時刻表](../../c-runtime-library/time-management.md) 。  
  
> [!NOTE]
>  從 MFC 變更的 `CTime` 結構 MFC 7.1 至 8.0。  如果您要還原序列化 `CTime` 結構使用 `operator _<_<` 在 MFC 8.0 \(含\) 以後版本中，產生的檔案將無法讀取在 MFC 較舊的版本。  
  
## 需求  
 **標題:** atltime.h  
  
## 請參閱  
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [\_ftime\_s、\_ftime32\_s、\_ftime64\_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s、\_localtime32\_s、\_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [CTimeSpan Class](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)
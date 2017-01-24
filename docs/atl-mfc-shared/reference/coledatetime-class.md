---
title: "COleDateTime Class | Microsoft Docs"
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
  - "COleDateTime"
  - "ATL.COleDateTime"
  - "ATL::COleDateTime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDateTime class"
  - "Date 資料型別, MFC encapsulation of"
  - "日期, handling in MFC"
  - "shared classes, COleDateTime"
  - "時間, handling in MFC"
  - "time-only values"
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
caps.latest.revision: 34
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDateTime Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝用來 OLE Automation 的 `DATE` 資料型別。  
  
## 語法  
  
```  
class COleDateTime  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleDateTime::COleDateTime](../Topic/COleDateTime::COleDateTime.md)|建構 `COleDateTime` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDateTime::Format](../Topic/COleDateTime::Format.md)|產生 `COleDateTime` 物件中的格式化字串表示。|  
|[COleDateTime::GetAsDBTIMESTAMP](../Topic/COleDateTime::GetAsDBTIMESTAMP.md)|呼叫這個方法會取得 `COleDateTime` 物件的時間做為 **DBTIMESTAMP** 資料結構。|  
|[COleDateTime::GetAsSystemTime](../Topic/COleDateTime::GetAsSystemTime.md)|呼叫這個方法會取得 `COleDateTime` 物件的時間做為 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) 資料結構。|  
|[COleDateTime::GetAsUDATE](../Topic/COleDateTime::GetAsUDATE.md)|呼叫這個方法會取得 `COleDateTime` 的時間做為 **UDATE** 資料結構。|  
|[COleDateTime::GetCurrentTime](../Topic/COleDateTime::GetCurrentTime.md)|建立表示目前時間的 `COleDateTime` 物件 \(靜態成員函式\)。|  
|[COleDateTime::GetDay](../Topic/COleDateTime::GetDay.md)|傳回這 `COleDateTime` 物件所代表的日期也–範圍\)。|  
|[COleDateTime::GetDayOfWeek](../Topic/COleDateTime::GetDayOfWeek.md)|傳回這 `COleDateTime` 物件所表示的星期幾 \(星期日\) 的\)。|  
|[COleDateTime::GetDayOfYear](../Topic/COleDateTime::GetDayOfYear.md)|傳回這 `COleDateTime` 物件表示中年份的日期 \(一月一日\) 的\)。|  
|[COleDateTime::GetHour](../Topic/COleDateTime::GetHour.md)|傳回這 `COleDateTime` 物件代表的小時 \(0\) – "\)。|  
|[COleDateTime::GetMinute](../Topic/COleDateTime::GetMinute.md)|傳回這 `COleDateTime` 物件表示分鐘 \(0\) – 59\)。|  
|[COleDateTime::GetMonth](../Topic/COleDateTime::GetMonth.md)|傳回這 `COleDateTime` 物件所表示月份也– \(\)。|  
|[COleDateTime::GetSecond](../Topic/COleDateTime::GetSecond.md)|傳回第二個物件代表這 `COleDateTime` \(0\) – 59\)。|  
|[COleDateTime::GetStatus](../Topic/COleDateTime::GetStatus.md)|取得狀況 \(驗證\) 這 `COleDateTime` 物件。|  
|[COleDateTime::GetYear](../Topic/COleDateTime::GetYear.md)|傳回這 `COleDateTime` 物件表示的年份。|  
|[COleDateTime::ParseDateTime](../Topic/COleDateTime::ParseDateTime.md)|讀取字串中的日期\/時間值並將 `COleDateTime`的值。|  
|[COleDateTime::SetDate](../Topic/COleDateTime::SetDate.md)|設定這 `COleDateTime` 物件中的值設定為指定的日期值的。|  
|[COleDateTime::SetDateTime](../Topic/COleDateTime::SetDateTime.md)|設定這 `COleDateTime` 物件中的值設定為指定的日期\/時間值的。|  
|[COleDateTime::SetStatus](../Topic/COleDateTime::SetStatus.md)|設定狀況 \(驗證\) 這 `COleDateTime` 物件。|  
|[COleDateTime::SetTime](../Topic/COleDateTime::SetTime.md)|設定這 `COleDateTime` 物件中的值設定為指定的時間值。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[COleDateTime::operator \=\=、COleDateTime::operator \<等等.](../Topic/COleDateTime%20Relational%20Operators.md)|比較兩 `COleDateTime` 值。|  
|[COleDateTime::operator \+， COleDateTime::operator \-](../Topic/COleDateTime::operator%20+,%20-.md)|加減 `COleDateTime` 值。|  
|[COleDateTime::operator \+\=， COleDateTime::operator \- \=](../Topic/COleDateTime::operator%20+=,%20-=.md)|從這個物件 `COleDateTime` 加減 `COleDateTime` 值。|  
|[COleDateTime::operator \=](../Topic/COleDateTime::operator%20=.md)|複製 `COleDateTime` 值。|  
|[COleDateTime::operator 日期， COleDateTime::operator Date\*](../Topic/COleDateTime::operator%20DATE.md)|轉換 `COleDateTime` 值至 `DATE` 或 `DATE*`。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleDateTime::m\_dt](../Topic/COleDateTime::m_dt.md)|包含這 `COleDateTime` 物件的基礎 **日期** 。|  
|[COleDateTime::m\_status](../Topic/COleDateTime::m_status.md)|包含這 `COleDateTime` 物件的狀態。|  
  
## 備註  
 `COleDateTime` 沒有基底類別。  
  
 它是其中一個 OLE Automation 的 [Variant](http://msdn.microsoft.com/zh-tw/e305240e-9e11-4006-98cc-26f4932d2118) 資料型別的可能類型。  `COleDateTime` 值表示絕對日期和時間值。  
  
 `DATE` 型別會實作為浮點值。  天數而從年 12 月將日測量，午夜。  下表顯示一些日期及其關聯的值:  
  
|日期|值|  
|--------|-------|  
|而年 12 月多日午夜，|\-1.0|  
|而年 12 月多日上午\)，|\-1.25|  
|而年 12 月將日午夜，|0.0|  
|而年 12 月有日午夜，|1.0|  
|年年一月一日上午、點，..|2.25|  
  
> [!CAUTION]
>  請注意在中的資料表中，雖然日值變成負數在而年 12 月將日的午夜前，時間值不。  例如， 6:00 上午由分數值為 0.5，0.25 永遠表示不論表示日期是否為正數 \(而 12 月將日以後\) 或負 \(而 12 月將日之前\)。  這表示簡單的浮點比較一個代表的 7:00 AM 會錯誤地排序表示 12\/29\/1899 的 `COleDateTime` 6:00 上午，因為 **later** 同一天。  
  
 `COleDateTime` 類別控制代碼會傳遞到十二月月份日期為一月一日，，，到。  `COleDateTime` 類別使用西曆;它不支援凱撒曆日期。  `COleDateTime` 忽略日光節約時間。  \(請參閱\) [日期和時間:Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
> [!NOTE]
>  您可以使用 `%y` 格式擷取以及一個雙位元組只年 1 月開始年份的日期。  如果您在年 1 月目前使用中的 `%y` 日期格式，程式碼會產生判斷提示失敗。  
  
 這個型別也用來表示日期或時間值。  依照慣例，這個日期為 \(而 12 月將日\) 使用在時間值和時間 00:00 \(午夜\) 視為日期值使用。  
  
 如果您建立 `COleDateTime` 物件使用日期小於等於，則日期會接受，但是 `GetYear`，對的後續呼叫， `GetMonth`、 `GetDay`、 `GetHour`、 `GetMinute`和 `GetSecond` 失敗並傳回為。  在過去，您可以使用兩位數的日期，日期，但一定是以或大在 MFC 4.2 \(含\) 以後版本。  
  
 若要避免發生問題，請指定一個四位數的日期。  例如：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/CPP/coledatetime-class_1.cpp)]  
  
 `COleDateTime` 值的基本算術運算使用附屬類別 [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)。  `COleDateTimeSpan` 值會定義時間間隔。  這些類別之間的關係類似於 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 和 [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)。  
  
 如需 `COleDateTime` 和 `COleDateTimeSpan` 類別的詳細資訊，請參閱本文 [日期和時間:Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
## 需求  
 **標題:** ATLComTime.h  
  
## 請參閱  
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CTime Class](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan Class](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)
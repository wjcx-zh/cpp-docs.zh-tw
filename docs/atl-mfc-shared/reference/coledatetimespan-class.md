---
title: "COleDateTimeSpan Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.COleDateTimeSpan"
  - "COleDateTimeSpan"
  - "ATL::COleDateTimeSpan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDateTimeSpan class"
  - "Date 資料型別, MFC encapsulation of"
  - "shared classes, COleDateTimeSpan"
  - "time span"
  - "timespan"
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# COleDateTimeSpan Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示相對於時間，時間。  
  
## 語法  
  
```  
class COleDateTimeSpan  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleDateTimeSpan::COleDateTimeSpan](../Topic/COleDateTimeSpan::COleDateTimeSpan.md)|建構 `COleDateTimeSpan` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDateTimeSpan::Format](../Topic/COleDateTimeSpan::Format.md)|產生 `COleDateTimeSpan` 物件中的格式化字串表示。|  
|[COleDateTimeSpan::GetDays](../Topic/COleDateTimeSpan::GetDays.md)|傳回這個物件表示 `COleDateTimeSpan` 延伸的日期部分。|  
|[COleDateTimeSpan::GetHours](../Topic/COleDateTimeSpan::GetHours.md)|傳回這個物件表示 `COleDateTimeSpan` 延伸的小時部分。|  
|[COleDateTimeSpan::GetMinutes](../Topic/COleDateTimeSpan::GetMinutes.md)|傳回這個物件表示 `COleDateTimeSpan` 延伸的分鐘部分。|  
|[COleDateTimeSpan::GetSeconds](../Topic/COleDateTimeSpan::GetSeconds.md)|傳回這個物件表示 `COleDateTimeSpan` 延伸的第二個部分。|  
|[COleDateTimeSpan::GetStatus](../Topic/COleDateTimeSpan::GetStatus.md)|取得狀態 \(驗證\) 這 `COleDateTimeSpan` 物件。|  
|[COleDateTimeSpan::GetTotalDays](../Topic/COleDateTimeSpan::GetTotalDays.md)|傳回這 `COleDateTimeSpan` 物件所表示的日數。|  
|[COleDateTimeSpan::GetTotalHours](../Topic/COleDateTimeSpan::GetTotalHours.md)|傳回這 `COleDateTimeSpan` 物件所表示的工作時數。|  
|[COleDateTimeSpan::GetTotalMinutes](../Topic/COleDateTimeSpan::GetTotalMinutes.md)|傳回這 `COleDateTimeSpan` 物件所表示的分鐘數。|  
|[COleDateTimeSpan::GetTotalSeconds](../Topic/COleDateTimeSpan::GetTotalSeconds.md)|傳回這 `COleDateTimeSpan` 物件表示秒數。|  
|[COleDateTimeSpan::SetDateTimeSpan](../Topic/COleDateTimeSpan::SetDateTimeSpan.md)|設定這 `COleDateTimeSpan` 物件值的深層複本。|  
|[COleDateTimeSpan::SetStatus](../Topic/COleDateTimeSpan::SetStatus.md)|設定狀態 \(驗證\) 這 `COleDateTimeSpan` 物件。|  
  
### 公用運算子  
  
|||  
|-|-|  
|[運算子 \+ \-，](../Topic/COleDateTimeSpan::operator%20+,%20-.md)|加入，減去，並變更 `COleDateTimeSpan` 值的正負號。|  
|[\+\=運算子， \- \=](../Topic/COleDateTimeSpan::operator%20+=,%20-=.md)|從這個 `COleDateTimeSpan` 值增加和減少 `COleDateTimeSpan` 值。|  
|[\=運算子](../Topic/COleDateTimeSpan::operator%20=.md)|複製 `COleDateTimeSpan` 值。|  
|[運算子\=\=， \<， \<\=](../Topic/COleDateTimeSpan%20Relational%20Operators.md)|比較兩個 `COleDateTimeSpan` 值。|  
|[運算子兩](../Topic/COleDateTimeSpan::operator%20double.md)|轉換這 `COleDateTimeSpan` 值組 **double**。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleDateTimeSpan::m\_span](../Topic/COleDateTimeSpan::m_span.md)|包含這個 `COleDateTimeSpan` 物件的基礎 **double** 。|  
|[COleDateTimeSpan::m\_status](../Topic/COleDateTimeSpan::m_status.md)|包含這個 `COleDateTimeSpan` 物件的狀態。|  
  
## 備註  
 `COleDateTimeSpan` 不具有基底類別。  
  
 `COleDateTimeSpan` 天數保留時間。  
  
 `COleDateTimeSpan` 搭配其附屬類別 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)。  `COleDateTime` 封裝 OLE Automation **DATE** 資料型別。  `COleDateTime` 表示絕對時間值。  所有 `COleDateTime` 計算會涉及 `COleDateTimeSpan` 值。  在這兩個類別之間的關聯性 \(Relationship\) 類似於 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 和 [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)。  
  
 如需 `COleDateTime` 和 `COleDateTimeSpan` 類別的詳細資訊，請參閱本文 [日期和時間:Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
## 需求  
 **Header:** ATLComTime.h  
  
## 請參閱  
 [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md)   
 [CTime Class](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan Class](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)
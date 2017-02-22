---
title: "CFileTime Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CFileTime"
  - "CFileTime"
  - "ATL.CFileTime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileTime class"
  - "shared classes, CFileTime"
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CFileTime Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供管理日期和時間值的方法與檔案。  
  
## 語法  
  
```  
  
   class CFileTime :   
public FILETIME  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFileTime::CFileTime](../Topic/CFileTime::CFileTime.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFileTime::GetCurrentTime](../Topic/CFileTime::GetCurrentTime.md)|呼叫這個靜態函式擷取表示目前的系統日期和時間的 `CFileTime` 物件。|  
|[CFileTime::GetTime](../Topic/CFileTime::GetTime.md)|呼叫這個方法會從物件擷取 `CFileTime` 時間。|  
|[CFileTime::LocalToUTC](../Topic/CFileTime::LocalToUTC.md)|呼叫這個方法會將本機檔案時間與 Coordinated Universal Time 的檔案時間 \(UTC\)。|  
|[CFileTime::SetTime](../Topic/CFileTime::SetTime.md)|呼叫這個方法會設定物件 `CFileTime` 日期和時間中的。|  
|[CFileTime::UTCToLocal](../Topic/CFileTime::UTCToLocal.md)|呼叫這個方法會將 Coordinated Universal Time \(UTC\) 的時間為本機檔案的時間。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CFileTime::operator \-](../Topic/CFileTime::operator%20-.md)|這個運算子來執行 `CFileTime` 或 `CFileTimeSpan` 物件的減法運算。|  
|[CFileTime::operator \!\=](../Topic/CFileTime::operator%20!=.md)|這個運算子來比較是否不相等的兩個 `CFileTime` 物件。|  
|[CFileTime::operator \+](../Topic/CFileTime::operator%20+.md)|這個運算子是用來在 `CFileTimeSpan` 物件加入。|  
|[CFileTime::operator \+\=](../Topic/CFileTime::operator%20+=.md)|這個運算子是用來在 `CFileTimeSpan` 物件加入並將結果指派給目前物件。|  
|[CFileTime::operator \<](../Topic/CFileTime::operator%20%3C.md)|這個運算子比較兩個物件 `CFileTime` 判斷較少。|  
|[CFileTime::operator \<\=](../Topic/CFileTime::operator%20%3C=.md)|這個運算子比較兩個物件 `CFileTime` 判斷相等或較少。|  
|[CFileTime::operator \=](../Topic/CFileTime::operator%20=.md)|指派運算子。|  
|[CFileTime::operator \-\=](../Topic/CFileTime::operator%20-=.md)|這個運算子來執行 `CFileTimeSpan` 物件值的減法並將結果指派給目前物件。|  
|[CFileTime::operator \=\=](../Topic/CFileTime::operator%20==.md)|這個運算子比較兩個 `CFileTime` 物件。|  
|[CFileTime::operator \>](../Topic/CFileTime::operator%20%3E.md)|這個運算子比較兩個物件 `CFileTime` 決定上限。|  
|[CFileTime::operator \>\=](../Topic/CFileTime::operator%20%3E=.md)|這個運算子比較兩個物件 `CFileTime` 判斷相等或較大。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[CFileTime::Day](../Topic/CFileTime::Day.md)|儲存的 100 奈秒間隔數組成一天靜態資料成員。|  
|[CFileTime::Hour](../Topic/CFileTime::Hour.md)|儲存的 100 奈秒間隔數組成一小時靜態資料成員。|  
|[CFileTime::Millisecond](../Topic/CFileTime::Millisecond.md)|儲存的 100 奈秒間隔數組成毫秒靜態資料成員。|  
|[CFileTime::Minute](../Topic/CFileTime::Minute.md)|儲存的 100 奈秒間隔數組成一分鐘靜態資料成員。|  
|[CFileTime::Second](../Topic/CFileTime::Second.md)|儲存的 100 奈秒間隔數組成一秒靜態資料成員。|  
|[CFileTime::Week](../Topic/CFileTime::Week.md)|儲存的 100 奈秒間隔數組成一週靜態資料成員。|  
  
## 備註  
 這個類別會提供管理日期和時間值的方法與檔案建立、存取和修改。  這個類別的方法和資料與物件搭配 `CFileTimeSpan` 經常使用，以處理相對時間值。  
  
 日期和時間值會儲存為 100 奈秒間隔數個 64 位元的值從 1601 年 1 月 1 日。  這是 Coordinated Universal Time \(UTC\) 格式。  
  
 提供下列靜態 const 成員變數簡化計算:  
  
|成員變數|100 奈秒間隔數。|  
|----------|----------------|  
|Millisecond|10,000|  
|秒|\* 1,000 毫秒|  
|分|接著\* 60|  
|時|分鐘\* 60|  
|天|\* 24 小時|  
|週|\* 7 天。|  
  
 **Note** 並非所有的檔案系統可以記錄檔建立和上次存取時間和不是所有的檔案系統類似記錄它們。  例如，在 Windows NT FAT 檔案系統，建立時間為 10 毫秒的解析度，寫入時間為 2 秒的解析度，，和存取時間有 1 天 \(存取日期\) 的解析度。  NTFS，存取時間為 1 小時的解析度。  此外，在磁碟上的 FAT 記錄時間在磁碟的本地時間，不過， NTFS 記錄的時間在 UTC。  如需詳細資訊，請參閱 [檔案時間](http://msdn.microsoft.com/library/windows/desktop/ms724290)。  
  
## 繼承階層架構  
 `FILETIME`  
  
 `CFileTime`  
  
## 需求  
 **Header:** atltime.h  
  
## 請參閱  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [CFileTimeSpan Class](../../atl-mfc-shared/reference/cfiletimespan-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)
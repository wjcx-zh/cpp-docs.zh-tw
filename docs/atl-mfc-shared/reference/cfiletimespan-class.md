---
title: "CFileTimeSpan Class | Microsoft Docs"
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
  - "CFileTimeSpan"
  - "ATL.CFileTimeSpan"
  - "ATL::CFileTimeSpan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileTimeSpan class"
  - "shared classes, CFileTimeSpan"
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
caps.latest.revision: 18
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFileTimeSpan Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供管理相關的日期和時間值的方法與檔案。  
  
## 語法  
  
```  
  
class CFileTimeSpan  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFileTimeSpan::CFileTimeSpan](../Topic/CFileTimeSpan::CFileTimeSpan.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFileTimeSpan::GetTimeSpan](../Topic/CFileTimeSpan::GetTimeSpan.md)|呼叫這個方法會從物件擷取 `CFileTimeSpan` 時間。|  
|[CFileTimeSpan::SetTimeSpan](../Topic/CFileTimeSpan::SetTimeSpan.md)|呼叫這個方法會設定 `CFileTimeSpan` 物件的時間。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CFileTimeSpan::operator \-](../Topic/CFileTimeSpan::operator%20-.md)|執行 `CFileTimeSpan` 物件的減法運算。|  
|[CFileTimeSpan::operator \!\=](../Topic/CFileTimeSpan::operator%20!=.md)|比較兩個 `CFileTimeSpan` 物件是否不相等。|  
|[CFileTimeSpan::operator \+](../Topic/CFileTimeSpan::operator%20+.md)|執行 `CFileTimeSpan` 物件加入。|  
|[CFileTimeSpan::operator \+\=](../Topic/CFileTimeSpan::operator%20+=.md)|執行 `CFileTimeSpan` 物件加入並將結果指派給目前物件。|  
|[CFileTimeSpan::operator \<](../Topic/CFileTimeSpan::operator%20%3C.md)|比較兩個物件 `CFileTimeSpan` 判斷較少。|  
|[CFileTimeSpan::operator \<\=](../Topic/CFileTimeSpan::operator%20%3C=.md)|比較兩個物件 `CFileTimeSpan` 判斷相等或較少。|  
|[CFileTimeSpan::operator \=](../Topic/CFileTimeSpan::operator%20=.md)|指派運算子。|  
|[CFileTimeSpan::operator \-\=](../Topic/CFileTimeSpan::operator%20-=.md)|執行 `CFileTimeSpan` 物件值的減法並將結果指派給目前物件。|  
|[CFileTimeSpan::operator \=\=](../Topic/CFileTimeSpan::operator%20==.md)|比較兩個 `CFileTimeSpan` 物件是否相等。|  
|[CFileTimeSpan::operator \>](../Topic/CFileTimeSpan::operator%20%3E.md)|比較兩個物件 `CFileTimeSpan` 決定上限。|  
|[CFileTimeSpan::operator \>\=](../Topic/CFileTimeSpan::operator%20%3E=.md)|比較兩個物件 `CFileTimeSpan` 判斷相等或較大。|  
  
## 備註  
 這個類別會提供管理常會遇到的相對網頁提供方法，在執行作業有關時，在建立，最後存取或上次修改。  這個類別的方法與物件搭配 [CFileTime 類別](../../atl-mfc-shared/reference/cfiletime-class.md) 經常使用。  
  
## 範例  
 [CFileTime::Millisecond](../Topic/CFileTime::Millisecond.md)。請參閱範例。  
  
## 需求  
 **Header:** atltime.h  
  
## 請參閱  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [CFileTime Class](../../atl-mfc-shared/reference/cfiletime-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)
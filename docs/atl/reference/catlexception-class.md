---
title: "CAtlException Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAtlException"
  - "ATL::CAtlException"
  - "ATL.CAtlException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlException class"
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CAtlException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會定義一個 ATL 例外狀況。  
  
## 語法  
  
```  
  
class CAtlException  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlException::CAtlException](../Topic/CAtlException::CAtlException.md)|建構函式。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAtlException::operator HRESULT](../Topic/CAtlException::operator%20HRESULT.md)|要轉型為的 HRESULT 值的目前物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAtlException::m\_hr](../Topic/CAtlException::m_hr.md)|已轉換的建立的物件和所使用的變數型別儲存錯誤條件。|  
  
## 備註  
 `CAtlException` 物件代表例外狀況與 ATL 作業相關。  `CAtlException` 類別包括儲存值例外狀況和轉型運算子的狀態碼原因可讓您將例外狀況中的公用資料成員，視其 HRESULT。  
  
 一般而言，您會 `AtlThrow` 而不是直接建立 `CAtlException` 物件。  
  
## 需求  
 **Header:** atlexcept.h  
  
## 請參閱  
 [AtlThrow](../Topic/AtlThrow.md)   
 [Class Overview](../../atl/atl-class-overview.md)
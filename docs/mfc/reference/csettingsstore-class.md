---
title: "CSettingsStore Class | Microsoft Docs"
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
  - "CSettingsStore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSettingsStore class"
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
caps.latest.revision: 29
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSettingsStore Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包裝 Windows API 函式，提供用來存取登錄的物件導向介面。  
  
## 語法  
  
```  
class CSettingsStore : public CObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSettingsStore::CSettingsStore](../Topic/CSettingsStore::CSettingsStore.md)|建構 `CSettingsStore` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSettingsStore::Close](../Topic/CSettingsStore::Close.md)|關閉開啟登錄機碼。|  
|[CSettingsStore::CreateKey](../Topic/CSettingsStore::CreateKey.md)|如果不存在，開啟指定的機碼或建立它。|  
|[CSettingsStore::DeleteKey](../Topic/CSettingsStore::DeleteKey.md)|刪除指定的金鑰和其所有的子節點。|  
|[CSettingsStore::DeleteValue](../Topic/CSettingsStore::DeleteValue.md)|刪除開啟機碼的值。|  
|[CSettingsStore::Open](../Topic/CSettingsStore::Open.md)|開啟指定的索引鍵。|  
|[CSettingsStore::Read](../Topic/CSettingsStore::Read.md)|擷取針對指定的機碼值。|  
|[CSettingsStore::Write](../Topic/CSettingsStore::Write.md)|寫入登錄值在開啟機碼下方。|  
  
## 備註  
 成員函式 `CreateKey` 和 `Open` 非常相似。  如果登錄機碼已經存在， `CreateKey` 和相同的方式 `Open` 函式。  不過，在中，如果登錄機碼不存在， `CreateKey` 會建立它，而 `Open` 會傳回錯誤值。  
  
## 範例  
 下列範例示範如何使用開啟，然後讀取 `CSettingsStore` 方法的方法。  這個程式碼片段是 [工具提示示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/CPP/csettingsstore-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSettingsStore](../../mfc/reference/csettingsstore-class.md)  
  
## 需求  
 **標題:** afxsettingsstore.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)
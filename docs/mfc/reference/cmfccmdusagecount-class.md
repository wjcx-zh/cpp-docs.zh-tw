---
title: "CMFCCmdUsageCount Class | Microsoft Docs"
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
  - "CMFCCmdUsageCount"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCCmdUsageCount class"
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCCmdUsageCount Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當使用者選取項目從  功能表時，追蹤使用計數 Windows 訊息，例如。  
  
## 語法  
  
```  
class CMFCCmdUsageCount : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|預設建構函式。|  
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|解構函式。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCCmdUsageCount::AddCmd](../Topic/CMFCCmdUsageCount::AddCmd.md)|會將與給定的命令計數器。|  
|[CMFCCmdUsageCount::GetCount](../Topic/CMFCCmdUsageCount::GetCount.md)|擷取與所指定的命令 ID. 的使用計數|  
|[CMFCCmdUsageCount::HasEnoughInformation](../Topic/CMFCCmdUsageCount::HasEnoughInformation.md)|判斷這個物件是否收集最低量的追蹤資料。|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](../Topic/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd.md)|判斷是否經常使用給定的命令。|  
|[CMFCCmdUsageCount::Reset](../Topic/CMFCCmdUsageCount::Reset.md)|清除使用計數所有命令。|  
|[CMFCCmdUsageCount::Serialize](../Topic/CMFCCmdUsageCount::Serialize.md)|從檔案讀取或寫入的這個物件為檔案。  \(覆寫 [CObject::Serialize](../Topic/CObject::Serialize.md)\)。|  
|[CMFCCmdUsageCount::SetOptions](../Topic/CMFCCmdUsageCount::SetOptions.md)|設定共用的 `CMFCCmdUsageCount` 類別資料成員的值。|  
  
### 資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|`m_CmdUsage`|`CMap` 物件給它的對應命令計數。|  
|`m_nMinUsagePercentage`|命令的最小使用百分比可以經常使用。|  
|`m_nStartCount`|用來判斷的起始計數器這個物件是否收集最低量的追蹤資料。|  
|`m_nTotalUsage`|計算所有追蹤的命令。|  
  
### 備註  
 `CMFCCmdUsageCount` 類別對應每個數字視窗訊息識別項為 32 位元不帶正負號的整數計數器。  `CMFCToolBar` 使用這個類別會顯示最常用的工具列項目。  如需 `CMFCToolBar` 的詳細資訊，請參閱 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)。  
  
 您可以 `CMFCCmdUsageCount` 保存在程式執行之間類別資料。  使用 [CMFCCmdUsageCount::Serialize](../Topic/CMFCCmdUsageCount::Serialize.md) 方法序列化的類別成員資料和 [CMFCCmdUsageCount::SetOptions](../Topic/CMFCCmdUsageCount::SetOptions.md) 方法設定共用的成員資料。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## 需求  
 **標題:** afxcmdusagecount.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)
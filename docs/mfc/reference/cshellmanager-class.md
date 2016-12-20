---
title: "CShellManager Class | Microsoft Docs"
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
  - "CShellManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CShellManager class"
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CShellManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行可讓您以指標一起用來識別項清單的方法 \(PIDLs\)。  
  
## 語法  
  
```  
class CShellManager : public CObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CShellManager::CShellManager](../Topic/CShellManager::CShellManager.md)|建構 `CShellManager` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CShellManager::BrowseForFolder](../Topic/CShellManager::BrowseForFolder.md)|會顯示可讓使用者選取 Shell 資料夾的對話方塊。|  
|[CShellManager::ConcatenateItem](../Topic/CShellManager::ConcatenateItem.md)|串連兩個 PIDLs。|  
|[CShellManager::CopyItem](../Topic/CShellManager::CopyItem.md)|建立新的 PIDL 並複製所提供的 PIDL 給它。|  
|[CShellManager::CreateItem](../Topic/CShellManager::CreateItem.md)|建立指定大小的新 PIDL。|  
|[CShellManager::FreeItem](../Topic/CShellManager::FreeItem.md)|刪除提供的 PIDL。|  
|[CShellManager::GetItemCount](../Topic/CShellManager::GetItemCount.md)|傳回集合中的項目數目所提供的 PIDL 的。|  
|[CShellManager::GetItemSize](../Topic/CShellManager::GetItemSize.md)|傳回所提供的 PIDL 的大小。|  
|[CShellManager::GetNextItem](../Topic/CShellManager::GetNextItem.md)|傳回從 PIDL 的下一個項目。|  
|[CShellManager::GetParentItem](../Topic/CShellManager::GetParentItem.md)|擷取所提供之項目的父項目。|  
|[CShellManager::ItemFromPath](../Topic/CShellManager::ItemFromPath.md)|擷取所提供的路徑所識別項目的 PIDL。|  
  
## 備註  
 `CShellManager` 的方法將處理與 PIDLs 的所有分類。  PIDL 是 Shell 物件的唯一識別項。  
  
 您無法以手動方式建立 `CShellManager` 物件。  它將會由您的應用程式架構自動建立。  不過，您應該在您的應用程式中初始化程序呼叫 [CWinAppEx::InitShellManager](../Topic/CWinAppEx::InitShellManager.md) 。  若要取得指標應用程式的 Shell 處理常式中，呼叫 [CWinAppEx::GetShellManager](../Topic/CWinAppEx::GetShellManager.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CShellManager](../../mfc/reference/cshellmanager-class.md)  
  
## 需求  
 **標題:** afxshellmanager.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
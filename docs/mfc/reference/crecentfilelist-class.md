---
title: "CRecentFileList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRecentFileList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRecentFileList class"
  - "檔案 [C++], most recently used"
  - "MRU 檔案"
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CRecentFileList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援 \(MRU\) 最近使用的檔案清單的控制項。  
  
## 語法  
  
```  
class CRecentFileList  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CRecentFileList::CRecentFileList](../Topic/CRecentFileList::CRecentFileList.md)|建構 `CRecentFileList` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRecentFileList::Add](../Topic/CRecentFileList::Add.md)|將檔案加入至 MRU 檔案清單。|  
|[CRecentFileList::GetDisplayName](../Topic/CRecentFileList::GetDisplayName.md)|針對 MRU 檔案名稱的功能表會顯示提供的顯示名稱。|  
|[CRecentFileList::GetSize](../Topic/CRecentFileList::GetSize.md)|要擷取的檔案數目 MRU 檔案清單中的。|  
|[CRecentFileList::ReadList](../Topic/CRecentFileList::ReadList.md)|讀取 MRU 檔案清單從登錄或 .INI 檔。|  
|[CRecentFileList::Remove](../Topic/CRecentFileList::Remove.md)|從 MRU 檔案清單中刪除檔案。|  
|[CRecentFileList::UpdateMenu](../Topic/CRecentFileList::UpdateMenu.md)|更新 MRU 檔案清單的功能表會顯示。|  
|[CRecentFileList::WriteList](../Topic/CRecentFileList::WriteList.md)|撰寫 MRU 檔案清單從登錄或 .INI 檔。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CRecentFileList::operator](../Topic/CRecentFileList::operator.md)|傳回 `CString` 物件在指定的位置。|  
  
## 備註  
 檔案可能會從 MRU 檔案清單中刪除，檔案清單可以讀取或寫入登錄或 .INI 檔，，並顯示 MRU 檔案清單的功能表進行更新。  
  
 如需 MRU 功能表項目的詳細資訊，請參閱  
  
-   知識庫文件 Q243751:HOWTO:加入 MRU 功能表項目的命令處理常式在 MFC 應用程式  
  
## 繼承階層架構  
 `CRecentFileList`  
  
## 需求  
 **Header:** afxadv.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)
---
title: "DELETEITEMSTRUCT 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DELETEITEMSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DELETEITEMSTRUCT 結構"
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# DELETEITEMSTRUCT 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`DELETEITEMSTRUCT` 結構描述已刪除的主控描繪清單方塊或下拉式方塊項目。  
  
## 語法  
  
```  
  
      typedef struct tagDELETEITEMSTRUCT { /* ditms */  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    HWND hwndItem;  
    UINT itemData;  
} DELETEITEMSTRUCT;  
```  
  
#### 參數  
 `CtlType`  
 指定 **ODT\_LISTBOX** \(主控描繪清單方塊\) 或 **ODT\_COMBOBOX** \(繪製主控描繪下拉式方塊\)。  
  
 `CtlID`  
 指定清單方塊或下拉式方塊的識別項。  
  
 `itemID`  
 標示第二個項目的索引所移除的清單方塊或下拉式方塊中。  
  
 `hwndItem`  
 識別控制項。  
  
 `itemData`  
 指定應用程式定義的資料項目。  這個值傳遞到將項目加入清單方塊或下拉式方塊訊息的 **lParam** 參數的控制項。  
  
## 備註  
 當項目從清單方塊或下拉式方塊中移除或終結時，清單方塊或下拉式方塊， Windows 會將 `WM_DELETEITEM` 傳送訊息給每個已刪除項目的擁有者。  訊息的 **lParam** 參數包含指標的結構。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../Topic/CWnd::OnDeleteItem.md)
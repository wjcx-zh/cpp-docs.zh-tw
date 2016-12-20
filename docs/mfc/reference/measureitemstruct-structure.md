---
title: "MEASUREITEMSTRUCT 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MEASUREITEMSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MEASUREITEMSTRUCT 結構"
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MEASUREITEMSTRUCT 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`MEASUREITEMSTRUCT` 結構通知視窗主控描繪的控制項或功能表項目的大小。  
  
## 語法  
  
```  
  
      typedef struct tagMEASUREITEMSTRUCT {  
   UINT CtlType;  
   UINT CtlID;  
   UINT itemID;  
   UINT itemWidth;  
   UINT itemHeight;  
   DWORD itemData  
} MEASUREITEMSTRUCT;  
```  
  
#### 參數  
 `CtlType`  
 包含控制項型別。  控制項型別的值如下:  
  
-   **ODT\_COMBOBOX** 主控描繪下拉式方塊  
  
-   **ODT\_LISTBOX** 主控描繪清單方塊  
  
-   **ODT\_MENU** 主控描繪功能表  
  
 `CtlID`  
 包含下拉式方塊、清單方塊或按鈕的控制項 ID。  這個成員不會用於功能表。  
  
 `itemID`  
 包含功能表的功能表項目 ID 或可變高度下拉式方塊或清單方塊的清單方塊項目 ID。  這個成員不會使用固定高度的下拉式方塊或清單方塊，或者為按鈕。  
  
 *itemWidth*  
 指定功能表項目的寬度。  在從訊息之前，傳回主控描繪功能表項目的擁有者必須填入這個成員。  
  
 *itemHeight*  
 在清單方塊或功能表指定個別項目的高度。  在從訊息之前傳回，主控描繪下拉式方塊、清單方塊或功能表項目的擁有者必須填寫這個成員。  清單方塊中項目的最大高度為 255。  
  
 `itemData`  
 對於下拉式方塊或清單方塊，成員包含傳遞至清單方塊中下列其中一個值:  
  
-   [CComboBox::AddString](../Topic/CComboBox::AddString.md)  
  
-   [CComboBox::InsertString](../Topic/CComboBox::InsertString.md)  
  
-   [CListBox::AddString](../Topic/CListBox::AddString.md)  
  
-   [CListBox::InsertString](../Topic/CListBox::InsertString.md)  
  
 針對功能表，這個成員包含傳遞至功能表下列其中一個值:  
  
-   [CMenu::AppendMenu](../Topic/CMenu::AppendMenu.md)  
  
-   [CMenu::InsertMenu](../Topic/CMenu::InsertMenu.md)  
  
-   [CMenu::ModifyMenu](../Topic/CMenu::ModifyMenu.md)  
  
 這可讓視窗正確處理與控制項的使用者互動。  無法完成 `MEASUREITEMSTRUCT` 結構的適當成員會導致控制項不適當的作業。  
  
## 需求  
 **Header:** 中  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnMeasureItem](../Topic/CWnd::OnMeasureItem.md)
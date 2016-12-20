---
title: "COMPAREITEMSTRUCT 結構 | Microsoft Docs"
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
  - "COMPAREITEMSTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COMPAREITEMSTRUCT 結構"
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COMPAREITEMSTRUCT 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`COMPAREITEMSTRUCT` 結構提供識別項以及應用程式所提供的資料為兩個項目在排序，主控描繪清單方塊或下拉式方塊。  
  
## 語法  
  
```  
  
      typedef struct tagCOMPAREITEMSTRUCT {  
    UINT   CtlType;  
    UINT   CtlID;  
    HWND   hwndItem;  
    UINT   itemID1;  
    DWORD  itemData1;  
    UINT   itemID2;  
    DWORD  itemData2;  
} COMPAREITEMSTRUCT;  
```  
  
#### 參數  
 `CtlType`  
 \( 指定主控描繪清單方塊\) \(指定主控描繪下拉式方塊\) 的**ODT\_LISTBOX** 或 **ODT\_COMBOBOX** 。  
  
 `CtlID`  
 清單方塊或下拉式方塊的控制項 ID。  
  
 `hwndItem`  
 控制項的視窗控制代碼。  
  
 *itemID1*  
 第一個項目的索引所比較的清單方塊或下拉式方塊中。  
  
 *itemData1*  
 由應用程式所提供的資料進行比較的第一個項目。  這個值會將項目加入至下拉式方塊或清單方塊的呼叫傳遞。  
  
 *itemID2*  
 第二個項目的索引所比較的清單方塊或下拉式方塊中。  
  
 *itemData2*  
 由應用程式所提供的資料進行比較的第二個項目。  這個值會將項目加入至下拉式方塊或清單方塊的呼叫傳遞。  
  
## 備註  
 當應用程式將新項目加入至主控描繪清單方塊或下拉式方塊會以 **CBS\_SORT** 或 **LBS\_SORT** 樣式，視窗會指派擁有者 `WM_COMPAREITEM` 訊息。  訊息的 `lParam` 參數包含長指標轉換為 `COMPAREITEMSTRUCT` 結構。  在收到這個訊息後，擁有者比較兩個項目並傳回指出項目在其他進行排序。  
  
## 需求  
 **Header:** winuser.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../Topic/CWnd::OnCompareItem.md)
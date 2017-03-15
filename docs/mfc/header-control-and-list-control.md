---
title: "標題控制項和清單控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeaderCtrl 類別, 與 CListCtrl"
  - "CListCtrl 類別, 標題控制項"
  - "CListCtrl 類別, 與 CHeaderCtrl"
  - "控制項 [MFC], 標題"
  - "標題控制項"
  - "標題控制項, 一起使用的清單控制項"
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 標題控制項和清單控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在大部分情況下，您將使用內嵌在 [CListCtrl](../mfc/reference/clistctrl-class.md) 或 [CListView](../mfc/reference/clistview-class.md) 物件中的標題控制項。  然而，有些個別的標題控制項物件是適當的情況，例如操作資料，排列資料列或資料行，在 [CView](../mfc/reference/cview-class.md)衍生物件。  在這些情況下，您需要對外觀和預設內嵌標題控制項的行為更大的控制項。  
  
 要標題控制項提供標準，預設行為的一般情況下，您可以使用 [CListCtrl](../mfc/reference/clistctrl-class.md) 或 [CListView](../mfc/reference/clistview-class.md) 。  使用 `CListCtrl` ，當您想要內嵌在清單檢視通用控制項中預設標題控制項的功能時。  使用 [CListView](../mfc/reference/clistview-class.md) ，在您想要內嵌在檢視物件的預設標題控制項的功能時。  
  
> [!NOTE]
>  如果清單檢視控制項使用 `LVS_REPORT` 樣式建立，這些控制項只包含一個固定標題控制項。  
  
 在大部分情況下，內嵌標題控制項的外觀可藉由變更包含的清單檢視控制項修改。  此外，標題控制項的相關資訊可以透過父清單檢視控制項的成員函式取得。  不過，對於對內嵌標題控制項的屬性和樣式的完全控制和存取，建議取得標題控制項物件的指標。  
  
 由呼叫個別類別的 `GetHeaderCtrl` 成員函式，內嵌標題控制項物件可以從 **CListCtrl** 或 `CListView` 存取。  下列程式碼可說明此點：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/CPP/header-control-and-list-control_1.cpp)]  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [搭配使用影像清單與標題控制項](../mfc/using-image-lists-with-header-controls.md)  
  
## 請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)
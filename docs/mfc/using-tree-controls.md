---
title: "使用樹狀目錄控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl 類別, 使用"
  - "樹狀目錄控制項, 關於樹狀目錄控制項"
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用樹狀目錄控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樹狀目錄控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 的一般使用方式會遵循下列模式:  
  
-   會建立控制項。  如果控制項在對話方塊樣板指定或，如果您使用 `CTreeView`，建立是自動的，在這個對話方塊或檢視建立時。  如果您要建立樹狀目錄控制項初始化為子視窗的視窗中，使用 [建立](../Topic/CTreeCtrl::Create.md) 成員函式。  
  
-   如果您希望樹狀目錄控制項使用影像，藉由呼叫 [SetImageList](../Topic/CTreeCtrl::SetImageList.md)設定影像清單。  您可以藉由呼叫 [SetIndent](../Topic/CTreeCtrl::SetIndent.md)來變更縮排。  的好時機會在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) \(在對話方塊的控制項\) 或 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) \(檢視\)。  
  
-   將命令加入至資料控制項呼叫 `CTreeCtrl` [InsertItem](../Topic/CTreeCtrl::InsertItem.md) 為每個資料項目一次運作。  `InsertItem` 傳回的控制代碼。您可以使用中參考它的項目，例如，當加入子項目時。  的好時機初始化資料為 `OnInitDialog` \(在對話方塊的控制項\) 或 `OnInitialUpdate` \(檢視\)。  
  
-   因為使用者與控制項互動，它會傳送各種告知訊息。  您可以指定函式處理要處理將在控制項視窗的訊息對應的 **ON\_NOTIFY\_REFLECT** 巨集或將 `ON_NOTIFY` 巨集加入至父視窗的訊息對應的每個訊息。  為可能的通知清單後請參閱本主題稍後的 [樹狀目錄控制項通知訊息](../mfc/tree-control-notification-messages.md) 。  
  
-   呼叫各種成員函式對控制項的值。  變更可以設定縮排和變更文字、影像或資料包括與項目。  
  
-   使用各種 Get 函式檢查控制項的內容。  您也可以周遊樹狀目錄控制項的內容可讓您擷取控制代碼給父、指定之項目的子系和同層級的函式。  您甚至可以排序特定節點的子系。  
  
-   當您在使用控制項時，請確定正確地終止。  如果樹狀目錄控制項在對話方塊中，或者是檢視，將自動終結和 `CTreeCtrl` 物件。  否則，您必須確保適當地終結控制項和 `CTreeCtrl` 物件。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)
---
title: "建立 CToolBarCtrl 物件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CToolBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBarCtrl 類別, 建立工具列"
  - "工具列控制項 [MFC], 建立"
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 建立 CToolBarCtrl 物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 物件包含許多內部資料結構—按鈕影像的點陣圖清單，按鈕標籤字串清單和 `TBBUTTON` 結構清單—組合影像和字串與按鈕的位置、樣式、狀態和指令 ID。  每一種資料結構之項目歸為以零起始的索引參考。  在您可以使用 `CToolBarCtrl` 物件之前，您必須設定好這些資料結構。  如需資料結構的清單，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [工具列控制項](https://msdn.microsoft.com/en-us/library/47xcww9x.aspx) 。  字串清單只可以為按鈕標籤使用;您無法從工具列擷取字串。  
  
 若要使用 `CToolBarCtrl` 物件，您通常會執行下列步驟:  
  
### 使用 CToolBarCtrl 物件  
  
1.  建構 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 物件。  
  
2.  呼叫 [建立](../Topic/CToolBarCtrl::Create.md) 以建立視窗工具列通用控制項並將它附加至 `CToolBarCtrl` 物件。  如果您想要按鈕的點陣圖影像，請藉由呼叫 [AddBitmap](../Topic/CToolBarCtrl::AddBitmap.md) 將按鈕點陣圖加入工具列。  如果您想要按鈕為標籤字串，請藉由呼叫 [AddString](../Topic/CToolBarCtrl::AddString.md) 和 [AddStrings](../Topic/CToolBarCtrl::AddStrings.md) 將字串加入至工具列。  在呼叫 `AddString` 和\/或 `AddStrings`之後，您應該呼叫 [AutoSize](../Topic/CToolBarCtrl::AutoSize.md) 以讓字串出現。  
  
3.  藉由呼叫 [AddButtons](../Topic/CToolBarCtrl::AddButtons.md) 將按鈕結構加入工具列。  
  
4.  如果您想要工具提示，請處理在工具列的主控視窗的 **TTN\_NEEDTEXT** 訊息如 [處理工具提示通知](../mfc/handling-tool-tip-notifications.md)中所述。  
  
5.  如果您想要讓使用者自訂工具列，請處理在主控視窗的自訂通知訊息如 [處理自訂通知](../mfc/handling-customization-notifications.md)中所述。  
  
## 請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)
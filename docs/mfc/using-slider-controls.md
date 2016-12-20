---
title: "使用滑桿控制項 | Microsoft Docs"
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
  - "CSliderCtrl 類別, 使用"
  - "滑桿"
  - "滑桿, 使用"
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用滑桿控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

滑動條控制項的一般使用方式會遵循下列模式:  
  
-   會建立控制項。  如果控制項在對話方塊樣板指定，在對話方塊中建立時建立是自動的。\(您應該會包含動畫控制項\) 的對話方塊類別中的 [CSliderCtrl](../mfc/reference/csliderctrl-class.md) 成員。或者，您可以使用 [建立](../Topic/CSliderCtrl::Create.md) 成員函式來建立控制項做為子視窗的所有視窗。  
  
-   呼叫各種成員函式對控制項的值。  變更可以設定滑桿的最小和最大位置，繪製的刻度標記，將選取範圍和重新調整滑桿。  對於在對話方塊的控制項，好時機可以在對話方塊的 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) 函式。  
  
-   因為使用者與控制項互動，它會傳送各種告知訊息。  您可以從控制項擷取的值會藉由呼叫 [GetPos](../Topic/CSliderCtrl::GetPos.md) 成員函式。  
  
-   當您在使用控制項時，請確定您正確地終止。  如果滑桿控制項在對話方塊中，將自動終結和 `CSliderCtrl` 物件。  否則，您必須確保適當地終結控制項和 `CSliderCtrl` 物件。  
  
## 請參閱  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控制項](../mfc/controls-mfc.md)
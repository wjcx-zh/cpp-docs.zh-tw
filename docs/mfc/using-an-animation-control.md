---
title: "使用動畫控制項 | Microsoft Docs"
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
  - "動畫控制項 [C++]"
  - "CAnimateCtrl 類別, 動畫控制項"
  - "控制項 [MFC], 動畫"
ms.assetid: a009a464-e12d-4112-bf52-04a09b28dd88
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用動畫控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

動畫控制項的一般使用方式會遵循下列模式:  
  
-   會建立控制項。  如果控制項在對話方塊樣板指定，建立是自動的，在對話方塊中建立時。\(您應該會包含動畫控制項\) 的對話方塊類別中的 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md) 成員。或者，您可以使用 [建立](../Topic/CAnimateCtrl::Create.md) 成員函式來建立控制項做為子視窗的所有視窗。  
  
-   載入 AVI 裁剪至動畫控制項藉由呼叫 [開啟](../Topic/CAnimateCtrl::Open.md) 成員函式。  如果您的動畫控制項在對話方塊中，執行此動作的好位置在對話方塊類別的 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) 函式。  
  
-   藉由呼叫 [播放](../Topic/CAnimateCtrl::Play.md) 成員函式播放裁剪。  如果您的動畫控制項在對話方塊中，執行此動作的好位置在對話方塊類別的 **OnInitDialog** 函式。  呼叫 **Play** 不需要動畫控制項是否已設定 `ACS_AUTOPLAY` 的樣式。  
  
-   如果您要顯示裁剪的部分或由架構播放它框架，請使用 `Seek` 成員函式。  若要停止播放的裁剪，請使用 `Stop` 成員函式。  
  
-   如果您沒有立即終結控制項，從記憶體中移除裁剪呼叫 **Close** 成員函式。  
  
-   如果動畫控制項在對話方塊中，將自動終結和 `CAnimateCtrl` 物件。  否則，您必須確保適當地終結控制項和 `CAnimateCtrl` 物件。  終結控制自動關閉 AVI 裁剪。  
  
## 請參閱  
 [使用 CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [控制項](../mfc/controls-mfc.md)
---
title: "初始化對話方塊 | Microsoft Docs"
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
  - "初始化對話方塊"
  - "MFC 對話方塊, 初始化"
  - "強制回應對話方塊, 初始化"
  - "非強制回應對話方塊, 初始化"
  - "OnInitDialog 方法"
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 初始化對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在對話方塊和其所有控制項建立之後，但是，對話方塊 \(任一型別\) 之前出現在螢幕上，對話方塊物件的 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) 成員函式呼叫。  在呼叫 `DoModal` 期間，對於強制回應對話方塊，就會發生這種情況。  對於非強制回應對話方塊，也就是說，當 **Create** 呼叫時，呼叫 `OnInitDialog` 。  您通常會覆寫 `OnInitDialog` 初始化對話方塊的控制項，例如設定編輯方塊的初始文字。  您必須呼叫基底類別， `CDialog`的 `OnInitDialog` 成員函式，從您的 `OnInitDialog` 覆寫。  
  
 如果您要設定自己的對話方塊的背景色彩 \(以及在應用程式的其他對話方塊\)，請參閱 [設定對話方塊的背景色彩。](../mfc/setting-the-dialog-box’s-background-color.md)。  
  
## 請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)
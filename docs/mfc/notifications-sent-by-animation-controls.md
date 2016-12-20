---
title: "動畫控制項傳送的告知 | Microsoft Docs"
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
  - "動畫控制項 [C++], 告知"
  - "CAnimateCtrl 類別, 告知"
  - "控制項 [MFC], 動畫"
  - "告知, 動畫控制項"
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 動畫控制項傳送的告知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

動畫控制項 \([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)\) 傳送通知訊息的兩個不同型別。  以 [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) 訊息的形式傳送通知。  
  
 當動畫控制項開始播放裁剪時， [ACN\_START](http://msdn.microsoft.com/library/windows/desktop/bb761891) 傳送。  當動畫完成控制項或停止播放裁剪時， [ACN\_STOP](http://msdn.microsoft.com/library/windows/desktop/bb761893) 傳送。  
  
## 請參閱  
 [使用 CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [控制項](../mfc/controls-mfc.md)
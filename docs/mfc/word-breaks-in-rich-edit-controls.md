---
title: "Rich Edit 控制項中的斷字法 | Microsoft Docs"
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
  - "CRichEditCtrl 中的斷字"
  - "CRichEditCtrl 類別, 其中的斷字法"
  - "Rich Edit 控制項, 其中的斷字法"
  - "斷字法"
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Rich Edit 控制項中的斷字法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Rich 編輯控制項 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 呼叫「文字中斷程式」的函式尋找文字之間的中斷並判斷標題的位置。  在執行自動換行作業，並在處理向左和 CTRL\+RIGHT 時組合鍵時，控制項會使用這個資訊。  應用程式可以傳送訊息至 Rich 編輯控制項取代預設斷字程序，擷取斷字資訊和決定行指定字元位置。  
  
## 請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)
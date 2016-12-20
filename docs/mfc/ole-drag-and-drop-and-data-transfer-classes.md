---
title: "OLE 拖放和資料傳輸類別 | Microsoft Docs"
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
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 類別 [C++]"
  - "資料傳輸 [C++], OLE"
  - "資料傳輸類別 [C++]"
  - "拖放 [C++], 類別"
  - "OLE 拖放 [C++], 和資料傳輸類別"
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 拖放和資料傳輸類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些類別是用於 OLE 資料傳輸。  它們允許資料是將應用程式之間使用剪貼簿或透過拖放。  
  
 [COleDropSource](../mfc/reference/coledropsource-class.md)  
 從開始到結束控制項拖放作業。  這個類別會決定拖放作業何時開始，以及何時結束。  在拖放作業期間也顯示游標回應。  
  
 [COleDataSource](../mfc/reference/coledatasource-class.md)  
 使用，在應用程式的資料傳輸的資料。  `COleDataSource` 可以視為物件導向的剪貼簿物件。  
  
 [COleDropTarget](../mfc/reference/coledroptarget-class.md)  
 表示拖放作業的目標。  `COleDropTarget` 物件對應到螢幕上的視窗。  它會判斷是否接受任何資料卸除了上方並實作實際置放作業。  
  
 [COleDataObject](../mfc/reference/coledataobject-class.md)  
 當做接收器邊為 `COleDataSource`。  `COleDataObject` 物件可用來存取 `COleDataSource` 物件中的資料。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)
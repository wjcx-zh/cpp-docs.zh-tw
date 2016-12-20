---
title: "Using the RichEdit 1.0 Control with MFC | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "RichEdit 1.0 control"
  - "rich edit controls, RichEdit 1.0"
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using the RichEdit 1.0 Control with MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要使用 RichEdit 控制項，您必須先呼叫 [AfxInitRichEdit2](../Topic/AfxInitRichEdit2.md) 以載入 RichEdit 2.0 控制項 \(RICHED20.DLL\)，或呼叫 [AfxInitRichEdit](../Topic/AfxInitRichEdit.md) 載入舊版 RichEdit 1.0 控制項 \(RICHED32.DLL\)。  
  
 您可以將目前的 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) 類別與舊版的 RichEdit 1.0 控制項一起使用，但是 **CRichEditCtrl** 的設計是僅為了支援 RichEdit 2.0 控制項。  因為 RichEdit 1.0 和 RichEdit 2.0 非常類似，大多數的方法都可以使用；然而，請注意 1.0 和 2.0 控制項之間有一些不同，因此有一些方法可能無法正確地運作，甚至根本無法使用。  
  
## 需求  
 MFC  
  
## 請參閱  
 [Troubleshooting the Dialog Editor](../mfc/troubleshooting-the-dialog-editor.md)   
 [Dialog Editor](../mfc/dialog-editor.md)
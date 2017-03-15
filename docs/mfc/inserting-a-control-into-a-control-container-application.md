---
title: "ActiveX 控制項容器：將控制項插入控制項容器應用程式中 | Microsoft Docs"
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
  - "ActiveX 控制項容器 [C++], 插入控制項"
  - "ActiveX 控制項 [C++], 加入至專案"
ms.assetid: bbb617ff-872f-43d8-b4d6-c49adb16b148
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActiveX 控制項容器：將控制項插入控制項容器應用程式中
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在您可以從 ActiveX 控制項容器應用程式前存取 ActiveX 控制項，請使用 [插入 ActiveX 控制項](../mfc/insert-activex-control-dialog-box.md) 對話方塊，您必須將 ActiveX 控制項加入至容器應用程式。  
  
 若要將 ActiveX 控制項加入至 ActiveX 控制項容器專案，請參閱 [檢視及加入 ActiveX 控制項加入至對話方塊](../mfc/viewing-and-adding-activex-controls-to-a-dialog-box.md)。  
  
 一旦您加入控制項，您需要加入成員變數 \(ActiveX 控制項型別\) 加入至對話方塊類別。  如需這個程序的詳細資訊，請參閱 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)。  
  
 一旦您加入成員變數類別，稱為包裝函式類別，會自動產生及加入至專案。  使用這個類別，控制容器和內嵌控制項之間的介面。  
  
## 請參閱  
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)
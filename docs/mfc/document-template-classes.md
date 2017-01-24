---
title: "文件樣板類別 | Microsoft Docs"
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
  - "vc.classes.document"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文件樣板, 類別"
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 文件樣板類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當新資料或檢視建立時，文件樣板物件協調資料產生，檢視，而且框架視窗物件。  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md)  
 資料範本的基底類別。  您直接永遠不會使用這個類別;相反地，您可以使用衍生自這個類別的其他文件樣板類別之一。  
  
 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)  
 文件的範本在多重文件介面 \(MDI\) \(MDI\)。  MDI 應用程式可以同時開啟多個文件。  
  
 [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)  
 文件的範本在單一文件介面 \(SDI\)。  SDI 應用程式一次只能有一個開啟的文件。  
  
## 相關類別  
 [CCreateContext](../mfc/reference/ccreatecontext-structure.md)  
 結構會文件範本對視窗建立函式協調資料產生、檢視和框架視窗物件。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)
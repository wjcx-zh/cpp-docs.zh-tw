---
title: "對話方塊列 | Microsoft Docs"
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
  - "CDialogBar 類別, 對話方塊列"
  - "控制列, 對話方塊列"
  - "對話方塊列"
  - "對話方塊列, 關於對話方塊列"
  - "MFC, 控制列"
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 對話方塊列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

關於對話方塊列可工具列，可以包含任何類型的控制項的一種 [控制列](../mfc/control-bars.md) 。  由於有非強制回應對話方塊的特性， [CDialogBar](../mfc/reference/cdialogbar-class.md) 物件提供更強大的工具列。  
  
 有工具列和 `CDialogBar` 物件之間的主要差異。  `CDialogBar` 物件在對話方塊樣板資源建立，您可以建立使用 Visual C\+\+ 對話方塊編輯器，而且可以包含任何類型的 Windows 控制項。  使用者可從控制項定位以進行控制。  如果調整大小，也可以指定對齊樣式對齊對話方塊列與父框架視窗的任何部分甚至讓它就緒。  下圖顯示的各種控制項的對話方塊列。  
  
 ![VC 對話方塊列](../mfc/media/vc378t1.png "vc378T1")  
對話方塊列  
  
 在其他方面，與 `CDialogBar` 物件一起使用像是以非強制回應對話方塊一起使用。  使用對話方塊編輯器設計和建立對話方塊資源。  
  
 其中一個對話方塊列美德是刪除按鈕之外，它們可能包含控制項。  
  
 當您衍生時正常自己的對話方塊從 `CDialog`類別，則您應該通常不會取得您的對話方塊列的類別。  對話方塊列可延伸到主視窗，而且所有對話方塊列控制通知資訊，例如 **BN\_CLICKED** 和 **EN\_CHANGE**，傳送到對話方塊列，主視窗的父代。  
  
## 請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)   
 [範例](../top/visual-cpp-samples.md)
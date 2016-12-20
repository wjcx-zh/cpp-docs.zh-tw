---
title: "將通用控制項做為子視窗使用 | Microsoft Docs"
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
  - "子視窗, 通用控制項做為"
  - "通用控制項 [C++], 子視窗"
  - "控制項 [MFC], 做為子視窗使用"
  - "視窗 [C++], 通用控制項做為"
  - "Windows 通用控制項 [C++], 子視窗"
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將通用控制項做為子視窗使用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

任何 Windows 通用控制項可以做為子視窗中其他視窗。  下列程序描述如何動態建立公用控制項一起使用。  
  
### 使用通用控制項做為子視窗使用  
  
1.  定義相關類別或處理常式的控制項。  
  
2.  使用 [CWnd::Create](../Topic/CWnd::Create.md) 方法之控制項的覆寫建立 Windows 控制項。  
  
3.  在建立控制項 \(早於 `OnCreate` 處理常式，則子類別化控制項\) 後，您可以使用其成員函式管理控制項。  請參閱個別控制項在 [控制項](../mfc/controls-mfc.md) 中的說明方法的詳細資料。  
  
4.  當您完成使用控制項時，請使用 [CWnd::DestroyWindow](../Topic/CWnd::DestroyWindow.md) 終結控制項。  
  
## 請參閱  
 [建立及使用控制項](../mfc/making-and-using-controls.md)   
 [控制項](../mfc/controls-mfc.md)
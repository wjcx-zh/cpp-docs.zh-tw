---
title: "Testing the Modified ATL DHTML Control | Microsoft Docs"
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
  - "DHTML controls, 測試"
  - "HTML 控制項, 測試"
  - "testing controls"
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Testing the Modified ATL DHTML Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試您的新控制項看看它現在可以運作。  
  
#### 建立和測試已修改的控制項  
  
1.  重新建置專案並開啟它在測試容器。  如需如何存取測試容器的詳細資訊，請參閱 [測試屬性和事件會和測試容器](../mfc/testing-properties-and-events-with-test-container.md) 。  
  
     調整控制項大小以顯示您所加入的按鈕。  
  
2.  檢查您可以修改 HTML 插入的兩個按鈕。  每個按鈕注意您在 [修改 ATL DHTML 控制項](../atl/modifying-the-atl-dhtml-control.md)識別的標籤: **重新整理** 和 **HelloHTML**。  
  
3.  測試兩個新的按鈕來查看其運作方式。  
  
 現在請測試不屬於 UI 部分的方法。  
  
1.  反白顯示控制項，因此，框線啟動。  
  
2.  在 **控制** 功能表上，按一下 **Invoke Methods**。  
  
 在標示的 **方法名稱** 清單的方法是容器可呼叫的方法: `MethodInvoked`和`GoToURL`。  其他方法是由控制項的 UI。  
  
1.  選取一個叫用方法並按一下 `Invoke` 顯示方法的訊息方塊或巡覽至 www.microsoft.com。  
  
2.  在 **Invoke Methods** 對話方塊中，按一下 **關閉**。  
  
 若要進一步了解組成 ATL DHTML 控制項之各個項目和檔案，請參閱 [識別 DHTML 控制專案的項目。](../atl/identifying-the-elements-of-the-dhtml-control-project.md)。  
  
## 請參閱  
 [DHTML 控制項的支援](../atl/atl-support-for-dhtml-controls.md)
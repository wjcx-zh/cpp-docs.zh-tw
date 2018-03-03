---
title: "如何： 將功能區控制項和事件處理常式加入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f5d5015fdf5fd2a97b6b8a9b9ee9cf5ccc755ce5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>如何：加入功能區控制項和事件處理常式
功能區控制項是項目，例如按鈕和下拉式方塊中，您加入至面板。 面板會顯示一組相關控制項的功能區列區域。  
  
 本主題中，您會開啟功能區設計工具，加入按鈕，並再連結會顯示"Hello World"的事件。  
  
### <a name="to-open-the-ribbon-designer"></a>若要開啟功能區設計工具  
  
1.  在 Visual Studio 中，在**檢視**功能表上，按一下 **資源檢視**。  
  
2.  在**資源檢視**，按兩下功能區資源以顯示在設計介面上。  
  
### <a name="to-add-a-button-and-an-event-handler"></a>若要加入按鈕和事件處理常式  
  
1.  從**工具列**，按一下 **按鈕**並將它拖曳至設計介面中的面板。  
  
2.  以滑鼠右鍵按一下按鈕，然後按一下**加入事件處理常式**。  
  
3.  在**事件處理常式精靈**，確認預設設定，然後按一下**新增和編輯**。 如需詳細資訊，請參閱[事件處理常式精靈](../ide/event-handler-wizard.md)。  
  
4.  在程式碼編輯器中，加入下列程式碼執行處理常式函式：  
  
 ```  
    MessageBox((LPCTSTR)L"Hello World");

 ```  
  
## <a name="see-also"></a>請參閱  
 [RibbonGadgets 範例： 功能區小工具應用程式](../visual-cpp-samples.md)   
 [功能區設計工具 (MFC)](../mfc/ribbon-designer-mfc.md)


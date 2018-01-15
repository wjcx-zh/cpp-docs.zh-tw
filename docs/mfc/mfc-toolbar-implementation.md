---
title: "MFC 工具列實作 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- toolbars [MFC], creating
- buttons [MFC], MFC toolbars
- toolbars [MFC], docking
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- floating toolbars [MFC]
- toolbars [MFC], floating
- docking toolbars [MFC]
- bitmaps [MFC], toolbar
- toolbar controls [MFC]
- CToolBarCtrl class [MFC], implementing toolbars
- tool tips [MFC], enabling
- toolbars [MFC]
- toolbars [MFC], implementing MFC toolbars
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 540f3240588b8e6fde119a167eace8103ef58c5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-toolbar-implementation"></a>MFC 工具列實作
工具列是[控制列](../mfc/control-bars.md)包含控制項的點陣圖影像。 這些映像可像按鈕、 核取方塊或選項按鈕。 MFC 提供類別[CToolbar](../mfc/reference/ctoolbar-class.md)管理工具列。  
  
 如果您啟用它，MFC 工具列的使用者可以停駐視窗邊緣或者 「 浮動 」 應用程式視窗中。 MFC 不支援可自訂工具列，在開發環境中一樣。  
  
 MFC 也支援工具提示： 當您將滑鼠游標放在按鈕上時，描述工具列按鈕的用途的小型快顯視窗。 根據預設，當使用者按下工具列按鈕，狀態字串會出現在 [狀態] 列 （如果有的話）。 您可以啟用 「 即時 」 狀態列更新以顯示狀態字串，當未按下它滑鼠置於按鈕上方時。  
  
> [!NOTE]
>  根據 MFC 4.0 版，工具列工具提示會實作與使用 Windows 95 和更新版本的功能，而不之前的實作特定 MFC。  
  
 回溯相容性，MFC 會保留舊的工具列實作類別中**COldToolBar**。 舊版的 MFC 的文件描述**COldToolBar**下`CToolBar`。  
  
 應用程式精靈中選取 [工具列] 選項，在程式中建立第一個工具列。 您也可以建立其他工具列。  
  
 下列被採用的這篇文章中：  
  
-   [工具列按鈕](#_core_toolbar_buttons)  
  
-   [停駐和浮動工具列](#_core_docking_and_floating_toolbars)  
  
-   [工具列和工具提示](#_core_toolbars_and_tool_tips)  
  
-   [CToolBar 和 CToolBarCtrl 類別](#_core_the_ctoolbar_and_ctoolbarctrl_classes)  
  
-   [工具列點陣圖](#_core_the_toolbar_bitmap)  
  
##  <a name="_core_toolbar_buttons"></a>工具列按鈕  
 在工具列中的按鈕會類似於功能表中的項目。 這兩種使用者介面物件產生命令，提供處理常式函式會處理您的程式。 工具列按鈕通常重複的功能表命令，提供相同功能的替代使用者介面的功能。 這類重複排列僅透過指定按鈕和功能表項目相同的識別碼。  
  
 您可以讓按鈕，在工具列中的顯示且運作為按鈕、 核取方塊或選項按鈕。 如需詳細資訊，請參閱類別[CToolBar](../mfc/reference/ctoolbar-class.md)。  
  
##  <a name="_core_docking_and_floating_toolbars"></a>停駐和浮動工具列  
 MFC 工具列可以：  
  
-   靜止沿著其父視窗一側邊。  
  
-   拖曳和 「 停駐 」，或附加，由任何側或兩側您指定的父視窗的使用者。  
  
-   「 浮動 」，或從框架視窗時，其迷你框架視窗，讓使用者可以移動至任何合適的位置中卸離。  
  
-   調整大小，而浮點數。  
  
 如需詳細資訊，請參閱文章[停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)。  
  
##  <a name="_core_toolbars_and_tool_tips"></a>工具列和工具提示  
 MFC 工具列可以進行顯示 「 工具提示 」，其中包含的工具列按鈕的用途的簡短文字描述的小型快顯視窗。 使用者移動滑鼠移到工具列按鈕上時，工具提示視窗出現提供提示。 如需詳細資訊，請參閱文章[工具列工具提示](../mfc/toolbar-tool-tips.md)。  
  
##  <a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>CToolBar 和 CToolBarCtrl 類別  
 管理您的應用程式工具列，透過類別[CToolBar](../mfc/reference/ctoolbar-class.md)。 根據 MFC 4.0 版，`CToolBar`具有已實作使用適用於 Windows 95 或更新版本，則工具列通用控制項和 Windows NT 3.51 或更新版本。  
  
 這項重新實作導致較少的 MFC 程式碼用於工具列，因為 MFC 使用的作業系統支援。 重新實作亦增強功能。 您可以使用`CToolBar`操作工具列，或成員函式可以取得基礎參考[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)物件，並呼叫其成員函式自訂工具列和其他功能。  
  
> [!TIP]
>  如果您有在投入大量資源的較舊的 MFC 實作`CToolBar`，仍會支援。 請參閱文章[使用您舊的工具列](../mfc/using-your-old-toolbars.md)。  
  
 另請參閱 MFC 一般範例[DOCKTOOL](../visual-cpp-samples.md)。  
  
##  <a name="_core_the_toolbar_bitmap"></a>工具列點陣圖  
 建構完成後，`CToolBar`物件會藉由載入點陣圖，包含每個按鈕的一個映像建立工具列影像。 應用程式精靈建立 Visual c + +，您可以自訂 [標準] 工具列點陣圖[工具列編輯器](../windows/toolbar-editor.md)。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [工具列基本概念](../mfc/toolbar-fundamentals.md)  
  
-   [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)  
  
-   [工具列工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [使用工具列控制項](../mfc/working-with-the-toolbar-control.md)  
  
-   [使用舊的工具列](../mfc/using-your-old-toolbars.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)類別  
  
## <a name="see-also"></a>請參閱  
 [工具列](../mfc/toolbars.md)   
 [工具列編輯器](../windows/toolbar-editor.md)


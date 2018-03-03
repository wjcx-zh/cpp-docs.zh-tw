---
title: "工具列工具提示 |Microsoft 文件"
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
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 248c975c51a2f44f6c9b17094d6b05082a9016a8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="toolbar-tool-tips"></a>工具列工具提示
工具提示會顯示工具列按鈕的用途的簡短描述當您將滑鼠指標移至按鈕的一段時間的小型快顯視窗。 當您使用具有工具列的應用程式精靈建立應用程式時，為您提供工具提示支援。 這篇文章會說明這兩個工具提示支援應用程式精靈，以及如何將工具提示支援加入至您的應用程式所建立。  
  
 本文涵蓋：  
  
-   [啟用工具提示](#_core_activating_tool_tips)  
  
-   [Flyby 狀態列更新](#_core_fly_by_status_bar_updates)  
  
##  <a name="_core_activating_tool_tips"></a>啟用工具提示  
 若要啟用應用程式中的工具提示，您必須執行兩件事：  
  
-   新增`CBRS_TOOLTIPS`其他樣式的樣式 (例如**WS_CHILD**， **WS_VISIBLE**，和其他**CBRS_**樣式) 做為傳遞`dwStyle`參數[CToolBar::Create](../mfc/reference/ctoolbar-class.md#create)函式或在[SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle)。  
  
-   下列程序所述，新增工具列的提示文字，以新行字元 ('\n') 分隔要包含工具列命令的命令列提示字元的字串資源。 字串資源共用的工具列按鈕的識別碼。  
  
#### <a name="to-add-the-tool-tip-text"></a>若要加入工具提示文字  
  
1.  當您要編輯工具列編輯器工具列時，請開啟**工具列按鈕屬性**指定按鈕的視窗。  
  
2.  在**提示**方塊中，指定您想要顯示在工具提示，此按鈕的文字。  
  
> [!NOTE]
>  設定文字，如按鈕屬性工具列編輯器會取代先前的程序，您必須用來開啟，然後編輯字串資源。  
  
 如果啟用工具提示的控制列，放在它的子控制項，控制列將會顯示工具提示控制列上的每個子控制項，只要符合下列準則：  
  
-   控制項的 ID 是-1。  
  
-   字串資料表項目具有相同 ID 的資源檔中的子控制項的工具提示字串。  
  
##  <a name="_core_fly_by_status_bar_updates"></a>Flyby 狀態列更新  
 工具提示與相關功能是 「 立即 」 顯示狀態列更新。 根據預設，狀態 列上的訊息會描述特定工具列按鈕，啟動 按鈕時。 藉由`CBRS_FLYBY`清單中的樣式傳遞給`CToolBar::Create`，您可以讓滑鼠游標而不實際啟動按鈕通過工具列時更新這些訊息。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [MFC 工具列實作 （在工具列上的概觀資訊）](../mfc/mfc-toolbar-implementation.md)  
  
-   [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)類別  
  
-   [使用工具列控制項](../mfc/working-with-the-toolbar-control.md)  
  
-   [使用舊的工具列](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>請參閱  
 [MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)


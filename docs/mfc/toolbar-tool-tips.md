---
title: "工具列工具提示 | Microsoft Docs"
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
  - "CBRS_FLYBY 常數"
  - "CBRS_TOOLTIPS 常數"
  - "flyby 狀態列更新"
  - "狀態列, 工具提示"
  - "工具提示 [C++]"
  - "工具提示 [C++], 啟動"
  - "工具提示 [C++], 加入文字"
  - "更新"
  - "更新, 狀態列訊息"
  - "更新狀態列訊息"
ms.assetid: d1696305-b604-4fad-9f09-638878371412
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 工具列工具提示
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

工具提示會顯示工具列按鈕的用途的簡短描述的微小的快顯視窗，當您一段時間放置在按鈕上。  當您使用有工具列的應用程式精靈的應用程式時，工具提示支援提供。  本文說明兩個應用程式精靈建立的工具提示支援以及如何將工具提示支援加入至應用程式。  
  
 本文包括:  
  
-   [啟動工具提示](#_core_activating_tool_tips)  
  
-   [定點代表越狀態列更新](#_core_fly_by_status_bar_updates)  
  
##  <a name="_core_activating_tool_tips"></a> 啟動工具提示  
 若要啟用應用程式的工具提示，您必須執行兩個動作:  
  
-   將 `CBRS_TOOLTIPS` 樣式套用至以 `dwStyle` 參數 \(例如 **WS\_CHILD**和 **WS\_VISIBLE**和 **CBRS\_** 其他樣式\) 傳遞的其他樣式套用至函式 [CToolBar::Create](../Topic/CToolBar::Create.md) 或 [SetBarStyle](../Topic/CControlBar::SetBarStyle.md)。  
  
-   依照下列程序所述，請附加工具列提示文字，以新行字元 \(「\\ n」\)，其中包含命令列提示字元中輸入工具列命令的字串資源。  字串資源共用工具列按鈕的 ID。  
  
#### 將工具提示文字  
  
1.  當您編輯工具列編輯器中的工具列，請開啟特定按鈕的 **Toolbar Button Properties** 視窗。  
  
2.  在 **Prompt** 方塊中，指定您希望出現在該按鈕的工具提示文字。  
  
> [!NOTE]
>  設定文字顯示為工具列編輯器的按鈕屬性取代程序之前，您必須開啟和編輯字串資源。  
  
 如果與工具提示允許的控制列在其上放置的子控制項，控制列將顯示每個子控制項的工具提示在控制列，只要符合下列準則:  
  
-   控制項的 ID 不是– 1。  
  
-   ID 的字串資料表輸入和資源檔中的子控制項相同的工具提示字串。  
  
##  <a name="_core_fly_by_status_bar_updates"></a> 定點代表越狀態列更新  
 功能與工具提示相關為定點代表越」狀態列更新。  根據預設，按鈕時，會啟動時，在狀態列中的訊息只描述特定工具列按鈕。  將 `CBRS_FLYBY` 樣式清單中傳遞至 `CToolBar::Create`，您可以讓這些訊息被更新，當滑鼠游標經過工具列時，而不用實際啟動按鈕。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [MFC 工具列實作 \(如需工具列的概觀資訊\)](../mfc/mfc-toolbar-implementation.md)  
  
-   [停駐和浮動工具列](../mfc/docking-and-floating-toolbars.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) 類別  
  
-   [與工具列控制項](../mfc/working-with-the-toolbar-control.md)  
  
-   [使用舊的工具列](../mfc/using-your-old-toolbars.md)  
  
## 請參閱  
 [MFC 工具列實作](../mfc/mfc-toolbar-implementation.md)
---
title: "訊息對應範圍的處理常式 | Microsoft Docs"
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
  - "命令處理, 命令更新處理常式"
  - "命令 ID, 訊息對應"
  - "命令傳送, 命令更新處理常式"
  - "命令更新處理常式"
  - "控制項通知訊息"
  - "控制項 [MFC], 告知"
  - "處理函式"
  - "處理函式, 宣告"
  - "處理函式, 訊息對應範圍"
  - "處理常式"
  - "處理常式, 訊息對應範圍"
  - "對應, 訊息範圍"
  - "訊息處理常式"
  - "訊息處理, 訊息處理函式"
  - "訊息對應, 訊息處理函式"
  - "訊息對應, 範圍"
  - "訊息範圍"
  - "訊息範圍, 對應"
  - "訊息對應範圍"
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 訊息對應範圍的處理常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何將訊息範圍加入至單一訊息處理常式 \(Message Handler\) 函式 \(而不是只有一個函式的對應訊息\)。  
  
 這是當您需要類似處理多個訊息或控制項告知的時間。  在這種情況下，您可能想要將所有訊息傳送至單一處理常式函式。  訊息對應範圍可讓您執行此訊息的連續範圍的:  
  
-   您可以將命令 ID 的範圍:  
  
    -   命令處理常式函式。  
  
    -   更新命令處理常式函式。  
  
-   您可以將控制項 ID 的範圍的控制項告知訊息至訊息處理常式函式。  
  
 在此文件中包含的主題:  
  
-   [將訊息對應項目](#_core_writing_the_message.2d.map_entry)  
  
-   [宣告處理常式函式。](#_core_declaring_the_handler_function)  
  
-   [命令 ID 的範圍的範例](#_core_example_for_a_range_of_command_ids)  
  
-   [控制 ID 的範圍的範例](#_core_example_for_a_range_of_control_ids)  
  
##  <a name="_core_writing_the_message.2d.map_entry"></a> 將訊息對應項目  
 如下列範例所示，在 .CPP 檔案中，加入您的訊息對應項目，如下所示:  
  
 [!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_1.cpp)]  
  
 訊息對應項目包括下列項目:  
  
-   訊息對應範圍巨集:  
  
    -   [ON\_COMMAND\_RANGE](../Topic/ON_COMMAND_RANGE.md)  
  
    -   [ON\_UPDATE\_COMMAND\_UI\_RANGE](../Topic/ON_UPDATE_COMMAND_UI_RANGE.md)  
  
    -   [ON\_CONTROL\_RANGE](../Topic/ON_CONTROL_RANGE.md)  
  
-   對巨集的參數:  
  
     前兩個巨集採用三個參數:  
  
    -   開始這個範圍的命令 ID。  
  
    -   結束這個範圍的命令 ID。  
  
    -   訊息處理常式函式的名稱。  
  
     命令 ID 的範圍必須是連續的。  
  
     第三個巨集，則為 `ON_CONTROL_RANGE`，並將額外的第一個參數:一個控制項通知訊息，例如 **EN\_CHANGE**。  
  
##  <a name="_core_declaring_the_handler_function"></a> 宣告處理常式函式。  
 將事件處理常式函式宣告。H 檔案。  下列程式碼顯示這項處理的樣子，如下所示:  
  
 [!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_2.h)]  
  
 單一命令的處理常式函式通常沒有參數。  除了更新處理函式外，訊息對應範圍的處理函式需要額外的參數，則為 `nID`，型別 **UINT**。  這個參數是第一個參數。  額外的參數符合必要的額外的命令 ID 指定命令使用者實際選取。  
  
 如需更新處理函式的參數要求的詳細資訊，請參閱 [命令 ID 的範圍的範例](#_core_example_for_a_range_of_command_ids)。  
  
##  <a name="_core_example_for_a_range_of_command_ids"></a> 命令 ID 的範圍的範例  
 時可以使用範圍?  一個例子像在縮放命令的處理順序 MFC [HIERSVR](../top/visual-cpp-samples.md)範例。  這個命令縮放檢視， VSPackage 會在 25% 和 300% 其正常大小之間。  HIERSVR 的檢視類別使用一個範圍處理與類似於的訊息對應項目的縮放命令:  
  
 [!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_3.cpp)]  
  
 當您將訊息對應項目時，您指定:  
  
-   兩個命令 ID、開始和結束連續範圍。  
  
     在此處其 `ID_VIEW_ZOOM25` 和 `ID_VIEW_ZOOM300`。  
  
-   命令行的處理常式函式名稱。  
  
     在此處為 `OnZoom`。  
  
 函式宣告將如下列所示:  
  
 [!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_4.h)]  
  
 表示更新處理函式多個類似和可能很有用。  它相當常見適用於許多命令寫入 `ON_UPDATE_COMMAND_UI` 處理常式和找到自己文字，或複製，相同多次程式碼。  解決方案是將命令 ID 的範圍為更新處理函式使用 `ON_UPDATE_COMMAND_UI_RANGE` 巨集。  命令 ID 必須形成連續範圍。  如需範例，請參閱 **OnUpdateZoom** 處理常式及其 `ON_UPDATE_COMMAND_UI_RANGE` 訊息對應項目在 HIERSVR 範例的檢視類別。  
  
 更新單一命令的處理常式函式通常會採用單一參數，則為 `pCmdUI`，型別 **CCmdUI\***。  不同於處理常式函式，更新訊息對應範圍的處理函式不需要額外的參數，則為 `nID`，型別 **UINT**。  命令 ID，需要指定命令使用者實際選取，在 `CCmdUI` 中找到物件。  
  
##  <a name="_core_example_for_a_range_of_control_ids"></a> 控制 ID 的範圍的範例  
 另一個有趣的大小寫對應控制項 ID 的範圍的控制項告知訊息給單一處理常式。  假設使用者可以按一下 10 個按鈕中的任一個。  將所有 10 個按鈕加入至處理常式，您的訊息對應項目如下所示::  
  
 [!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_5.cpp)]  
  
 當您在訊息對應時寫入 `ON_CONTROL_RANGE` 巨集，您指定:  
  
-   特定控制項通知訊息。  
  
     在此處它 **BN\_CLICKED**。  
  
-   控制項 ID 值與控制項關聯的連續範圍。  
  
     這些是 `IDC_BUTTON1` 和 `IDC_BUTTON10`。  
  
-   訊息處理常式函式的名稱。  
  
     在此處為 `OnButtonClicked`。  
  
 當您撰寫處理函式時，如下所示，請指定額外 **UINT** 參數，例如:  
  
 [!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/CPP/handlers-for-message-map-ranges_6.cpp)]  
  
 單一 **BN\_CLICKED** 訊息的 `OnButtonClicked` 處理常式沒有參數。  按鈕的範圍內以相同的處理常式並將 **UINT**。  額外參數允許識別特定控制項負責產生 **BN\_CLICKED** 訊息。  
  
 在這個範例顯示的程式碼是典型的:將值傳遞至訊息範圍和判斷提示內的 `int` 是這種情況。  您可以接受按鈕的其他動作。  
  
## 請參閱  
 [宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)
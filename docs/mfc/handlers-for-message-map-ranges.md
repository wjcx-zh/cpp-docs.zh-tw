---
title: "訊息對應範圍的處理常式 |Microsoft 文件"
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
- message handlers [MFC]
- handlers [MFC], message-map ranges
- message maps [MFC], message handler functions
- message maps [MFC], ranges
- control-notification messages [MFC]
- command IDs [MFC], message mapping
- message-map ranges [MFC]
- handlers [MFC]
- message handling [MFC], message handler functions
- mappings [MFC], message ranges
- command handling [MFC], command update handlers
- controls [MFC], notifications
- handler functions [MFC], message-map ranges
- handler functions [MFC]
- command update handlers [MFC]
- command routing [MFC], command update handlers
- message ranges [MFC]
- handler functions [MFC], declaring
- message ranges [MFC], mapping
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02b44288d21ab2df68468b0e39cb1ee35b7b8810
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2018
---
# <a name="handlers-for-message-map-ranges"></a>訊息對應範圍的處理常式
本文說明如何將一個範圍的訊息對應到單一訊息處理函式 （而不是只有一個函式對應一個訊息）。  
  
 但有些的時候，當您需要完全相同的方式處理多個訊息或控制項的通知。 在這種時候，您可能想要將所有的訊息對應至單一處理常式函式。 訊息對應範圍可讓您執行這項操作的連續範圍的訊息：  
  
-   您可以將對應的命令識別碼的範圍：  
  
    -   命令處理常式的函式。  
  
    -   命令更新處理常式函式。  
  
-   您可以將某個範圍的控制項 Id 的控制項通知訊息對應至訊息處理常式函式。  
  
 本文涵蓋的主題包括：  
  
-   [撰寫訊息對應項目](#_core_writing_the_message.2d.map_entry)  
  
-   [宣告處理常式函式](#_core_declaring_the_handler_function)  
  
-   [命令 Id 的範圍內的範例](#_core_example_for_a_range_of_command_ids)  
  
-   [控制項 Id 的範圍內的範例](#_core_example_for_a_range_of_control_ids)  
  
##  <a name="_core_writing_the_message.2d.map_entry"></a> 撰寫訊息對應項目  
 在中。CPP 檔案中加入您的訊息對應項目，如下列範例所示：  
  
 [!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]  
  
 訊息對應項目是由下列項目所組成：  
  
-   訊息對應範圍巨集：  
  
    -   [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)  
  
    -   [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)  
  
    -   [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)  
  
-   在巨集參數：  
  
     前兩個巨集採用三個參數：  
  
    -   命令 ID 開始範圍  
  
    -   命令 ID 範圍結束  
  
    -   訊息處理常式函式名稱  
  
     命令 Id 的範圍必須是連續的。  
  
     第三個巨集， `ON_CONTROL_RANGE`，會採用額外的第一個參數： 控制項通知訊息，例如**EN_CHANGE**。  
  
##  <a name="_core_declaring_the_handler_function"></a> 宣告處理常式函式  
 加入您的處理常式函式宣告中。H 檔案。 下列程式碼將示範可能的外觀，如下所示：  
  
 [!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]  
  
 單一命令的處理常式函式通常不接受任何參數。 更新處理常式函式，除了訊息對應範圍的處理常式函式需要額外的參數， `nID`，型別**UINT**。 這個參數是第一個參數。 額外的參數配合指定使用者實際選擇的命令所需的額外的命令 ID。  
  
 如需更新處理常式函式的參數需求的詳細資訊，請參閱[範例為某個範圍的命令識別碼](#_core_example_for_a_range_of_command_ids)。  
  
##  <a name="_core_example_for_a_range_of_command_ids"></a> 命令 Id 範圍的範例  
 當可能會使用其中一個範例是在處理命令，例如 MFC 範例中的 [縮放] 命令範圍[HIERSVR](../visual-cpp-samples.md)。 此命令放大檢視中，調整 25%到其一般大小的 300%之間。 HIERSVR 的檢視類別與訊息對應項目，類似一個框住這個處理的縮放命令使用的範圍：  
  
 [!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]  
  
 當您撰寫訊息對應項目時，您指定：  
  
-   兩個的命令 Id，開頭和結尾連續範圍。  
  
     以下是`ID_VIEW_ZOOM25`和`ID_VIEW_ZOOM300`。  
  
-   命令處理常式函式名稱。  
  
     這裡有`OnZoom`。  
  
 函式宣告會與以下相似：  
  
 [!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]  
  
 類似，而可能會更廣的更新處理常式函式大小寫。 要寫入相當常見`ON_UPDATE_COMMAND_UI`的命令數目的處理常式，並尋找自行撰寫，或複製，相同的程式碼重複。 解決方法是將命令 Id，其中一個更新處理常式函式使用的範圍對應`ON_UPDATE_COMMAND_UI_RANGE`巨集。 命令 Id 必須形成連續範圍。 如需範例，請參閱**OnUpdateZoom**處理常式及其`ON_UPDATE_COMMAND_UI_RANGE`HIERSVR 範例的檢視類別中的訊息對應項目。  
  
 更新處理常式函式，針對單一命令通常會接受一個參數， `pCmdUI`，型別**CCmdUI\***。 不同於處理常式函式，如訊息對應範圍的更新處理常式函式不需要額外的參數， `nID`，型別**UINT**。 若要指定哪個指令使用者實際上選擇所需的命令 ID 位於`CCmdUI`物件。  
  
##  <a name="_core_example_for_a_range_of_control_ids"></a> 控制項 Id 範圍的範例  
 另一個有趣的情況下對應至單一處理常式的某一範圍的控制項 Id 的控制項通知訊息。 假設使用者可以按一下任何 10 個按鈕。 若要將所有 10 個按鈕對應至一個處理常式，您的訊息對應項目看起來會像這樣：  
  
 [!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]  
  
 當您撰寫`ON_CONTROL_RANGE`中訊息對應巨集，您指定：  
  
-   特定的控制項通知訊息。  
  
     這裡有**BN_CLICKED**。  
  
-   控制項的連續範圍相關聯控制項 ID 的值。  
  
     這些是這裡`IDC_BUTTON1`和`IDC_BUTTON10`。  
  
-   訊息處理常式函式的名稱。  
  
     這裡有`OnButtonClicked`。  
  
 當您撰寫處理常式函式時，指定額外**UINT**參數，如下列所示：  
  
 [!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]  
  
 `OnButtonClicked`單一處理常式**BN_CLICKED**訊息會採用任何參數。 某一範圍的按鈕相同的處理常式會使用其中**UINT**。 額外的參數允許特定的控制項負責產生用來識別**BN_CLICKED**訊息。  
  
 範例所示的程式碼通常是： 將值傳遞至轉換`int`內訊息的範圍和判斷提示，這大小寫。 然後，您可能需要不同的動作依據 button 已按下。  
  
## <a name="see-also"></a>另請參閱  
 [宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)

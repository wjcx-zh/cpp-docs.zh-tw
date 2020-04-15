---
title: 訊息對應範圍的處理常式
ms.date: 11/04/2016
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
ms.openlocfilehash: fc33df6957beab6e4e8de3093dfc00cf2651780e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370513"
---
# <a name="handlers-for-message-map-ranges"></a>訊息對應範圍的處理常式

本文介紹如何將一系列消息映射到單個消息處理程式函數(而不是將一條消息映射到只有一個函數)。

有時,您需要以完全相同的方式處理多條消息或控制通知。 在這種情況下,您可能希望將所有消息映射到單個處理程式函數。 訊息對應範圍允許您對連續的消息範圍執行此操作:

- 您可以將指令 ID 的範圍映射到:

  - 命令處理程式函數。

  - 命令更新處理程式函數。

- 您可以將一系列控制項的 I 將控制項通知訊息映射到消息處理程式函數。

本文涵蓋的主題包括:

- [編寫訊息對應項目](#_core_writing_the_message.2d.map_entry)

- [宣告處理函數](#_core_declaring_the_handler_function)

- [指令 I 系列的範例](#_core_example_for_a_range_of_command_ids)

- [控制項一系列指示器的範例](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>編寫訊息對應項目

在。CPP 檔,添加消息映射項目,如以下範例所示:

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

訊息對應項目由以下項目組成:

- 訊息對應範圍巨集:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- 巨集的參數:

  前兩個巨集採用三個參數:

  - 啟動範圍的指令識別碼

  - 結束範圍的指令識別碼

  - 訊息處理常式函式名稱

  命令指示的範圍從連續的。

  第三個巨`ON_CONTROL_RANGE`集 ,取得額外的第一個參數:控制通知訊息,如**EN_CHANGE**。

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>宣告處理函數

在中添加處理程式函數聲明。H 檔。 以下代碼顯示了可能如下所示,如下所示:

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

單個命令的處理程式函數通常不採用任何參數。 除了更新處理程式函數外,消息映射範圍的處理程式函數需要**UINT**類型的額外參數*nID*。 此參數是第一個參數。 額外參數容納指定用戶實際選擇的命令所需的額外命令 ID。

有關更新處理程式函數的參數要求的詳細資訊,請參閱命令[I 範圍範例](#_core_example_for_a_range_of_command_ids)。

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>命令指示範圍的範例

何時可以使用範圍 一個範例是處理 MFC 示例[HIERSVR](../overview/visual-cpp-samples.md)中的縮放命令等命令。 此命令可縮放檢視,將其縮放在正常大小的 25% 到 300% 之間。 HIERSVR 的檢視類使用範圍來處理縮放命令,其消息映射條目類似於:

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

編寫訊息對應項目時,指定:

- 兩個命令指示,開始和結束連續範圍。

   在這裏,他們是**ID_VIEW_ZOOM25**和**ID_VIEW_ZOOM300。**

- 命令的處理程式函數的名稱。

   這裡是`OnZoom`。

函數宣告類似於:

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

更新處理程式函數的情況類似,並且可能更有用。 為許多命令編寫`ON_UPDATE_COMMAND_UI`處理程式,並發現自己一遍又一遍地編寫或複製相同的代碼是很常見的。 解決方案是使用`ON_UPDATE_COMMAND_UI_RANGE`宏將命令指示數範圍映射到一個更新處理程式函數。 命令指示必須形成連續範圍。 例如,請參閱 HIERSVR 範例的檢視類`OnUpdateZoom`中的 處理`ON_UPDATE_COMMAND_UI_RANGE`程式及其消息映射條目。

單個命令的更新處理程式函數通常採用類型`CCmdUI*`為的單個參數*pCmdUI。* 與處理程式函數不同,消息映射範圍的更新處理程式函數不需要**UINT**類型的額外參數*nID*。 命令 ID(用於指定使用者實際選擇的命令)`CCmdUI`在 物件中找到。

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>控制指示範圍的範例

另一個有趣的情況是,將一系列控件的 I 將控制通知消息映射到單個處理程式。 假設用戶可以按下 10 個按鈕中的任何一個。 要將所有 10 個按鈕映射到一個處理程式,消息映射條目如下所示:

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

在消息對應中`ON_CONTROL_RANGE`寫入巨集時,請指定:

- 特定的控制通知消息。

   這是**BN_CLICKED。**

- 與控制項的連續範圍關聯的控制項ID值。

   這裡是**IDC_BUTTON1**和**IDC_BUTTON10。**

- 消息處理程式函數的名稱。

   這裡是`OnButtonClicked`。

編寫處理程式函數時,請指定額外的**UINT**參數,如下所示:

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

單個`OnButtonClicked`**BN_CLICKED**訊息的處理程式不採用任何參數。 一系列按鈕的同一處理程式需要一個**UINT**。 額外的參數允許識別負責生成**BN_CLICKED**消息的特定控制項。

示例中顯示的代碼是典型的:將傳遞`int`的值轉換為消息範圍內的值,並斷言情況確實如此。 然後,您可以根據按一下的按鈕執行一些不同的操作。

## <a name="see-also"></a>另請參閱

[宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)

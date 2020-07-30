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
ms.openlocfilehash: 44194a6e5bafea2b17c9a1d58c41bf9dc541729d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231906"
---
# <a name="handlers-for-message-map-ranges"></a>訊息對應範圍的處理常式

本文說明如何將某個範圍的訊息對應至單一訊息處理常式函式（而不是只將一個訊息對應至一個函式）。

有時候您需要以完全相同的方式處理一個以上的訊息或控制項通知。 在這種情況下，您可能會想要將所有訊息對應至單一處理程式函式。 訊息對應範圍可讓您針對連續的訊息範圍執行此動作：

- 您可以將命令識別碼的範圍對應到：

  - 命令處理常式函式。

  - 命令更新處理常式函式。

- 您可以將控制項 Id 範圍的控制項通知訊息對應至訊息處理常式函式。

本文涵蓋的主題包括：

- [寫入訊息對應專案](#_core_writing_the_message.2d.map_entry)

- [宣告處理函式](#_core_declaring_the_handler_function)

- [命令識別碼範圍的範例](#_core_example_for_a_range_of_command_ids)

- [控制項識別碼範圍的範例](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>寫入訊息對應專案

在。CPP 檔案，加入您的訊息對應專案，如下列範例所示：

[!code-cpp[NVC_MFCMessageHandling#6](codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

訊息對應專案是由下列專案所組成：

- 訊息對應範圍宏：

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- 宏的參數：

  前兩個宏接受三個參數：

  - 啟動範圍的命令識別碼

  - 結束範圍的命令識別碼

  - 訊息處理常式函式的名稱

  命令識別碼的範圍必須是連續的。

  第三個宏 `ON_CONTROL_RANGE` 會採用額外的第一個參數：控制項通知訊息，例如**EN_CHANGE**。

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>宣告處理函式

在中加入您的處理常式函式宣告。H 檔案。 下列程式碼會顯示其外觀，如下所示：

[!code-cpp[NVC_MFCMessageHandling#7](codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

單一命令的處理常式函式通常不會採用任何參數。 除了更新處理常式函數之外，訊息對應範圍的處理常式函式需要**UINT**類型的額外參數（ *nID*）。 這個參數是第一個參數。 額外的參數會容納指定使用者實際選擇的命令所需的額外命令識別碼。

如需有關更新處理常式函式之參數需求的詳細資訊，請參閱[命令識別碼範圍的範例](#_core_example_for_a_range_of_command_ids)。

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>命令識別碼範圍的範例

當您可能使用範圍時，其中一個範例就是處理命令，例如 MFC 範例[HIERSVR](../overview/visual-cpp-samples.md)中的 Zoom 命令。 此命令會縮放視圖，並在其正常大小的25% 和300% 之間調整。 HIERSVR 的 view 類別使用範圍來處理 Zoom 命令，其中包含如下所示的訊息對應專案：

[!code-cpp[NVC_MFCMessageHandling#8](codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

當您撰寫訊息對應專案時，您可以指定：

- 兩個命令識別碼，開頭和結尾都是連續的範圍。

   在這裡**ID_VIEW_ZOOM25**和**ID_VIEW_ZOOM300**。

- 命令之處理常式函式的名稱。

   就在這裡 `OnZoom` 。

函式宣告如下所示：

[!code-cpp[NVC_MFCMessageHandling#9](codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

更新處理常式函式的情況很類似，而且可能更普遍。 撰寫 `ON_UPDATE_COMMAND_UI` 許多命令的處理常式，並尋找自己撰寫或複製相同的程式碼，是很常見的情況。 解決方法是使用宏，將某個範圍的命令識別碼對應到一個更新處理常式函式 `ON_UPDATE_COMMAND_UI_RANGE` 。 命令識別碼必須形成連續的範圍。 如需範例，請參閱 `OnUpdateZoom` `ON_UPDATE_COMMAND_UI_RANGE` HIERSVR 範例的 view 類別中的處理常式和其訊息對應專案。

單一命令的更新處理常式函式通常會採用類型*pCmdUI*的單一參數 pCmdUI `CCmdUI*` 。 不同于處理常式函式，訊息對應範圍的更新處理常式函數不需要**UINT**類型的額外參數（ *nID*）。 在物件中找到指定使用者實際選擇的命令所需的命令識別碼 `CCmdUI` 。

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>控制項識別碼範圍的範例

另一個有趣的情況是將控制項 Id 範圍的控制項通知訊息對應至單一處理程式。 假設使用者可以按一下10個按鈕。 若要將所有10個按鈕對應到一個處理常式，您的訊息對應專案看起來會像這樣：

[!code-cpp[NVC_MFCMessageHandling#10](codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

當您在 `ON_CONTROL_RANGE` 訊息對應中撰寫宏時，您可以指定：

- 特定的控制項通知訊息。

   **BN_CLICKED**。

- 與連續控制項範圍相關聯的控制項識別碼值。

   這裡是**IDC_BUTTON1**和**IDC_BUTTON10**。

- 訊息處理常式函式的名稱。

   就在這裡 `OnButtonClicked` 。

當您撰寫處理常式函數時，請指定額外的**UINT**參數，如下所示：

[!code-cpp[NVC_MFCMessageHandling#11](codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

`OnButtonClicked`單一**BN_CLICKED**訊息的處理常式不接受任何參數。 針對某個範圍的按鈕，相同的處理常式會採用一個**UINT**。 額外的參數可讓您識別負責產生**BN_CLICKED**訊息的特定控制項。

範例中顯示的程式碼是典型的：將傳遞至的值轉換為 **`int`** 訊息範圍內的，並判斷提示這種情況。 然後，您可能會根據按下的按鈕，採取一些不同的動作。

## <a name="see-also"></a>另請參閱

[宣告訊息處理函式](declaring-message-handler-functions.md)

---
title: 訊息對應範圍的處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca420ce09cae5bf7c11dcfb0ad384e0002bdc4b1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403565"
---
# <a name="handlers-for-message-map-ranges"></a>訊息對應範圍的處理常式

這篇文章說明如何將一個範圍的訊息對應至單一的訊息處理常式函式 （而不是只有一個函式對應一則訊息）。

有些的時候，當您需要完全相同的方式處理多個訊息或控制項通知。 在這類的時間，您可能想要將所有的訊息對應至單一處理常式函式。 訊息對應範圍可讓您執行這項操作的連續範圍的訊息：

- 您可以將對應的命令識別碼的範圍：

   - 命令處理常式函式。

   - 命令更新處理常式函式。

- 您可以將某個範圍內的控制項 Id 的控制項通知訊息對應至訊息處理常式函式。

本文章涵蓋的主題包括：

- [寫入訊息對應項目](#_core_writing_the_message.2d.map_entry)

- [宣告處理常式函式](#_core_declaring_the_handler_function)

- [一系列的命令 Id 的範例](#_core_example_for_a_range_of_command_ids)

- [範圍的控制項 Id 的範例](#_core_example_for_a_range_of_control_ids)

##  <a name="_core_writing_the_message.2d.map_entry"></a> 寫入訊息對應項目

在中。CPP 檔案中，新增您的訊息對應項目，如下列範例所示：

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

訊息對應項目是由下列項目所組成：

- 訊息對應範圍巨集：

   - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

   - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

   - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- 巨集的參數：

     前兩個巨集採取三個參數：

   - 開始範圍命令 ID

   - 範圍結束命令識別碼

   - 訊息處理常式函式的名稱

     命令 Id 的範圍必須是連續的。

     第三個巨集， `ON_CONTROL_RANGE`，會採用一個額外的第一個參數： 控制項通知訊息，例如**EN_CHANGE**。

##  <a name="_core_declaring_the_handler_function"></a> 宣告處理常式函式

新增您的處理常式函式宣告中。H 檔案。 下列程式碼會顯示可能的外觀，如下所示：

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

單一命令的處理常式函式通常不接受任何參數。 更新處理常式函式，除了訊息對應範圍的處理常式函式需要額外的參數， *nID*，型別的**UINT**。 這個參數是第一個參數。 額外的參數適用於在指定的使用者實際上選擇的命令所需的額外的命令 ID。

如需有關更新處理常式函式的參數需求的詳細資訊，請參閱[範例中的某個範圍的命令識別碼](#_core_example_for_a_range_of_command_ids)。

##  <a name="_core_example_for_a_range_of_command_ids"></a> 命令 Id 範圍的範例

當可能會使用其中一個範例是在處理命令，例如 MFC 範例中的 [縮放] 命令的範圍[HIERSVR](../visual-cpp-samples.md)。 此命令就會縮放檢視中，調整 25%到 300%的正常大小之間。 HIERSVR 的檢視類別會使用範圍來處理 [縮放] 命令，使用類似這樣的訊息對應項目：

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

當您撰寫的訊息對應項目時，您指定：

- 兩個命令識別碼，開頭和結尾的連續範圍。

     以下是**ID_VIEW_ZOOM25**並**ID_VIEW_ZOOM300**。

- 命令處理常式函式名稱。

     這裡有`OnZoom`。

函式宣告會像這樣：

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

更新處理常式函式的情況是類似，且可能更廣泛地有用。 經常寫入`ON_UPDATE_COMMAND_UI`一些命令處理常式，而發現自己撰寫，或複製，相同的程式碼重複。 解決方法是將對應的命令處理常式函式使用時，更新其中一個識別碼範圍`ON_UPDATE_COMMAND_UI_RANGE`巨集。 命令 Id 必須形成連續的範圍。 如需範例，請參閱`OnUpdateZoom`處理常式並將其`ON_UPDATE_COMMAND_UI_RANGE`HIERSVR 範例的檢視類別中的訊息對應項目。

更新處理常式函式，針對單一命令通常會採用單一參數， *pCmdUI*，型別的`CCmdUI*`。 不同於處理常式函式中，訊息對應範圍的更新處理常式函式不需要額外的參數， *nID*，型別的**UINT**。 中找到命令識別碼，以指定的命令實際選擇的使用者需要有`CCmdUI`物件。

##  <a name="_core_example_for_a_range_of_control_ids"></a> 控制項 Id 範圍的範例

另一個有趣的案例對應至單一處理常式的某個範圍內的控制項 Id 的控制項通知訊息。 假設使用者可以按一下任何 10 個按鈕。 若要有一個處理常式對應所有 10 個按鈕，您的訊息對應項目會看起來像這樣：

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

當您撰寫`ON_CONTROL_RANGE`訊息對應中的巨集，您指定：

- 特定的控制項通知訊息。

     它具有以下**BN_CLICKED**。

- 連續的控制項範圍相關聯控制項 ID 的值。

     這些如下**IDC_BUTTON1**並**IDC_BUTTON10**。

- 訊息處理常式函式的名稱。

     這裡有`OnButtonClicked`。

當您撰寫處理常式函式時，指定額外**UINT**參數，如下列所示：

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

`OnButtonClicked`單一處理常式**BN_CLICKED**訊息不接受任何參數。 範圍的按鈕相同的處理常式會採用其中一個**UINT**。 額外的參數是用來識別特定的控制項負責產生**BN_CLICKED**訊息。

範例所示的程式碼是典型： 將值傳遞至轉換`int`內訊息的範圍和判斷提示，這會大小寫。 然後，您可能需要一些不同的動作，視所按的按鈕。

## <a name="see-also"></a>另請參閱

[宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)

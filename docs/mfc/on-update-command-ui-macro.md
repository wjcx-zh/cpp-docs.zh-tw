---
title: ON_UPDATE_COMMAND_UI 巨集
ms.date: 09/06/2019
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 2a3f097a44e96fc470719ce636cc1b73e676fb38
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095840"
---
# <a name="on_update_command_ui-macro"></a>ON_UPDATE_COMMAND_UI 巨集

若要將使用者介面物件連接至命令目標物件中的命令更新處理常式，請開啟**類別檢視**，然後以滑鼠右鍵按一下要加入處理常式的類別，然後選擇 [**類別] [Wizard]** 。 在左側的清單中尋找使用者介面物件的識別碼，然後選擇右窗格中的 [ **UPDATE_COMMAND_UI** ]，再按一下 [**新增處理常式**]。 這會在類別中建立處理常式函式，並在訊息對應中新增適當的專案。 如需詳細資訊，請參閱[將訊息對應至](../mfc/reference/mapping-messages-to-functions.md)函式。 您可以在 [**訊息**] 窗格中指定要處理的其他訊息。

例如，若要更新程式之 [編輯] 功能表中的 [全部清除] 命令，請使用**類別 Wizard**在選取的類別中加入訊息對應專案、在類別宣告中呼叫`OnUpdateEditClearAll`的命令更新處理常式的函式宣告，以及空白的類別的實作為檔案中的函式樣板。 函式原型如下所示：

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

就像所有處理常式一樣，函式宣告會顯示**afx_msg**關鍵字。 就像所有更新處理常式，它會採用一個引數，即指向 `CCmdUI` 物件的指標。

## <a name="see-also"></a>另請參閱

[如何：更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)

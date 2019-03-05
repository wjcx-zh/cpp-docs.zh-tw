---
title: ON_UPDATE_COMMAND_UI 巨集
ms.date: 11/04/2016
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 986bc4f12223048a20f88da5d164b24dc1c08ace
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261176"
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI 巨集

使用**屬性**視窗連接使用者介面物件的命令目標物件中的命令更新處理常式。 它會自動連接使用者介面物件的 ID ON_UPDATE_COMMAND_UI 巨集，並建立所將處理更新之物件中的處理常式。 請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md)如需詳細資訊。

例如，若要更新程式的 [編輯] 功能表中 [全部清除] 命令，使用**屬性**視窗，以在所選類別中，更新命令處理常式的函式宣告中新增訊息對應項目稱為`OnUpdateEditClearAll`類別中宣告和空函式範本類別的實作檔中。 函式原型如下所示：

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

像所有的處理常式，函式會顯示**afx_msg**關鍵字。 就像所有更新處理常式，它會採用一個引數，即指向 `CCmdUI` 物件的指標。

## <a name="see-also"></a>另請參閱

[如何：更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)

---
title: 命令和控制項告知的處理常式
ms.date: 11/04/2016
helpviewer_keywords:
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
ms.openlocfilehash: 43b6a517b680a5f6ff092337fbf3d90dd0115dd7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907976"
---
# <a name="handlers-for-commands-and-control-notifications"></a>命令和控制項告知的處理常式

沒有命令或控制項通知訊息的預設處理常式。 因此，您只能依照慣例為這些類別的訊息命名您的處理常式。 當您將命令或控制通知對應至處理常式時，[類別嚮導](reference/mfc-class-wizard.md)會根據命令識別碼或控制通知代碼來建議名稱。 您可以接受建議的名稱、加以變更或予以取代。

慣例會建議您針對其所代表的使用者介面物件，為兩個類別中的處理常式命名。 結果，[編輯] 功能表上 [剪下] 命令的處理常式可能也會被命名

[!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

由於剪下命令通常會在應用程式中執行，因此，架構會將剪下命令的命令 ID 預先定義為**ID_EDIT_CUT**。 如需所有預先定義的命令 ID 的清單，請參閱檔案 AFXRES.H。 如需詳細資訊，請參閱[標準命令](../mfc/standard-commands.md)。

此外，慣例會從標示為「我的按鈕」的按鈕，建議**BN_CLICKED**通知訊息的處理常式

[!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

您可能會將**IDC_MY_BUTTON**的識別碼指派給此命令，因為它相當於應用程式特定的使用者介面物件。

兩種類別的訊息都不接受引數並且不會傳回值。

## <a name="see-also"></a>另請參閱

[宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)

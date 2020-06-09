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
ms.openlocfilehash: cc89cbfde0a1eba5dc736b40c178d4a4fde37a4d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625774"
---
# <a name="handlers-for-commands-and-control-notifications"></a>命令和控制項告知的處理常式

沒有命令或控制項通知訊息的預設處理常式。 因此，您只能依照慣例為這些類別的訊息命名您的處理常式。 當您將命令或控制通知對應至處理常式時，[類別嚮導](reference/mfc-class-wizard.md)會根據命令識別碼或控制通知代碼來建議名稱。 您可以接受建議的名稱、加以變更或予以取代。

慣例會建議您針對其所代表的使用者介面物件，為兩個類別中的處理常式命名。 結果，[編輯] 功能表上 [剪下] 命令的處理常式可能也會被命名

[!code-cpp[NVC_MFCMessageHandling#4](codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

由於剪下命令通常會在應用程式中執行，因此，架構會預先定義**ID_EDIT_CUT**的 cut 命令的命令識別碼。 如需所有預先定義的命令 ID 的清單，請參閱檔案 AFXRES.H。 如需詳細資訊，請參閱[標準命令](standard-commands.md)。

此外，慣例會針對標示為「我的按鈕」的按鈕，建議**BN_CLICKED**通知訊息的處理常式命名為

[!code-cpp[NVC_MFCMessageHandling#5](codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

您可能會將**IDC_MY_BUTTON**的識別碼指派給此命令，因為它相當於應用程式特定的使用者介面物件。

兩種類別的訊息都不接受引數並且不會傳回值。

## <a name="see-also"></a>另請參閱

[宣告訊息處理函式](declaring-message-handler-functions.md)

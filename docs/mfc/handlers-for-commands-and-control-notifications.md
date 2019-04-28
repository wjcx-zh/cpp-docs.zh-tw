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
ms.openlocfilehash: 6c92660c67fa91c27bb094111cebfef57904cdc7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358990"
---
# <a name="handlers-for-commands-and-control-notifications"></a>命令和控制項告知的處理常式

沒有命令或控制項通知訊息的預設處理常式。 因此，您只能依照慣例為這些類別的訊息命名您的處理常式。 當您將命令或控制項通知對應到處理常式時，[屬性] 視窗會根據命令 ID 或控制通知碼建議一個名稱。 您可以接受建議的名稱、加以變更或予以取代。

慣例會建議您針對其所代表的使用者介面物件，為兩個類別中的處理常式命名。 結果，[編輯] 功能表上 [剪下] 命令的處理常式可能也會被命名

[!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]

因為 Cut 命令因此通常應用程式中實作時，架構會預先定義為 [剪下] 命令的命令 ID **ID_EDIT_CUT**。 如需所有預先定義的命令 ID 的清單，請參閱檔案 AFXRES.H。 如需詳細資訊，請參閱 <<c0> [ 標準命令](../mfc/standard-commands.md)。

此外，慣例會建議的處理常式**BN_CLICKED**由標記為 「 My Button 」 按鈕的通知訊息可能會命名為

[!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]

您可以指派此命令的識別碼**IDC_MY_BUTTON**因為它相當於應用程式特定的使用者介面物件。

兩種類別的訊息都不接受引數並且不會傳回值。

## <a name="see-also"></a>另請參閱

[宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)

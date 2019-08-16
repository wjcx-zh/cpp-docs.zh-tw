---
title: 處理 Rebar 控制項中的通知訊息
ms.date: 11/04/2016
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
ms.openlocfilehash: 948990c8597c2ccdcec496252c6801c02a78cbf5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507963"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>處理 Rebar 控制項中的通知訊息

在 Rebar 控制項的父類別中，請為任何一個您要處理的 Rebar 控制項 (`OnChildNotify`) 通知訊息建立一個 switch 陳述式的 `CReBarCtrl` 處理常式函式。 當使用者拖曳物件到 Rebar 控制項上方、變更 Rebar 群組列的配置、從 Rebar 控制項刪除群組列等等時，就會傳送通知給父視窗。

下列通知訊息可以由 Rebar 控制項物件傳送：

- 當 Rebar 自動調整大小時, 由 Rebar 控制項傳送的 RBN_AUTOSIZE (使用 RBS_AUTOSIZE 樣式建立)。

- 當使用者開始拖曳寬線時, 由 Rebar 控制項傳送的 RBN_BEGINDRAG。

- 當寬線的子視窗調整大小時, 由 Rebar 控制項傳送的 RBN_CHILDSIZE。

- 在刪除寬線之後, 由 Rebar 控制項所傳送的 RBN_DELETEDBAND。

- 當要刪除寬線時, 由 Rebar 控制項傳送的 RBN_DELETINGBAND。

- 當使用者停止拖曳寬線時, 由 Rebar 控制項傳送的 RBN_ENDDRAG。

- 當物件拖曳至控制項的寬線上方時, 由 Rebar 控制項 (以 RBS_REGISTERDROP 樣式建立) 所傳送的 RBN_GETOBJECT。

- 當 Rebar 控制項的高度變更時, 它所傳送的 RBN_HEIGHTCHANGE。

- 當使用者變更控制項群組的版面配置時, 由 Rebar 控制項傳送的 RBN_LAYOUTCHANGED。

如需這些通知的詳細資訊, 請參閱 Windows SDK 中的[Rebar 控制項參考](/windows/win32/controls/rebar-control-reference)。

## <a name="see-also"></a>另請參閱

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

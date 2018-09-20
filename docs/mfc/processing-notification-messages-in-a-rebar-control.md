---
title: 處理 Rebar 控制項中的通知訊息 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4532206be5787266df470dedceda0880222b675f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438492"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>處理 Rebar 控制項中的通知訊息

在 Rebar 控制項的父類別中，請為任何一個您要處理的 Rebar 控制項 (`OnChildNotify`) 通知訊息建立一個 switch 陳述式的 `CReBarCtrl` 處理常式函式。 當使用者拖曳物件到 Rebar 控制項上方、變更 Rebar 群組列的配置、從 Rebar 控制項刪除群組列等等時，就會傳送通知給父視窗。

下列通知訊息可以由 Rebar 控制項物件傳送：

- RBN_AUTOSIZE，由 rebar 控制項 （使用 RBS_AUTOSIZE 樣式建立） 傳送當 rebar 自動調整其大小。

- 當使用者開始拖曳群組列的 rebar 控制項傳送 RBN_BEGINDRAG。

- RBN_CHILDSIZE 傳送，由 rebar 控制項寬線子視窗調整大小時。

- RBN_DELETEDBAND 傳送，由 rebar 控制項之後被刪除。

- RBN_DELETINGBAND，由 rebar 控制項即將被刪除時傳送。

- 當使用者停止拖曳群組列的 rebar 控制項傳送 RBN_ENDDRAG。

- RBN_GETOBJECT，由 rebar 控制項 （使用 RBS_REGISTERDROP 樣式建立） 傳送當物件已拖曳至控制項中。

- RBN_HEIGHTCHANGE 傳送 rebar 控制項時，它的高度變更。

- RBN_LAYOUTCHANGED 傳送，由 rebar 控制項，當使用者變更控制項的群組列的配置。

如需有關這些通知的詳細資訊，請參閱 < [Rebar 控制項參考](https://msdn.microsoft.com/library/windows/desktop/bb774375)Windows SDK 中。

## <a name="see-also"></a>另請參閱

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)


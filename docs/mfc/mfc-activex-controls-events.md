---
title: MFC ActiveX 控制項：事件
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
ms.openlocfilehash: 0d8a881d07a3e48673c6dc3298816d165273be0d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276763"
---
# <a name="mfc-activex-controls-events"></a>MFC ActiveX 控制項：事件

ActiveX 控制項使用事件通知告訴它發生了控制項的容器。 事件的常見範例包括按一下控制項時，使用鍵盤和變更控制項的狀態中輸入的資料。 這些動作發生時，控制項就會引發警示之容器的事件。

事件也會呼叫訊息。

MFC 支援兩種類型的事件： 內建和自訂。 內建事件是這些類別的事件[COleControl](../mfc/reference/colecontrol-class.md)會自動處理。 內建事件的完整清單，請參閱文章[MFC ActiveX 控制項：新增內建事件](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)。 自訂事件會讓控制項能夠通知容器，該控制項的特定動作發生時。 某些範例可能是控制項的內部狀態或特定視窗訊息回條的變更。

為您的控制項來正確地引發事件，您的控制項類別必須對應到相關的事件發生時應該呼叫成員函式的控制項的每個事件。 這項對應機制 （稱為 「 事件對應） 集中管理事件的相關資訊，並讓 Visual Studio 輕鬆地存取和操作控制項的事件。 由下列巨集，位於標頭中宣告這個事件對應 (。H） 檔案的控制項類別宣告：

[!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/cpp/mfc-activex-controls-events_1.h)]

在宣告事件對應之後，必須定義在您的控制項實作 (。CPP) 檔案。 下列程式碼會定義事件的對應，可讓您的控制項，來引發特定事件：

[!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

如果您使用 MFC ActiveX 控制項精靈以建立專案時，它會自動新增這幾行。 如果您不使用 MFC ActiveX 控制項精靈，您必須手動加入這些行。

使用 類別檢視中，您可以新增類別所支援的內建事件`COleControl`或您定義的自訂事件。 針對每個新的事件，類別檢視會自動新增適當的項目控制項的事件對應和控制項的。IDL 檔案。

其他兩篇文章討論事件的細節：

- [MFC ActiveX 控制項：新增內建事件](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [MFC ActiveX 控制項：加入自訂事件](../mfc/mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 類別](../mfc/reference/colecontrol-class.md)

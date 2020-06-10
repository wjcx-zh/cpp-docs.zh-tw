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
ms.openlocfilehash: 129b805379fa68cb4f50ee1f8e3ac7d1b725d9ec
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622330"
---
# <a name="mfc-activex-controls-events"></a>MFC ActiveX 控制項：事件

ActiveX 控制項使用事件來通知容器控制項已發生某個問題。 事件的常見範例包括：按一下控制項、使用鍵盤輸入的資料，以及控制項狀態的變更。 當這些動作發生時，控制項會引發事件以警示容器。

事件也稱為「訊息」。

MFC 支援兩種類型的事件： stock 和 custom。 Stock 事件是類別[COleControl](reference/colecontrol-class.md)自動處理的事件。 如需存貨事件的完整清單，請參閱[MFC ActiveX 控制項：加入](mfc-activex-controls-adding-stock-events-to-an-activex-control.md)內建事件一文。 自訂事件可讓控制項在發生該控制項的特定動作時，通知容器。 某些範例會變更控制項的內部狀態或特定視窗訊息的接收。

為了讓您的控制項適當地引發事件，您的控制項類別必須將控制項的每個事件對應至應該在相關事件發生時呼叫的成員函式。 這個對應機制（稱為「事件對應」）會集中處理事件的相關資訊，並可讓 Visual Studio 輕鬆地存取和操作控制項的事件。 這個事件對應是由下列宏（位於標頭（）所宣告。H）控制項類別宣告的檔案：

[!code-cpp[NVC_MFC_AxUI#2](codesnippet/cpp/mfc-activex-controls-events_1.h)]

在宣告事件對應之後，必須在控制項的實作為（中定義）。CPP）檔案。 下列幾行程式碼會定義事件對應，讓您的控制項引發特定事件：

[!code-cpp[NVC_MFC_AxUI#3](codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

如果您使用 MFC ActiveX Control Wizard 來建立專案，則會自動加入這些行。 如果您不使用 MFC ActiveX Control Wizard，就必須手動加入這些行。

使用類別檢視，您可以加入類別所支援的內建事件 `COleControl` ，或您定義的自訂事件。 對於每個新事件，類別檢視會自動將適當的專案加入至控制項的事件對應和控制項的。IDL 檔案。

另兩篇文章會詳細討論事件：

- [MFC ActiveX 控制項：加入內建事件](mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [MFC ActiveX 控制項：新增自訂事件](mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項](mfc-activex-controls.md)<br/>
[MFC ActiveX 控制項：方法](mfc-activex-controls-methods.md)<br/>
[COleControl 類別](reference/colecontrol-class.md)

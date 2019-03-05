---
title: 搭配使用影像清單與 Rebar 控制項
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
ms.openlocfilehash: fa5307c201850fc42439c79a1c638a0707379913
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285395"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>搭配使用影像清單與 Rebar 控制項

除了其他方面，每個 Rebar 群組列還可以包含關聯影像清單中的影像。 下列程序詳述用於顯示 Rebar 群組列中影像的必要步驟。

### <a name="to-display-images-in-a-rebar-band"></a>若要顯示 Rebar 群組列中影像

1. 附加影像清單至 rebar 控制項物件，藉由呼叫[SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist)，將指標傳遞至現有的映像清單。

1. 修改**REBARBANDINFO**結構以指派影像給 rebar 群組列：

   - 設定*fMask*成員，才能`RBBIM_IMAGE`，以包含其他旗標，視使用位元的 OR 運算子。

   - 設定*iImage*要顯示之影像的影像清單索引的成員。

1. 使用必要資訊初始化剩餘的資料成員，例如包含之子視窗的大小、文字和控制代碼。

1. 插入新的群組列 （含影像） 藉由呼叫[crebarctrl:: Insertband](../mfc/reference/crebarctrl-class.md#insertband)，並傳遞**REBARBANDINFO**結構。

下列範例假設，具有兩個影像的現有影像清單物件已附加至 Rebar 控制項物件 (`m_wndReBar`)。 包含第一個影像的新 Rebar 群組列 (由 `rbi`所定義)，已新增對 `InsertBand` 的呼叫：

[!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]

## <a name="see-also"></a>另請參閱

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

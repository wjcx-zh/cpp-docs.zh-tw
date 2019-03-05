---
title: 新增 ATL 訊息處理常式
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
ms.openlocfilehash: cc7631ac9e02891cee725b47133a273e756759d6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302451"
---
# <a name="adding-an-atl-message-handler"></a>新增 ATL 訊息處理常式

若要新增至控制項的訊息處理常式 （的成員函式會處理 Windows 訊息），第一次類別檢視 中選取的控制項。 然後開啟**屬性**視窗中，選取**訊息**圖示，然後按一下下拉箭號控制相反必要的訊息方塊中。 這會新增訊息處理常式的宣告中控制項的標頭檔和控制項的.cpp 檔案中的處理常式的基本架構實作。 它也會新增訊息對應，並新增處理常式項目。

新增 ATL 中的訊息處理常式是類似於 MFC 類別中加入訊息處理常式。 請參閱[加入 MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)如需詳細資訊。

下列條件適用於只新增 ATL 訊息處理常式：

- 訊息處理常式會遵循相同的命名慣例，因此 MFC。

- 新的訊息對應項目新增到主要的訊息對應。 精靈無法辨識替代的訊息對應和鏈結。

## <a name="see-also"></a>另請參閱

[實作視窗](../atl/implementing-a-window.md)

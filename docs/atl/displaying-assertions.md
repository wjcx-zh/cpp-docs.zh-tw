---
title: 顯示判斷提示
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
ms.openlocfilehash: bb06b8f124180ed566ecf2c761deb359444fb019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234874"
---
# <a name="displaying-assertions"></a>顯示判斷提示

如果用戶端連線到您的服務會停止回應，服務可能判斷提示並顯示訊息方塊，您不能看到。 您可以使用視覺效果來確認此C++的偵錯工具偵錯程式碼 (請參閱[使用工作管理員](../atl/using-task-manager.md)本節稍早的)。

如果您判斷您的服務會顯示訊息方塊，看不到，您可能想要設定**允許服務與桌面互動**選項後再一次使用服務。 此選項會允許服務才會出現在桌面上顯示任何訊息方塊的啟動參數。 若要設定此選項，開啟 [服務] 控制台應用程式中，選取的服務，按一下**啟始**，然後選取**允許服務與桌面互動**選項。

## <a name="see-also"></a>另請參閱

[偵錯提示](../atl/debugging-tips.md)

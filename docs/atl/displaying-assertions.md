---
title: 顯示判斷提示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ff7b9b29808e310be2d5568add64a0294bc67e7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762378"
---
# <a name="displaying-assertions"></a>顯示判斷提示

如果用戶端連線到您的服務會停止回應，服務可能判斷提示並顯示訊息方塊，您不能看到。 您可以使用 Visual c + + 的偵錯工具偵錯程式碼來確認此 (請參閱[使用工作管理員](../atl/using-task-manager.md)本節稍早的)。

如果您判斷您的服務會顯示訊息方塊，看不到，您可能想要設定**允許服務與桌面互動**選項後再一次使用服務。 此選項會允許服務才會出現在桌面上顯示任何訊息方塊的啟動參數。 若要設定此選項，開啟 [服務] 控制台應用程式中，選取的服務，按一下**啟始**，然後選取**允許服務與桌面互動**選項。

## <a name="see-also"></a>另請參閱

[偵錯提示](../atl/debugging-tips.md)


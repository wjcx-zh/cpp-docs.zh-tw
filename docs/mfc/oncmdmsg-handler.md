---
title: OnCmdMsg 處理常式
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 5114fe53a5bac345eb6a55fb6c371f7bc1f698ef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624033"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg 處理常式

若要完成命令路由，每個命令目標會呼叫序列中下一個命令目標的 `OnCmdMsg` 成員函式。 命令目標會使用 `OnCmdMsg` 判斷是否可以處理命令，如果無法處理便傳送至另一個命令目標。

每個命令目標類別可能會覆寫 `OnCmdMsg` 成員函式。 覆寫會讓每個類別將命令路由傳送到下一個特定目標。 例如，框架視窗一律會將命令路由至其目前的子視窗或視圖，如資料表[標準命令路由](command-routing.md)中所示。

`CCmdTarget` 的預設 `OnCmdMsg` 實作會使用命令目標類別的訊息對應，搜尋每一個接收到的命令訊息的處理函式，其與搜尋標準訊息的方式相同。 如果找到符合的項目，便會呼叫處理常式。 訊息對應搜尋會在[架構如何搜尋訊息對應](how-the-framework-searches-message-maps.md)中說明。

## <a name="see-also"></a>另請參閱

[架構如何呼叫處理常式](how-the-framework-calls-a-handler.md)

---
title: 哪裡可以找到訊息對應
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: eec0ae43546e3cc0c08e3178c4808e21fa48686a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360169"
---
# <a name="where-to-find-message-maps"></a>哪裡可以找到訊息對應

使用應用程式嚮導創建新的骨架應用程式時,應用程式嚮導會為其創建的每個命令目標類編寫一個消息映射。 這包括派生的應用程式、文檔、檢視和框架視窗類。 其中一些消息映射已包含應用程式嚮導為某些消息和預定義命令提供的條目,有些只是要添加的處理程式的占位符。

類的消息映射位於 中。類的 CPP 檔。 使用應用程式精靈建立的基本消息映射,可以使用[類嚮導](reference/mfc-class-wizard.md)為每個類將處理的消息和命令添加條目。 添加一些條目后,典型的消息映射可能如下所示:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

消息映射由宏的集合組成。 兩個宏[,BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)和[END_MESSAGE_MAP,](reference/message-map-macros-mfc.md#end_message_map)將消息映射置於括弧。 其他宏(如`ON_COMMAND`)將填寫消息映射的內容。

> [!NOTE]
> 消息映射宏後面不跟分號。

當您使用"添加類"嚮導創建新類時,它將為類提供消息映射。 或者,您可以使用原始程式碼編輯器手動創建消息映射。

## <a name="see-also"></a>另請參閱

[架構如何搜尋訊息對應](../mfc/how-the-framework-searches-message-maps.md)

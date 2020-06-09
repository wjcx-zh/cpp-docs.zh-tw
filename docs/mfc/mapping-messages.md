---
title: 對應訊息
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], about message maps
- mappings [MFC], commands
- commands [MFC], mapping
- command mapping [MFC]
- message handling [MFC], connecting to handler functions
- commands [MFC], connecting to handler functions
- mappings [MFC], messages
- messages [MFC], mapping
ms.assetid: 996f0652-0698-4b8c-b893-cdaa836d9d0f
ms.openlocfilehash: 16d6d7725d82bed6c9bfc02e408b68dcf7ffe5e4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625496"
---
# <a name="mapping-messages"></a>對應訊息

每個可以接收訊息或命令的架構類別皆有其自己的「訊息對應」。 架構會使用訊息對應將訊息和命令連接到它們的處理函式。 任何衍生自類別 `CCmdTarget` 的類別皆可有訊息對應。 其他文件會詳細解釋訊息對應並說明用法。

儘管名稱為「訊息對應」，訊息對應也會處理訊息和命令，這三個訊息類別都會列在[訊息類別](message-categories.md)中。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](messages-and-commands-in-the-framework.md)

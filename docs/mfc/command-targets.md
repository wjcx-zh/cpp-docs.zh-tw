---
title: 命令目標
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: 59ba197174e95e42cd237c875f39f07801cb3dbe
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619318"
---
# <a name="command-targets"></a>命令目標

[架構中](user-interface-objects-and-command-ids.md)的圖形命令會顯示使用者介面物件（例如功能表項目）與架構呼叫的處理函式之間的連接，以在按一下物件時執行產生的命令。

Windows 會將不是命令訊息的訊息直接傳送至視窗，而其訊息處理常式則接著被呼叫。 不過，架構會將命令路由至多個候選物件 (稱為「命令目標」)，其中一個通常會叫用命令的處理常式。 處理常式函式對於命令和標準 Windows 訊息的運作方式相同，但呼叫它們的機制不同，如[架構如何呼叫處理常式](how-the-framework-calls-a-handler.md)中所述。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](messages-and-commands-in-the-framework.md)

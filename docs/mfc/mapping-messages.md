---
title: 將訊息對應 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7324da5eaff15d240cabbaede2c2982021361257
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410974"
---
# <a name="mapping-messages"></a>對應訊息

每個可以接收訊息或命令的架構類別皆有其自己的「訊息對應」。 架構會使用訊息對應將訊息和命令連接到它們的處理函式。 任何衍生自類別 `CCmdTarget` 的類別皆可有訊息對應。 其他文件會詳細解釋訊息對應並說明用法。

儘管名稱 「 訊息對應 」 訊息對應會處理訊息和命令，所有三個訊息中列出分類[訊息分類](../mfc/message-categories.md)。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)


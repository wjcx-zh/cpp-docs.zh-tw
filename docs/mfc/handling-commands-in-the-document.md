---
title: 處理文件中的命令
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
ms.openlocfilehash: f3cce539d52bd04e97a6b5f84cbd833b05afb5bb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280429"
---
# <a name="handling-commands-in-the-document"></a>處理文件中的命令

您的文件類別可能也會處理功能表項目、 工具列按鈕或快速鍵產生的特定命令。 根據預設，`CDocument`處理儲存和另存新檔命令 [檔案] 功能表中，使用序列化。 其他會影響資料的命令可能也會處理由您的文件的成員函式。 例如，在 Scribble 程式中，類別`CScribDoc`編輯全部清除 命令，這會刪除所有目前儲存在文件中的資料提供的處理常式。 文件可以有訊息對應，但不同檢視，於文件無法處理標準 Windows 訊息 — 僅**WM_COMMAND**訊息或 「 命令 」。

## <a name="see-also"></a>另請參閱

[使用文件](../mfc/using-documents.md)

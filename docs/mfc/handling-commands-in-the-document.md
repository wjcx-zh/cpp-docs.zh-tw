---
title: 處理文件中的命令 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8845ea7c44fd5a34774db0508302f5959987cdc9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441261"
---
# <a name="handling-commands-in-the-document"></a>處理文件中的命令

您的文件類別可能也會處理功能表項目、 工具列按鈕或快速鍵產生的特定命令。 根據預設，`CDocument`處理儲存和另存新檔命令 [檔案] 功能表中，使用序列化。 其他會影響資料的命令可能也會處理由您的文件的成員函式。 例如，在 Scribble 程式中，類別`CScribDoc`編輯全部清除 命令，這會刪除所有目前儲存在文件中的資料提供的處理常式。 文件可以有訊息對應，但不同檢視，於文件無法處理標準 Windows 訊息 — 僅**WM_COMMAND**訊息或 「 命令 」。

## <a name="see-also"></a>另請參閱

[使用文件](../mfc/using-documents.md)


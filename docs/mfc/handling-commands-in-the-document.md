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
ms.openlocfilehash: ed2ef635437408cacfd600d6cdba4b3731d575b4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625748"
---
# <a name="handling-commands-in-the-document"></a>處理文件中的命令

您的檔類別也可以處理功能表項目、工具列按鈕或快速鍵所產生的特定命令。 根據預設，會 `CDocument` 使用序列化處理 [檔案] 功能表上的 [儲存] 和 [另存新檔] 命令。 其他會影響資料的命令也可能由檔的成員函式來處理。 例如，在自由曲線程式中，類別會 `CScribDoc` 為 [全部編輯] 的 [全部清除] 命令提供處理常式，以刪除目前儲存在檔中的所有資料。 檔可以有訊息對應，但不同于 views，檔無法處理標準的 Windows 訊息，只會**WM_COMMAND**訊息或「命令」。

## <a name="see-also"></a>另請參閱

[使用文件](using-documents.md)

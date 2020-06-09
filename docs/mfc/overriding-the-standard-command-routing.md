---
title: 覆寫標準命令路由
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 680b185f8d68a834862bc0fe14bf6e7984effd65
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617728"
---
# <a name="overriding-the-standard-command-routing"></a>覆寫標準命令路由

偶爾當您必須實作一些標準架構路由變化時，您可以覆寫它。 這個概念是可以藉由在這些類別中覆寫 `OnCmdMsg` 來變更一個或多個類別的路由。 可以這麼做：

- 在中斷命令以傳遞至非預設物件的類別。

- 在新的非預設物件，或在可能接收依序傳遞之命令的命令目標。

如果您將一些新物件插入至路由，其類別必須是命令目標類別。 在您覆寫的 `OnCmdMsg` 版本中，務必呼叫您覆寫的版本。 如需範例，請參閱 MFC 參考中類別的[OnCmdMsg](reference/ccmdtarget-class.md#oncmdmsg)成員函式 `CCmdTarget` ，以及這些類別中的版本（如和） *MFC Reference* `CView` `CDocument` 。

## <a name="see-also"></a>另請參閱

[架構如何呼叫處理常式](how-the-framework-calls-a-handler.md)

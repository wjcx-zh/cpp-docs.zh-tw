---
title: 覆寫標準命令路由
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 5383c1053894d44e23baf51b19ac3df4e60158e5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277946"
---
# <a name="overriding-the-standard-command-routing"></a>覆寫標準命令路由

偶爾當您必須實作一些標準架構路由變化時，您可以覆寫它。 這個概念是可以藉由在這些類別中覆寫 `OnCmdMsg` 來變更一個或多個類別的路由。 可以這麼做：

- 在中斷命令以傳遞至非預設物件的類別。

- 在新的非預設物件，或在可能接收依序傳遞之命令的命令目標。

如果您將一些新物件插入至路由，其類別必須是命令目標類別。 在您覆寫的 `OnCmdMsg` 版本中，務必呼叫您覆寫的版本。 請參閱[OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg)類別成員函式`CCmdTarget`中*MFC 參考 》* 並做為這類類別中的版本`CView`並`CDocument`中提供的原始碼的範例。

## <a name="see-also"></a>另請參閱

[架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)

---
title: 訊息處理常式
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
ms.openlocfilehash: 0d3ed6239b638a0e161cd7e3580f4fe6e1b4a7e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383752"
---
# <a name="message-handlers"></a>訊息處理常式

在 MFC 中，專用*處理常式*函式會處理每個個別的訊息。 訊息處理函式是類別的成員函式。 這份文件使用詞彙*訊息處理常式成員函式*，*訊息處理常式函式*，*訊息處理常式*，和*處理常式*交替。 有些類型的訊息處理常式也稱為「命令處理常式」。

撰寫訊息處理常式在架構應用程式的撰寫中佔相當大的比例。 本文章系列說明訊息處理機制的運作方式。

用途這麼一則訊息的處理常式沒有任何要完成的動作以回應訊息。 您可以使用類別的 [屬性] 視窗建立處理常式，然後使用原始程式碼編輯器填入處理常式的程式碼。

您可以使用任何 Microsoft Visual C++ 和 MFC 的功能撰寫處理常式。 如需所有類別的清單，請參閱 <<c0> [ 類別庫概觀](../mfc/class-library-overview.md)中*MFC 參考 》*。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)

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
ms.openlocfilehash: f9c5272b513a92dc6dcfa37559b00ae79b658918
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619981"
---
# <a name="message-handlers"></a>訊息處理常式

在 MFC 中，專用的*處理常式*函式會處理每個個別的訊息。 訊息處理函式是類別的成員函式。 本檔會使用詞彙*訊息處理常式成員函式*、訊息處理常式*函數*、*訊息處理*程式和*處理常式*交換。 有些類型的訊息處理常式也稱為「命令處理常式」。

撰寫訊息處理常式在架構應用程式的撰寫中佔相當大的比例。 本文章系列說明訊息處理機制的運作方式。

訊息的處理常式會執行所需的動作來回應該訊息。 您可以使用類別的[類別 Wizard](reference/mfc-class-wizard.md)來建立處理常式，然後使用原始程式碼編輯器填入處理常式的程式碼。

您可以使用任何 Microsoft Visual C++ 和 MFC 的功能撰寫處理常式。 如需所有類別的清單，請參閱*MFC 參考*中的[類別庫總覽](class-library-overview.md)。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](messages-and-commands-in-the-framework.md)

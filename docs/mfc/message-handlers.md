---
title: 訊息處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22dde243bb6d8e8a283e670804d4b8b6cad9082c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406746"
---
# <a name="message-handlers"></a>訊息處理常式

在 MFC 中，專用*處理常式*函式會處理每個個別的訊息。 訊息處理函式是類別的成員函式。 這份文件使用詞彙*訊息處理常式成員函式*，*訊息處理常式函式*，*訊息處理常式*，和*處理常式*交替。 有些類型的訊息處理常式也稱為「命令處理常式」。

撰寫訊息處理常式在架構應用程式的撰寫中佔相當大的比例。 本文章系列說明訊息處理機制的運作方式。

用途這麼一則訊息的處理常式沒有任何要完成的動作以回應訊息。 您可以使用類別的 [屬性] 視窗建立處理常式，然後使用原始程式碼編輯器填入處理常式的程式碼。

您可以使用任何 Microsoft Visual C++ 和 MFC 的功能撰寫處理常式。 如需所有類別的清單，請參閱 <<c0> [ 類別庫概觀](../mfc/class-library-overview.md)中*MFC 參考 》*。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)


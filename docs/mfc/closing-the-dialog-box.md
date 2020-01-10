---
title: 關閉對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 48ea954552b3ea9aa7193a47fc2a66d731312d77
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685383"
---
# <a name="closing-the-dialog-box"></a>關閉對話方塊

當使用者選擇強制回應對話方塊的任何按鈕 (通常是 [確定] 按鈕或 [取消] 按鈕) 時，對話方塊便會關閉。 選擇 [確定] 或 [取消] 按鈕，會讓 Windows 以按鈕的識別碼（ **IDOK**或**IDCANCEL**）傳送**BN_CLICKED**控制項通知訊息給對話方塊物件。 `CDialog` 會為以下訊息提供預設的處理函式：`OnOK` 和 `OnCancel`。 預設處理常式會呼叫 `EndDialog` 成員函式，以關閉對話方塊視窗。 您也可以從自己的程式碼呼叫 `EndDialog`。 如需詳細資訊，請參閱*MFC 參考*中 `CDialog` 類別的[EndDialog](../mfc/reference/cdialog-class.md#enddialog)成員函式。

若要排列關閉和刪除非強制回應對話方塊，請覆寫 `PostNcDestroy`，並在**this**指標上叫用**delete**運算子。 終結[對話方塊](../mfc/destroying-the-dialog-box.md)說明接下來會發生什麼事。

## <a name="see-also"></a>另請參閱

[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)

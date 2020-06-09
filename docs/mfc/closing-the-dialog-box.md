---
title: 關閉對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: a695a8e331eb8a4f22394deb65857bf93ecab41e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617200"
---
# <a name="closing-the-dialog-box"></a>關閉對話方塊

當使用者選擇強制回應對話方塊的任何按鈕 (通常是 [確定] 按鈕或 [取消] 按鈕) 時，對話方塊便會關閉。 選擇 [確定] 或 [取消] 按鈕，會讓 Windows 以按鈕的識別碼（ **IDOK**或**IDCANCEL**）傳送對話方塊物件**BN_CLICKED**控制項通知訊息。 `CDialog` 會為以下訊息提供預設的處理函式：`OnOK` 和 `OnCancel`。 預設處理常式會呼叫 `EndDialog` 成員函式，以關閉對話方塊視窗。 您也可以從自己的程式碼呼叫 `EndDialog`。 如需詳細資訊，請[EndDialog](reference/cdialog-class.md#enddialog)參閱 `CDialog` *MFC 參考*中類別的 EndDialog 成員函式。

若要排列關閉和刪除非強制回應對話方塊，請覆寫並叫用 `PostNcDestroy` **this**指標上的**delete**運算子。 終結[對話方塊](destroying-the-dialog-box.md)說明接下來會發生什麼事。

## <a name="see-also"></a>另請參閱

[在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)

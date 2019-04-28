---
title: 關閉對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: 07e4159eccde1fab89d4a5ffadee4e6d11fc20f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326842"
---
# <a name="closing-the-dialog-box"></a>關閉對話方塊

當使用者選擇強制回應對話方塊的任何按鈕 (通常是 [確定] 按鈕或 [取消] 按鈕) 時，對話方塊便會關閉。 選擇 [確定] 或 [取消] 按鈕會使 Windows 將對話方塊物件傳送**BN_CLICKED**與按鈕的控制項通知訊息的識別碼，或是**IDOK**或是**IDCANCEL**。 `CDialog` 會為以下訊息提供預設的處理函式：`OnOK` 和 `OnCancel`。 預設處理常式會呼叫 `EndDialog` 成員函式，以關閉對話方塊視窗。 您也可以從自己的程式碼呼叫 `EndDialog`。 如需詳細資訊，請參閱 < [EndDialog](../mfc/reference/cdialog-class.md#enddialog)類別成員函式`CDialog`中*MFC 參考 》*。

若要安排關閉和刪除非強制回應對話方塊，覆寫`PostNcDestroy`，並叫用**刪除**運算子**這**指標。 [終結對話方塊](../mfc/destroying-the-dialog-box.md)說明接下來的情況。

## <a name="see-also"></a>另請參閱

[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

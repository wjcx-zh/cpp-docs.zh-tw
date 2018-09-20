---
title: 關閉對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9ad4b8af63b68912c232767bf1fd14070fda261
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409047"
---
# <a name="closing-the-dialog-box"></a>關閉對話方塊

當使用者選擇強制回應對話方塊的任何按鈕 (通常是 [確定] 按鈕或 [取消] 按鈕) 時，對話方塊便會關閉。 選擇 [確定] 或 [取消] 按鈕會使 Windows 將對話方塊物件傳送**BN_CLICKED**與按鈕的控制項通知訊息的識別碼，或是**IDOK**或是**IDCANCEL**。 `CDialog` 會為以下訊息提供預設的處理函式：`OnOK` 和 `OnCancel`。 預設處理常式會呼叫 `EndDialog` 成員函式，以關閉對話方塊視窗。 您也可以從自己的程式碼呼叫 `EndDialog`。 如需詳細資訊，請參閱 < [EndDialog](../mfc/reference/cdialog-class.md#enddialog)類別成員函式`CDialog`中*MFC 參考 》*。

若要安排關閉和刪除非強制回應對話方塊，覆寫`PostNcDestroy`，並叫用**刪除**運算子**這**指標。 [終結對話方塊](../mfc/destroying-the-dialog-box.md)說明接下來的情況。

## <a name="see-also"></a>另請參閱

[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)


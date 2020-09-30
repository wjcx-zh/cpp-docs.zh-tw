---
title: 對話方塊資料驗證
ms.date: 11/04/2016
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
ms.openlocfilehash: 9de2db002d7f06e797531c09af0a021c402eec7d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502277"
---
# <a name="dialog-data-validation"></a>對話方塊資料驗證

您可以藉由呼叫 DDV 函式來指定資料交換以外的驗證，如 [對話方塊資料交換](dialog-data-exchange.md)中的範例所示。 `DDV_MaxChars`範例中的呼叫會驗證文字方塊控制項中輸入的字串不超過20個字元。 如果驗證失敗，DDV 函式通常會使用訊息方塊來警示使用者，並將焦點放在違規的控制項，讓使用者可以重新輸入資料。 您必須在相同控制項的 DDX 函式之後，立即呼叫指定控制項的 DDV 函式。

您也可以定義自己的自訂 DDX 和 DDV 常式。 如需有關 DDX 和 DDV 的這個和其他方面的詳細資訊，請參閱 [MFC 技術提示 26](tn026-ddx-and-ddv-routines.md)。

[ [加入成員變數] 嚮導](../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) 會為您撰寫資料對應中的所有 DDX 和 DDV 呼叫。

## <a name="see-also"></a>另請參閱

[對話資料交換和驗證](dialog-data-exchange-and-validation.md)<br/>
[在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)<br/>
[對話方塊資料交換](dialog-data-exchange.md)

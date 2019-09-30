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
ms.openlocfilehash: c89ed82b148062ddb64fa85eaabda12f44e59895
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685772"
---
# <a name="dialog-data-validation"></a>對話方塊資料驗證

您可以藉由呼叫 DDV 函式來指定除了資料交換以外的驗證，如[對話方塊資料交換](../mfc/dialog-data-exchange.md)中的範例所示。 範例中的 `DDV_MaxChars` 呼叫會驗證文字方塊控制項中輸入的字串長度不超過20個字元。 DDV 函式通常會在驗證失敗時以訊息方塊來警示使用者，並將焦點放在違規的控制項上，讓使用者可以重新輸入資料。 指定控制項的 DDV 函數必須在相同控制項的 DDX 函式之後立即呼叫。

您也可以定義自己的自訂 DDX 和 DDV 常式。 如需有關 DDX 和 DDV 的這方面和其他層面的詳細資訊，請參閱[MFC 技術提示 26](../mfc/tn026-ddx-and-ddv-routines.md)。

[[加入成員變數] Wizard](../ide/add-member-variable-wizard.md)會為您撰寫資料對應中的所有 DDX 和 DDV 呼叫。

## <a name="see-also"></a>另請參閱

[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)<br/>
[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[對話方塊資料交換](../mfc/dialog-data-exchange.md)

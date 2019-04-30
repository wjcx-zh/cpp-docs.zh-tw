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
ms.openlocfilehash: cef9941cccd49ca61f0a93472636656f7241a61e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383811"
---
# <a name="dialog-data-validation"></a>對話方塊資料驗證

中的範例所示，您可以藉由呼叫 DDV 函式中，指定除了資料交換的驗證[對話資料交換](../mfc/dialog-data-exchange.md)。 `DDV_MaxChars`呼叫在範例中，驗證輸入文字方塊控制項中的字串不超過 20 個字元。 如果驗證失敗，並將焦點放在違規的控制項，讓使用者可以重新輸入資料 DDV 函式通常會警示使用者的訊息方塊。 DDV 函式，以指定的控制項必須 DDX 函式之後立即呼叫相同的控制項。

您也可以定義您自己自訂的 DDX 和 DDV 常式。 如需此功能與其他方面的 DDX 和 DDV 的詳細資訊，請參閱[MFC 技術提示 26](../mfc/tn026-ddx-and-ddv-routines.md)。

[加入成員變數精靈](../ide/add-member-variable-wizard.md)會寫入所有的 DDX 和 DDV 資料對應中會為您呼叫。

## <a name="see-also"></a>另請參閱

[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)<br/>
[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[對話方塊資料交換](../mfc/dialog-data-exchange.md)

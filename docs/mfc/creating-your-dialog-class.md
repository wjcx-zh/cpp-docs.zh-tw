---
title: 建立您的對話方塊類別
ms.date: 09/06/2019
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: 424d18196063456245e2a4841b42e6e447bded17
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907332"
---
# <a name="creating-your-dialog-class"></a>建立您的對話方塊類別

針對程式中的每個對話方塊，建立新的對話方塊類別以使用對話資源。

新增[類別](../ide/adding-a-class-visual-cpp.md)說明如何建立新的對話方塊類別。 當您使用[類別 Wizard](reference/mfc-class-wizard.md)建立對話方塊類別時，它會在您指定的 .h 和 .cpp 檔案中寫入下列專案：

在 .h 檔案中：

- 對話方塊類別的類別宣告。 類別衍生自[CDialog](../mfc/reference/cdialog-class.md)。

在 .cpp 檔案中：

- 類別的訊息對應。

- 對話方塊的標準構造函式。

- [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)成員函式的覆寫。 編輯此函式。 它用於對話方塊資料交換和驗證功能，如稍後的[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)中所述。

## <a name="see-also"></a>另請參閱

[使用程式碼精靈建立對話方塊類別](../mfc/creating-a-dialog-class-with-code-wizards.md)<br/>
[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

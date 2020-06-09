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
ms.openlocfilehash: fab75268e39d75b67db435ebb8d0af6c0b8371fd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620508"
---
# <a name="creating-your-dialog-class"></a>建立您的對話方塊類別

針對程式中的每個對話方塊，建立新的對話方塊類別以使用對話資源。

新增[類別](../ide/adding-a-class-visual-cpp.md)說明如何建立新的對話方塊類別。 當您使用[類別 Wizard](reference/mfc-class-wizard.md)建立對話方塊類別時，它會在您指定的 .h 和 .cpp 檔案中寫入下列專案：

在 .h 檔案中：

- 對話方塊類別的類別宣告。 類別衍生自[CDialog](reference/cdialog-class.md)。

在 .cpp 檔案中：

- 類別的訊息對應。

- 對話方塊的標準構造函式。

- [DoDataExchange](reference/cwnd-class.md#dodataexchange)成員函式的覆寫。 編輯此函式。 它用於對話方塊資料交換和驗證功能，如稍後的[對話方塊資料交換和驗證](dialog-data-exchange-and-validation.md)中所述。

## <a name="see-also"></a>另請參閱

[使用程式碼精靈建立對話方塊類別](creating-a-dialog-class-with-code-wizards.md)<br/>
[在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)

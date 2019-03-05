---
title: 建立您的對話方塊類別
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: bacedc49fcdabdd5dc7fb0f392a66afd3baadd06
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326396"
---
# <a name="creating-your-dialog-class"></a>建立您的對話方塊類別

在程式中每個對話方塊中，建立新的對話方塊類別，才能使用對話方塊資源。

[將類別加入](../ide/adding-a-class-visual-cpp.md)說明如何建立新的對話方塊類別。 當您使用 加入類別精靈建立對話方塊類別時，它會寫入下列項目。H 和。您指定的 CPP 檔案：

在中。H 檔案：

- 在對話方塊類別的類別宣告。 類別衍生自[CDialog](../mfc/reference/cdialog-class.md)。

在中。CPP 檔案：

- 此類別的訊息對應。

- 標準建構函式 對話方塊。

- 覆寫[DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)成員函式。 編輯此函式。 它用於對話方塊資料交換和驗證功能稍後所述[ 對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。

## <a name="see-also"></a>另請參閱

[使用程式碼精靈建立對話方塊類別](../mfc/creating-a-dialog-class-with-code-wizards.md)<br/>
[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

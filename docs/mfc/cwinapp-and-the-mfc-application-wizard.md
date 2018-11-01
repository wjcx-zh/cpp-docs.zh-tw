---
title: CWinApp 和 MFC 應用程式精靈
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: c659387043accbd6cdad7d5e2b97ce8bf15c6e63
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437202"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp 和 MFC 應用程式精靈

當它建立基本架構的應用程式時，MFC 應用程式精靈會宣告應用程式類別衍生自[CWinApp](../mfc/reference/cwinapp-class.md)。 MFC 應用程式精靈也會產生實作檔包含下列項目：

- 應用程式類別的訊息對應。

- 空的類別建構函式。

- 變數宣告和物件的類別。

- 標準實作您`InitInstance`成員函式。

應用程式類別會放在專案的標頭和主要的原始程式檔。 類別和建立檔案的名稱會根據您在 MFC 應用程式精靈中提供的專案名稱。 若要檢視這些類別的程式碼的最簡單方式是透過[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)。

訊息對應提供與標準實作適合許多用途，但您可以視需要修改它們。 這些實作最有趣的是`InitInstance`成員函式。 一般而言，您將加入程式碼的架構實作`InitInstance`。

## <a name="see-also"></a>另請參閱

[CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)<br/>
[可覆寫的 CWinApp 成員函式](../mfc/overridable-cwinapp-member-functions.md)<br/>
[特殊 CWinApp 服務](../mfc/special-cwinapp-services.md)


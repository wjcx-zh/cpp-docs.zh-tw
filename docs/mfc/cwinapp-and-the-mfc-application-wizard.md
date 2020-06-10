---
title: CWinApp 和 MFC 應用程式精靈
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: f57b3b2b37a97093aa6d81b59a12c8cf023e3157
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622945"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp 和 MFC 應用程式精靈

當它建立基本架構應用程式時，MFC 應用程式 Wizard 會宣告一個衍生自[CWinApp](reference/cwinapp-class.md)的應用程式類別。 MFC 應用程式 Wizard 也會產生包含下列專案的執行檔：

- 應用程式類別的訊息對應。

- 空的類別的函式。

- 宣告類別的一個和唯一一個物件的變數。

- 成員函式的標準實作為 `InitInstance` 。

應用程式類別會放在專案標頭和主要來源檔案中。 根據您在 MFC 應用程式精靈中提供的專案名稱，建立類別和檔案的名稱。 若要查看這些類別的程式碼，最簡單的方式是透過[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)。

提供的標準執行和訊息對應可供許多用途，但您可以視需要加以修改。 這些實作為最有趣的就是 `InitInstance` 成員函式。 一般來說，您會將程式碼加入至的框架執行 `InitInstance` 。

## <a name="see-also"></a>另請參閱

[CWinApp：應用程式類別](cwinapp-the-application-class.md)<br/>
[可覆寫的 CWinApp 成員函式](overridable-cwinapp-member-functions.md)<br/>
[特殊 CWinApp 服務](special-cwinapp-services.md)

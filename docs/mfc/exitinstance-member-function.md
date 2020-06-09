---
title: ExitInstance 成員函式
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: 58546d26293ad48a39a36b98ba4bfdabb68385ee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622688"
---
# <a name="exitinstance-member-function"></a>ExitInstance 成員函式

每次應用程式的複本終止時，就會呼叫[CWinApp](reference/cwinapp-class.md)類別的[ExitInstance](reference/cwinapp-class.md#exitinstance)成員函式，這通常是使用者結束應用程式的結果。

如果您需要特別清除處理，例如釋放繪圖裝置介面 (Graphics Device，GDI) 資源或解除配置程式執行期間使用的記憶體，則可以覆寫 `ExitInstance`。 不過，如文件和檢視這類標準項目的清除則是由 Framework，以及其他針對這些特定物件執行特殊清除的可覆寫函式所提供。

## <a name="see-also"></a>另請參閱

[CWinApp：應用程式類別](cwinapp-the-application-class.md)

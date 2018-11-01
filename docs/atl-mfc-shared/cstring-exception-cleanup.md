---
title: CString 例外狀況清除
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
ms.openlocfilehash: f1950553e3bf3a43f029478e00b177f5cbfe121f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492543"
---
# <a name="cstring-exception-cleanup"></a>CString 例外狀況清除

在舊版的 MFC 中，重要的是，您清除[CString](../atl-mfc-shared/reference/cstringt-class.md)之後使用的物件。 Mfc 3.0 版和更新版本，已不再需要明確清除。

在 c + + 例外狀況處理機制，MFC 現在會使用，您不必擔心清除例外狀況之後。 如需如何的描述 c + + 「 回溯 」 堆疊之後在攔截到例外狀況，請參閱 < [try、 catch 和 throw 陳述式](../cpp/try-throw-and-catch-statements-cpp.md)。 即使您使用 MFC**嘗試**/**攔截**巨集，而不是 c + + 關鍵字**試**並**攔截**，MFC 使用 c + +例外狀況機制下方，因此您仍然不需要明確清除。

## <a name="see-also"></a>另請參閱

[字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[例外狀況處理](../mfc/exception-handling-in-mfc.md)


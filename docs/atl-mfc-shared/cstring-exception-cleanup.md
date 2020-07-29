---
title: CString 例外狀況清除
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
ms.openlocfilehash: 48c8f1c0040236a4f7bf27a2d5ad985ae343c03a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222052"
---
# <a name="cstring-exception-cleanup"></a>CString 例外狀況清除

在舊版的 MFC 中，請務必在使用之後清除[CString](../atl-mfc-shared/reference/cstringt-class.md)物件。 在 MFC 版本3.0 和更新版本中，已不再需要明確清除。

在 MFC 現在使用的 c + + 例外狀況處理機制底下，您不必擔心在例外狀況之後的清除。 如需在攔截到例外狀況之後，如何「回溯」堆疊的說明，請參閱[try、catch 和 throw 語句](../cpp/try-throw-and-catch-statements-cpp.md)。 即使您使用 mfc **TRY** / **CATCH**宏，而不是 c + + 關鍵字 **`try`** 和 **`catch`** ，mfc 還是會使用下面的 c + + 例外狀況機制，因此您仍然不需要明確清除。

## <a name="see-also"></a>另請參閱

[字串（ATL/MFC）](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[例外狀況處理](../mfc/exception-handling-in-mfc.md)

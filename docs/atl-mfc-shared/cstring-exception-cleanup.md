---
title: CString 例外狀況清除
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
ms.openlocfilehash: d131ce8ebe5158d7f3a567580064068742b63707
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236624"
---
# <a name="cstring-exception-cleanup"></a>CString 例外狀況清除

在舊版的 MFC 中，重要的是，您清除[CString](../atl-mfc-shared/reference/cstringt-class.md)之後使用的物件。 Mfc 3.0 版和更新版本，已不再需要明確清除。

在C++現在會使用 MFC 的例外狀況處理機制，您就不必擔心清除例外狀況之後。 如需描述如何C++「 回溯 」 堆疊在攔截到例外狀況之後，請參閱[try、 catch 和 throw 陳述式](../cpp/try-throw-and-catch-statements-cpp.md)。 即使您使用 MFC**嘗試**/**攔截**巨集，而不是C++關鍵字**嘗試**並**攔截**，MFC 會使用C++例外狀況機制下，因此您仍然不必明確地清除。

## <a name="see-also"></a>另請參閱

[字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[例外狀況處理](../mfc/exception-handling-in-mfc.md)

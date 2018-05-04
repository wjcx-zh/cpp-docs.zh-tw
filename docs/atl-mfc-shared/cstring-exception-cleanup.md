---
title: CString 例外狀況清除 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d18d10d517a6c5b0d075a7fb0ed113448625b698
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="cstring-exception-cleanup"></a>CString 例外狀況清除
在舊版的 MFC，是非常重要的就清理[CString](../atl-mfc-shared/reference/cstringt-class.md)之後使用的物件。 Mfc 3.0 版和更新版本，已不再需要明確清除。  
  
 在 c + + 例外狀況處理機制，現在會使用 MFC，您不必擔心清理之後發生例外狀況。 如需如何的說明 c + +"會回溯 」 堆疊之後在攔截到例外狀況，請參閱[try、 catch 和 throw 陳述式](../cpp/try-throw-and-catch-statements-cpp.md)。 即使您使用 MFC**再試一次**/**攔截**巨集，而不是 c + + 關鍵字**再試一次**和**攔截**，MFC 會使用 c + +例外狀況機制，因此您仍然可以在不需要明確清除。  
  
## <a name="see-also"></a>另請參閱  
 [字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [例外狀況處理](../mfc/exception-handling-in-mfc.md)


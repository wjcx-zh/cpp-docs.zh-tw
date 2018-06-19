---
title: Windows Sockets： 轉換字串 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bad57be68ce716cddf2ce44f12e94c545a7bbfd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383756"
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets：轉換字串
本文和兩個方針手冊說明了 Windows Sockets 程式設計的幾個問題。 本文涵蓋轉換的字串。 其他問題包含在[Windows Sockets： 封鎖](../mfc/windows-sockets-blocking.md)和[Windows Sockets： 位元組順序](../mfc/windows-sockets-byte-ordering.md)。  
  
 如果您使用，或衍生自類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，您必須自行管理這些問題。 如果您使用，或衍生自類別[CSocket](../mfc/reference/csocket-class.md)，MFC 會為您管理它們。  
  
## <a name="converting-strings"></a>將字串轉換  
 如果您使用不同的寬字元格式儲存的字串，例如多位元組字元或 Unicode 設定 (MBCS) 的應用程式之間進行通訊或與下列其中一種使用 ANSI 字元字串的應用程式，您必須管理的轉換在您自己`CAsyncSocket`。 `CArchive`物件搭配`CSocket`物件管理這項轉換為您透過功能類別的[CString](../atl-mfc-shared/reference/cstringt-class.md)。 如需詳細資訊，請參閱 Windows Sockets 規格，位於 Windows SDK。  
  
 如需詳細資訊，請參閱:  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>另請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)


---
title: Windows Sockets： 轉換字串 |Microsoft Docs
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
ms.openlocfilehash: 6b23d2149659cdad320a58bdff0f42ba113b5696
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378932"
---
# <a name="windows-sockets-converting-strings"></a>Windows Sockets：轉換字串

本文和兩個方針手冊說明了 Windows Sockets 程式設計的幾個問題。 本文章涵蓋將字串轉換。 其他問題所述[Windows Sockets： 封鎖](../mfc/windows-sockets-blocking.md)並[Windows Sockets： 位元組順序](../mfc/windows-sockets-byte-ordering.md)。

如果您使用或衍生自類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，您必須自行管理這些問題。 如果您使用或衍生自類別[CSocket](../mfc/reference/csocket-class.md)，MFC 會為您管理它們。

## <a name="converting-strings"></a>將字串轉換

如果您使用儲存在不同的寬字元格式的字串，例如 Unicode 或多位元組字元設定 (MBCS) 的應用程式之間進行通訊，或其中一個應用程式和之間使用 ANSI 字元字串，您必須管理的轉換在您自己`CAsyncSocket`。 `CArchive`搭配使用的物件`CSocket`物件會管理這項轉換為您透過功能的類別[CString](../atl-mfc-shared/reference/cstringt-class.md)。 如需詳細資訊，請參閱 Windows Sockets 規格，位於 Windows SDK。

如需詳細資訊，請參閱:

- [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets：搭配使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets：背景](../mfc/windows-sockets-background.md)

- [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>另請參閱

[MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)


---
title: Windows Sockets 類別
ms.date: 11/04/2016
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 3f1b7b2b6674b4a5f8c8f7bff6c5fa239715f459
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445978"
---
# <a name="windows-sockets-classes"></a>Windows Sockets 類別

Windows Sockets 提供一個與網路通訊協定無關的方法，可在兩部電腦之間溝通。 這些通訊端可以是同步 (您的程式會等待直到完成通訊) 或非同步 (您的程式在通訊進行時會繼續執行)。

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
在精簡型包裝函式中封裝 Windows Sockets API。

[CSocket](../mfc/reference/csocket-class.md)<br/>
從 `CAsyncSocket` 衍生的較高層級抽象。 它會以同步方式進行作業。

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
提供 `CFile` 介面給 Windows Socket。

## <a name="see-also"></a>另請參閱

[類別總覽](../mfc/class-library-overview.md)

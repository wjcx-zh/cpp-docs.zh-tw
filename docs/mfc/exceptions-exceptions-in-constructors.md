---
title: '例外狀況: 建構函式中的例外狀況'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 0b11f5be18879d5ad4b9e204bb02e18b4617c6b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405868"
---
# <a name="exceptions-exceptions-in-constructors"></a>例外狀況: 建構函式中的例外狀況

當擲回例外狀況的建構函式中，清除任何物件和記憶體配置進行之前擲回的例外狀況中所述[例外狀況：從您自己的函式擲回例外狀況](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)。

如果建構函式擲回例外狀況，表示呼叫建構函式時已經配置物件本身的記憶體。 因此，在擲回例外狀況之後，編譯器將會自動解除配置物件所佔用的記憶體。

如需詳細資訊，請參閱[例外狀況：釋放例外狀況中的物件](../mfc/exceptions-freeing-objects-in-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)

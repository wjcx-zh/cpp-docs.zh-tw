---
title: 例外狀況：建構函式中的例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 23d1f6a9a3c76cc9c0c1d4aebd5c0b0ea45c3154
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472263"
---
# <a name="exceptions-exceptions-in-constructors"></a>例外狀況：建構函式中的例外狀況

當擲回例外狀況的建構函式中，清除任何物件和記憶體配置進行之前擲回的例外狀況中所述[例外狀況： 從您的函式擲回的例外狀況](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)。

如果建構函式擲回例外狀況，表示呼叫建構函式時已經配置物件本身的記憶體。 因此，在擲回例外狀況之後，編譯器將會自動解除配置物件所佔用的記憶體。

如需詳細資訊，請參閱 <<c0> [ 例外狀況： 例外狀況時釋放物件](../mfc/exceptions-freeing-objects-in-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)


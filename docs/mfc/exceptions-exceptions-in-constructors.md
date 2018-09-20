---
title: 例外狀況： 建構函式中例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cab21255698c19046cfca185a0d8d7e7c530112
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421930"
---
# <a name="exceptions-exceptions-in-constructors"></a>例外狀況：建構函式中的例外狀況

當擲回例外狀況的建構函式中，清除任何物件和記憶體配置進行之前擲回的例外狀況中所述[例外狀況： 從您的函式擲回的例外狀況](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)。

如果建構函式擲回例外狀況，表示呼叫建構函式時已經配置物件本身的記憶體。 因此，在擲回例外狀況之後，編譯器將會自動解除配置物件所佔用的記憶體。

如需詳細資訊，請參閱 <<c0> [ 例外狀況： 例外狀況時釋放物件](../mfc/exceptions-freeing-objects-in-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)


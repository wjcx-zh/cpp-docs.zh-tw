---
title: 例外狀況：建構函式中的例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 4089f4d44f03c7de3432f137b5d28f74189e1cb9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624620"
---
# <a name="exceptions-exceptions-in-constructors"></a>例外狀況：建構函式中的例外狀況

在函式中擲回例外狀況時，請清除您在擲回例外狀況之前所做的任何物件和記憶體配置，如[例外狀況：從您自己](exceptions-throwing-exceptions-from-your-own-functions.md)的函式擲回例外狀況中所述。

如果建構函式擲回例外狀況，表示呼叫建構函式時已經配置物件本身的記憶體。 因此，在擲回例外狀況之後，編譯器將會自動解除配置物件所佔用的記憶體。

如需詳細資訊，請參閱[例外狀況：釋放例外狀況中的物件](exceptions-freeing-objects-in-exceptions.md)。

## <a name="see-also"></a>另請參閱

[例外狀況處理](exception-handling-in-mfc.md)

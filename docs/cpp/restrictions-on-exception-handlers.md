---
title: 例外狀況處理常式的限制
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 1f80cb1574cbfef0783c7e55dcd198dfb822f566
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225900"
---
# <a name="restrictions-on-exception-handlers"></a>例外狀況處理常式的限制

在程式碼中使用例外狀況處理常式的主要限制是，您無法使用 **`goto`** 語句跳至 **__try**語句區塊。 您必須改為透過一般控制流程進入陳述式區塊。 您可以從 **__try**語句區塊跳出，並在選擇時將例外狀況處理常式加以擴展。

## <a name="see-also"></a>另請參閱

[撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

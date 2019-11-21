---
title: 例外狀況處理常式的限制
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 030d444443b3a6e3e2e0ac0e015619046a76d562
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245150"
---
# <a name="restrictions-on-exception-handlers"></a>例外狀況處理常式的限制

The principal limitation to using exception handlers in code is that you cannot use a **goto** statement to jump into a **__try** statement block. 您必須改為透過一般控制流程進入陳述式區塊。 You can jump out of a **__try** statement block and nest exception handlers as you choose.

## <a name="see-also"></a>請參閱

[撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
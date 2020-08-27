---
title: 例外狀況處理常式的限制
description: 描述跳入結構化例外狀況處理區塊的限制。
ms.date: 08/24/2020
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: c4182f065789533bf7599621d8d2829b2d52d6ed
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898443"
---
# <a name="restrictions-on-exception-handlers"></a>例外狀況處理常式的限制

在程式碼中使用例外狀況處理常式的主要限制是，您不能使用 **`goto`** 語句跳入 **`__try`** 語句區塊。 您必須改為透過一般控制流程進入陳述式區塊。 您可以跳出 **`__try`** 語句區塊，也可以依您的選擇來嵌套例外狀況處理常式。

## <a name="see-also"></a>請參閱

[撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

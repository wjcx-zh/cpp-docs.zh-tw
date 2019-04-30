---
title: 例外狀況處理常式的限制
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 7d5bf20da61f4b9f5012b7f2aab932dfc904c302
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403356"
---
# <a name="restrictions-on-exception-handlers"></a>例外狀況處理常式的限制

程式碼中使用例外狀況處理常式的主要限制是，您無法使用**goto**陳述式跳入 **__try**陳述式區塊。 您必須改為透過一般控制流程進入陳述式區塊。 您可以跳出 **__try**陳述式區塊和巢狀例外狀況處理常式，如您所選擇。

## <a name="see-also"></a>另請參閱

[撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
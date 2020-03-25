---
title: 例外狀況處理常式的限制
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 54bf4a44d06eacd22dc4b9819d160d3c6a66c684
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179077"
---
# <a name="restrictions-on-exception-handlers"></a>例外狀況處理常式的限制

在程式碼中使用例外狀況處理常式的主要限制是，您無法使用**goto**語句跳至 **__try**語句區塊。 您必須改為透過一般控制流程進入陳述式區塊。 您可以從 **__try**語句區塊跳出，並在選擇時將例外狀況處理常式加以擴展。

## <a name="see-also"></a>另請參閱

[撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

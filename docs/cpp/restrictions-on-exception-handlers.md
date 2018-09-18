---
title: 例外狀況處理常式的限制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29a462f83bff3bab158e9bcf9fa7947efb56a79b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074470"
---
# <a name="restrictions-on-exception-handlers"></a>例外狀況處理常式的限制

程式碼中使用例外狀況處理常式的主要限制是，您無法使用**goto**陳述式跳入 **__try**陳述式區塊。 您必須改為透過一般控制流程進入陳述式區塊。 您可以跳出 **__try**陳述式區塊和巢狀例外狀況處理常式，如您所選擇。

## <a name="see-also"></a>另請參閱

[撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
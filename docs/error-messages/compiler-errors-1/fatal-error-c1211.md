---
title: 嚴重錯誤 C1211 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1211
dev_langs:
- C++
helpviewer_keywords:
- C1211
ms.assetid: df0ca70d-ec6e-4400-926a-b877e2599978
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 444d2bc25c2eddd5ea9a0170272bd3e71b61f94f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018520"
---
# <a name="fatal-error-c1211"></a>嚴重錯誤 C1211

所安裝的 執行階段版本不支援 TypeForwardedTo 自訂屬性

如果您有目前版本的編譯器，但 Common Language Runtime 來自舊版本，就會發生 C1211。

編譯器的某個功能可能無法在執行階段的舊版本上運作。

若要解決 C1211，請安裝所使用編譯器隨附的 Common Language Runtime。

如需詳細資訊，請參閱 <<c0> [ 型別轉送 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)。
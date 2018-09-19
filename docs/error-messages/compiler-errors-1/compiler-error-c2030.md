---
title: 編譯器錯誤 C2030 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2030
dev_langs:
- C++
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0c5849c372cc4c7ebf27dbe010e65d406ad1ab1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032889"
---
# <a name="compiler-error-c2030"></a>編譯器錯誤 C2030

具有 'protected private' 可及性的解構函式不可以是宣告為 'sealed' 之類別的成員

宣告為 `sealed` 的 Windows 執行階段類別不能有受保護的私用解構函式。 sealed 類型只允許公用虛擬和私用非虛擬解構函式。 如需詳細資訊，請參閱 < [Ref 類別與結構](../../cppcx/ref-classes-and-structs-c-cx.md)。

若要修正這個錯誤，請變更解構函式的存取範圍。
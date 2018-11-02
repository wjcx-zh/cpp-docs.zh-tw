---
title: 編譯器錯誤 C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: 217f97d205e1da075277b8b0bc22ff3baab13482
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602172"
---
# <a name="compiler-error-c2030"></a>編譯器錯誤 C2030

具有 'protected private' 可及性的解構函式不可以是宣告為 'sealed' 之類別的成員

宣告為 `sealed` 的 Windows 執行階段類別不能有受保護的私用解構函式。 sealed 類型只允許公用虛擬和私用非虛擬解構函式。 如需詳細資訊，請參閱 < [Ref 類別與結構](../../cppcx/ref-classes-and-structs-c-cx.md)。

若要修正這個錯誤，請變更解構函式的存取範圍。
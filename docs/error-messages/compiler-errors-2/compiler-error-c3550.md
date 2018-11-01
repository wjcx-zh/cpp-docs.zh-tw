---
title: 編譯器錯誤 C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: dbed14b9f2fa0f2163484edd8b5dfa330af9cbf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498870"
---
# <a name="compiler-error-c3550"></a>編譯器錯誤 C3550

此內容中不得有純 'decltype(auto)'

如果 `decltype(auto)` 做為函式傳回型別的預留位置，則必須由本身使用。 它不能在指標宣告 (`decltype(auto*)`)、參考宣告 (`decltype(auto&)`) 或任何其他這類限定性條件中使用。

## <a name="see-also"></a>另請參閱

[auto](../../cpp/auto-cpp.md)
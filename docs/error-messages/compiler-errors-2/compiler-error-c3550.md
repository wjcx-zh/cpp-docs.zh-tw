---
title: 編譯器錯誤 C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 106ac93496eebb25ee603251d84680053e1310b7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032330"
---
# <a name="compiler-error-c3550"></a>編譯器錯誤 C3550

此內容中不得有純 'decltype(auto)'

如果 `decltype(auto)` 做為函式傳回型別的預留位置，則必須由本身使用。 它不能在指標宣告 (`decltype(auto*)`)、參考宣告 (`decltype(auto&)`) 或任何其他這類限定性條件中使用。

## <a name="see-also"></a>另請參閱

[auto](../../cpp/auto-cpp.md)
---
title: 編譯器錯誤 C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 106ac93496eebb25ee603251d84680053e1310b7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032330"
---
# <a name="compiler-error-c3550"></a>編譯器錯誤 C3550

此內容中不得有純 'decltype(auto)'

如果 `decltype(auto)` 做為函式傳回型別的預留位置，則必須由本身使用。 它不能在指標宣告 (`decltype(auto*)`)、參考宣告 (`decltype(auto&)`) 或任何其他這類限定性條件中使用。

## <a name="see-also"></a>另請參閱

[auto](../../cpp/auto-cpp.md)
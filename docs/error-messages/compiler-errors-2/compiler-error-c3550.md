---
title: 編譯器錯誤 C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 17c90aa68b29c9490deb8d49895162e8a6bdefec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200768"
---
# <a name="compiler-error-c3550"></a>編譯器錯誤 C3550

此內容中不得有純 'decltype(auto)'

如果 `decltype(auto)` 做為函式傳回型別的預留位置，則必須由本身使用。 它不能在指標宣告 (`decltype(auto*)`)、參考宣告 (`decltype(auto&)`) 或任何其他這類限定性條件中使用。

## <a name="see-also"></a>另請參閱

[auto](../../cpp/auto-cpp.md)

---
title: nullptr
ms.date: 07/22/2020
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 801ae927d6c9fb70c3187d10269e87097a879bfc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223625"
---
# <a name="nullptr"></a>nullptr

**`nullptr`** 關鍵字會指定類型為的 null 指標常數 `std::nullptr_t` ，這會轉換成任何原始指標類型。  雖然您可以使用關鍵字 **`nullptr`** ，而不包含任何標頭，但如果您的程式碼使用類型 `std::nullptr_t` ，則必須包含標頭來定義它 `<cstddef>` 。

> [!NOTE]
> **`nullptr`** 關鍵字也是在 managed 程式碼應用程式的 c + +/cli 中定義，而且無法與 ISO Standard c + + 關鍵字互換。 如果您的程式碼可能會使用 [`/clr`](../build/reference/clr-common-language-runtime-compilation.md) 以 managed 程式碼為目標的編譯器選項進行編譯，則請 `__nullptr` 在任何行程式碼中使用，您必須保證編譯器會使用原生 c + + 轉譯。 如需詳細資訊，請參閱[ `nullptr` （c + +/cli 和 c + +/cx）](../extensions/nullptr-cpp-component-extensions.md)。

## <a name="remarks"></a>備註

請避免使用 `NULL` 或零（ `0` ）做為 null 指標常數; **`nullptr`** 較不容易誤用，而且在大部分情況下效果較佳。  例如，若使用 `func(std::pair<const char *, double>)`，呼叫 `func(std::make_pair(NULL, 3.14))` 就會造成編譯器錯誤。  宏 `NULL` 會展開為 `0` ，因此呼叫會傳回 `std::make_pair(0, 3.14)` `std::pair<int, double>` ，而這無法轉換成 `std::pair<const char *, double>` 中的參數類型 `func` 。  呼叫 `func(std::make_pair(nullptr, 3.14))` 可以成功編譯，因為 `std::make_pair(nullptr, 3.14)` 會傳回 `std::pair<std::nullptr_t, double>` (可轉換為 `std::pair<const char *, double>`)。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[`nullptr`（C + +/CLI 和 c + +/CX）](../extensions/nullptr-cpp-component-extensions.md)

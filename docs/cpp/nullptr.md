---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 223f4c3e8c838698f9716e241543db405c9394af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177764"
---
# <a name="nullptr"></a>nullptr

指定類型為 `std::nullptr_t` 的 Null 指標常數，此指標常數可以轉換成任何原始指標類型。  雖然您可以使用關鍵字**nullptr**而不包含任何標頭，但如果您的程式碼使用類型 `std::nullptr_t`，則您必須包含標頭 `<cstddef>`來定義它。

> [!NOTE]
>  **Nullptr**關鍵字也是在/cli 中C++針對受控碼應用程式定義，而且無法與 ISO Standard C++關鍵字互換。 如果您的程式碼可能會使用以 managed 程式碼為目標的[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項進行編譯，則請在任何程式碼中使用 `__nullptr`，您必須保證編譯器會C++使用原生轉譯。 如需詳細資訊，請參閱[nullptr](../extensions/nullptr-cpp-component-extensions.md)。

## <a name="remarks"></a>備註

避免使用 Null 或零（`0`）做為 null 指標常數;**nullptr**較不容易被誤用，而且在大部分的情況下效果更好。  例如，若使用 `func(std::pair<const char *, double>)`，呼叫 `func(std::make_pair(NULL, 3.14))` 就會造成編譯器錯誤。  巨集 NULL 會展開為 `0`，因此呼叫 `std::make_pair(0, 3.14)` 會傳回 `std::pair<int, double>` (不可轉換為 func() 的 `std::pair<const char *, double>` 參數類型)。  呼叫 `func(std::make_pair(nullptr, 3.14))` 可以成功編譯，因為 `std::make_pair(nullptr, 3.14)` 會傳回 `std::pair<std::nullptr_t, double>` (可轉換為 `std::pair<const char *, double>`)。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)（C++/cli）

---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 51df20ea00e5dd77ab1fc1a2a01253b8f788ad0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358846"
---
# <a name="nullptr"></a>nullptr

指定類型為 `std::nullptr_t` 的 Null 指標常數，此指標常數可以轉換成任何原始指標類型。  儘管可以使用關鍵字**nullptr**而不包括任何標頭,但如果代碼`std::nullptr_t`使用 類型 ,則必須`<cstddef>`通過包括標頭 來定義它。

> [!NOTE]
> **nullptr**關鍵字也C++/CLI 中為託管代碼應用程式定義,不能與 ISO 標準C++關鍵字互換。 如果代碼可能使用以託管代碼為目標的[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項進行編譯,則在`__nullptr`任何代碼行中使用,其中必須保證編譯器使用本機C++解釋。 有關詳細資訊,請參閱[nullptr](../extensions/nullptr-cpp-component-extensions.md)。

## <a name="remarks"></a>備註

避免使用 NULL`0`或零 ( ) 作為空指標常量;**在大多數情況下,空位**不易被誤用,效果更好。  例如，若使用 `func(std::pair<const char *, double>)`，呼叫 `func(std::make_pair(NULL, 3.14))` 就會造成編譯器錯誤。  巨集 NULL 會展開為 `0`，因此呼叫 `std::make_pair(0, 3.14)` 會傳回 `std::pair<int, double>` (不可轉換為 func() 的 `std::pair<const char *, double>` 參數類型)。  呼叫 `func(std::make_pair(nullptr, 3.14))` 可以成功編譯，因為 `std::make_pair(nullptr, 3.14)` 會傳回 `std::pair<std::nullptr_t, double>` (可轉換為 `std::pair<const char *, double>`)。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[空值](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)

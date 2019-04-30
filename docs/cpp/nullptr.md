---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 57be8d71f1dac4f347ea6567c02a385719bb7306
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403486"
---
# <a name="nullptr"></a>nullptr

指定類型為 `std::nullptr_t` 的 Null 指標常數，此指標常數可以轉換成任何原始指標類型。  雖然您可以使用關鍵字**nullptr**不含任何標頭中，如果您的程式碼會使用型別`std::nullptr_t`，則您必須定義它所包含的標頭`<cstddef>`。

> [!NOTE]
>  **Nullptr**關鍵字也會定義在C++/適用於 CLI 管理程式碼應用程式，而且不能互換使用 ISO 標準C++關鍵字。 如果您的程式碼可以使用編譯[/clr](../build/reference/clr-common-language-runtime-compilation.md)編譯器選項，以 managed 程式碼為目標，然後使用`__nullptr`中任何一行程式碼，您必須保證編譯器會使用原生C++解譯。 如需詳細資訊，請參閱 < [nullptr](../extensions/nullptr-cpp-component-extensions.md)。

## <a name="remarks"></a>備註

請避免使用 NULL 或零 (`0`) 為 null 指標常數;**nullptr**比較不容易誤用，而且在大部分情況下，效果更好。  例如，若使用 `func(std::pair<const char *, double>)`，呼叫 `func(std::make_pair(NULL, 3.14))` 就會造成編譯器錯誤。  巨集 NULL 會展開為 `0`，因此呼叫 `std::make_pair(0, 3.14)` 會傳回 `std::pair<int, double>` (不可轉換為 func() 的 `std::pair<const char *, double>` 參數類型)。  呼叫 `func(std::make_pair(nullptr, 3.14))` 可以成功編譯，因為 `std::make_pair(nullptr, 3.14)` 會傳回 `std::pair<std::nullptr_t, double>` (可轉換為 `std::pair<const char *, double>`)。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)
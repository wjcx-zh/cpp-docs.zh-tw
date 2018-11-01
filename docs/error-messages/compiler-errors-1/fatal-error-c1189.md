---
title: 嚴重錯誤 C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 06d42316a0109ac063bba43cefebd9aab71c2e72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565525"
---
# <a name="fatal-error-c1189"></a>嚴重錯誤 C1189

> **\#錯誤：** *使用者提供錯誤訊息*

## <a name="remarks"></a>備註

產生 「 C1189`#error`指示詞。 開發人員程式碼指示詞指定的錯誤訊息的文字。 如需詳細資訊，請參閱 < [#error 指示詞 （C/c + +）](../../preprocessor/hash-error-directive-c-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 「 C1189。 在範例中，開發人員問題的自訂錯誤訊息因為`_WIN32`未定義識別項：

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>另請參閱

[#define 指示詞 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
---
title: 嚴重錯誤 C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 2217b865109cc48151e4e96b2d38b88764c0c64f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203621"
---
# <a name="fatal-error-c1189"></a>嚴重錯誤 C1189

> **\#錯誤：** *使用者提供的錯誤訊息*

## <a name="remarks"></a>備註

C1189 是由 `#error` 指示詞所產生。 編碼指示詞的開發人員會指定錯誤訊息的文字。 如需詳細資訊，請參閱[#error 指示詞C++（C/）](../../preprocessor/hash-error-directive-c-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C1189。 在範例中，因為未定義 `_WIN32` 識別碼，所以開發人員會發出自訂錯誤訊息：

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>另請參閱

[#define 指示詞 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)

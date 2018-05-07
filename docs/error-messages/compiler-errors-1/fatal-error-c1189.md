---
title: 嚴重錯誤 C1189 |Microsoft 文件
ms.custom: ''
ms.date: 04/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1189
dev_langs:
- C++
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 051b7eb965526d12311dfacaeae7a00e4fbe4e75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1189"></a>嚴重錯誤 C1189

> **\#錯誤：** *使用者提供錯誤訊息*

## <a name="remarks"></a>備註

所產生 C1189`#error`指示詞。 開發人員碼指示詞指定的錯誤訊息的文字。 如需詳細資訊，請參閱[#error 指示詞 （C/c + +）](../../preprocessor/hash-error-directive-c-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C1189。 在範例中，開發人員會發出自訂錯誤訊息因為`_WIN32`未定義識別項：

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>另請參閱

[#define 指示詞 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
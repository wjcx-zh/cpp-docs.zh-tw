---
title: 嚴重錯誤 C1189 |Microsoft 文件
ms.custom: ''
ms.date: 04/27/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C1189
dev_langs:
- C++
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b49f227b5fda20ab0ba202d3d7eca99492509b35
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
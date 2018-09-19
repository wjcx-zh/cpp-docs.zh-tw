---
title: 編譯器錯誤 C3163 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3163
dev_langs:
- C++
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e712a70bdd443d9a6c640853b958f29dac78dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061964"
---
# <a name="compiler-error-c3163"></a>編譯器錯誤 C3163

'construct': 屬性與先前的宣告不一致

套用至定義的屬性會套用至宣告之屬性與衝突。

解決 C3163 方法之一就是消除上向前宣告的屬性。 向前宣告上的任何屬性，應該小於上定義的屬性或者，最多可以等於給它們。

C3163 錯誤的可能原因包括 Microsoft 原始程式碼註釋語言 (SAL)。 除非您使用編譯您的專案，否則 SAL 巨集不要展開 **/analyze**旗標。 順利進行編譯而不需要 / 分析的程式可能會擲回 C3163，如果您嘗試重新編譯使用 /analyze 選項。 如需 SAL 的詳細資訊，請參閱[SAL 註釋](../../c-runtime-library/sal-annotations.md)。

## <a name="example"></a>範例

下列範例會產生 C3163。

```
// C3163.cpp
// compile with: /clr /c
using namespace System;

[CLSCompliant(true)] void f();
[CLSCompliant(false)] void f() {}   // C3163
// try the following line instead
// [CLSCompliant(true)] void f() {}
```

## <a name="see-also"></a>另請參閱

[SAL 註釋](../../c-runtime-library/sal-annotations.md)
---
title: 編譯器錯誤 C3699 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3699
dev_langs:
- C++
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64e5a5bb98f9e8a6950bbb279c026f167a2ee92e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107703"
---
# <a name="compiler-error-c3699"></a>編譯器錯誤 C3699

'operator': 類型 'type' 上無法使用這個間接取值

嘗試使用不允許的間接取值`type`。

## <a name="example"></a>範例

下列範例會產生 C3699。

```
// C3699.cpp
// compile with: /clr /c
using namespace System;
int main() {
   String * s;   // C3699
   // try the following line instead
   // String ^ s2;
}
```

## <a name="example"></a>範例

Trivial 屬性不能有參考類型。 如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md) 。 下列範例會產生 C3699。

```
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>範例

相當於"指標的指標 」 語法是追蹤參考的控制代碼。 下列範例會產生 C3699。

```
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```
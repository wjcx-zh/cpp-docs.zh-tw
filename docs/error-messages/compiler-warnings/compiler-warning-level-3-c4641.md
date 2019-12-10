---
title: 編譯器警告 (層級 3) C4641
ms.date: 11/04/2016
f1_keywords:
- C4641
helpviewer_keywords:
- C4641
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
ms.openlocfilehash: 1e3eab6e96e829e3c3fd9304e757ba653e8f19b4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991814"
---
# <a name="compiler-warning-level-3-c4641"></a>編譯器警告 (層級 3) C4641

XML 文件註解有模稜兩可的交互參考

編譯器無法明確解析參考。 若要解決此警告，請指定明確參考所需的參數資訊。

如需詳細資訊，請參閱 [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C4641。

```cpp
// C4641.cpp
// compile with: /W3 /doc /clr /c

/// <see cref="f" />   // C4641
// try the following line instead
// /// <see cref="f(int)" />
public ref class GR {
public:
   void f( int ) {}
   void f( char ) {}
};
```

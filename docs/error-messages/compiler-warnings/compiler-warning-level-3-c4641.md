---
title: 編譯器警告 (層級 3) C4641
ms.date: 11/04/2016
f1_keywords:
- C4641
helpviewer_keywords:
- C4641
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
ms.openlocfilehash: 9357088106a45026eae543f8627ea59988e73995
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818501"
---
# <a name="compiler-warning-level-3-c4641"></a>編譯器警告 (層級 3) C4641

XML 文件註解有模稜兩可的交互參考

編譯器無法明確地解析的參考。 若要解決這個警告，指定參數所需的資訊，讓參考模稜兩可。

如需詳細資訊，請參閱 [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C4641。

```
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
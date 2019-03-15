---
title: 編譯器警告 (層級 4) C4634
ms.date: 11/04/2016
f1_keywords:
- C4634
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
ms.openlocfilehash: 7d0e2af13128a201d96aa905d85621e14441a673
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818254"
---
# <a name="compiler-warning-level-4-c4634"></a>編譯器警告 (層級 4) C4634

XML 文件註解: 無法套用: 原因

XML 文件標記無法套用至所有 C++ 建構。  例如，您無法將文件註解加入命名空間或範本。

如需詳細資訊，請參閱 [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C4634。

```
// C4634.cpp
// compile with: /W4 /doc /c
/// This is a namespace.   // C4634
namespace hello {
   class MyClass  {};
};
```

## <a name="example"></a>範例

下列範例會產生 C4634。

```
// C4634_b.cpp
// compile with: /W4 /doc /c
/// This is a template.   // C4634
template <class T>
class MyClass  {};
```
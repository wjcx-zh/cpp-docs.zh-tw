---
title: 編譯器錯誤 C3075
ms.date: 11/04/2016
f1_keywords:
- C3075
helpviewer_keywords:
- C3075
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
ms.openlocfilehash: 0494961b47e99ce1f3e559302aff56278098a912
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406713"
---
# <a name="compiler-error-c3075"></a>編譯器錯誤 C3075

'instance' : 不可將參考類型的執行個體 'type' 嵌入實值類型中

實值類型不能包含參考類型的執行個體。

如需詳細資訊，請參閱 < [ C++的參考型別堆疊語意](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="example"></a>範例

下列範例會產生 C3075。

```
// C3075.cpp
// compile with: /clr /c
ref struct U {};
value struct X {
   U y;   // C3075
};

ref struct Y {
   U y;   // OK
};
```
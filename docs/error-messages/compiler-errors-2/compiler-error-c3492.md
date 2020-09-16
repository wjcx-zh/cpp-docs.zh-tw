---
title: 編譯器錯誤 C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: bdaeb8797eb71b205f737d08e74430f161cb8caa
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686544"
---
# <a name="compiler-error-c3492"></a>編譯器錯誤 C3492

'var': 您無法擷取匿名等位的成員

您無法擷取未命名等位的成員。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 為等位命名，並將完整的等位結構傳遞至 Lambda 運算式的擷取清單。

## <a name="examples"></a>範例

下列範例會產生 C3492，因為它會擷取匿名等位的成員：

```cpp
// C3492a.cpp

int main()
{
   union
   {
      char ch;
      int x;
   };

   ch = 'y';
   [&x](char ch) { x = ch; }(ch); // C3492
}
```

下列範例透過為等位命名，並將完整的等位結構傳遞至 Lambda 運算式的擷取清單，來解決 C3492：

```cpp
// C3492b.cpp

int main()
{
   union
   {
      char ch;
      int x;
   } u;

   u.ch = 'y';
   [&u](char ch) { u.x = ch; }(u.ch);
}
```

## <a name="see-also"></a>另請參閱

[Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)

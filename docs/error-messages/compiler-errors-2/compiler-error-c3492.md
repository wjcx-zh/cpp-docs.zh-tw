---
title: 編譯器錯誤 C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: facd8c78e775945924d77b09f9dc754bdc301ddd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038815"
---
# <a name="compiler-error-c3492"></a>編譯器錯誤 C3492

'var': 您無法擷取匿名等位的成員

您無法擷取未命名等位的成員。

### <a name="to-correct-this-error"></a>更正這個錯誤

- 為等位命名，並將完整的等位結構傳遞至 Lambda 運算式的擷取清單。

## <a name="example"></a>範例

下列範例會產生 C3492，因為它會擷取匿名等位的成員：

```
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

## <a name="example"></a>範例

下列範例透過為等位命名，並將完整的等位結構傳遞至 Lambda 運算式的擷取清單，來解決 C3492：

```
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
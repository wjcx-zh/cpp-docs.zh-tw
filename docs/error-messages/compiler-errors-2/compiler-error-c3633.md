---
title: 編譯器錯誤 C3633
ms.date: 11/04/2016
f1_keywords:
- C3633
helpviewer_keywords:
- C3633
ms.assetid: 7d65babf-2191-4d67-a69f-f5c4c2ddf946
ms.openlocfilehash: 2d96a0e4f5f0b34c76f41058316c7f158f1a939d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385702"
---
# <a name="compiler-error-c3633"></a>編譯器錯誤 C3633

無法為受管理的 'type' 的成員定義 'member'

CLR 參考類別資料成員不可為非 POD + + 類型。  您可以只具現化 CLR 型別中的 POD 原生型別。  比方說，是 POD 類型不能包含複製建構函式或指派運算子。

## <a name="example"></a>範例

下列範例會產生 C3633。

```
// C3633.cpp
// compile with: /clr /c
#pragma warning( disable : 4368 )

class A1 {
public:
   A1() { II = 0; }
   int II;
};

ref class B {
public:
   A1 a1;   // C3633
   A1 * a2;   // OK
   B() : a2( new A1 ) {}
    ~B() { delete a2; }
};
```

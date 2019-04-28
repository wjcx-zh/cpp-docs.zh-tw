---
title: 連結器工具警告 LNK4248
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: db9432c505b7348c9bef5ed34aac1cb4edecb17b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352513"
---
# <a name="linker-tools-warning-lnk4248"></a>連結器工具警告 LNK4248

無法解析的 typeref 語彙基元 (token) 的 'type';映像可能無法執行

類型沒有定義 MSIL 中繼資料。

僅向前宣告中的 MSIL 模組的型別時，可能會發生 LNK4248 (編譯 **/clr**)，其中型別參考在 MSIL 模組中，而且 MSIL 模組與已定義的原生模組連結型別。

在此情況下，連結器會提供原生型別定義在 MSIL 中繼資料，，，這可能會提供正確的行為。

不過，如果 CLR 型別轉送類型宣告，然後連結器的原生型別定義可能不正確

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 提供的類型定義中的 MSIL 模組。

## <a name="example"></a>範例

下列範例會產生 LNK4248。 定義結構的解析。

```
// LNK4248.cpp
// compile with: /clr /W1
// LNK4248 expected
struct A;
void Test(A*){}

int main() {
   Test(0);
}
```

## <a name="example"></a>範例

下列範例已轉送的類型定義。

```
// LNK4248_2.cpp
// compile with: /clr /c
class A;   // provide a definition for A here to resolve
A * newA();
int valueA(A * a);

int main() {
   A * a = newA();
   return valueA(a);
}
```

## <a name="example"></a>範例

下列範例會產生 LNK4248。

```
// LNK4248_3.cpp
// compile with: /c
// post-build command: link LNK4248_2.obj LNK4248_3.obj
class A {
public:
   int b;
};

A* newA() {
   return new A;
}

int valueA(A * a) {
   return (int)a;
}
```
---
title: 編譯器錯誤 C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: 3a0fd9c49a71f6f53d1a109378e3a6894bb68723
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175418"
---
# <a name="compiler-error-c2146"></a>編譯器錯誤 C2146

語法錯誤： 遺漏 'token' 識別項 'identifier' 之前

編譯器預期`token`找到`identifier`改。  可能的原因：

1. 拼字檢查或大小寫錯誤。

1. 在識別項的宣告中遺漏類型規範。

此錯誤可能被因印刷錯誤。 錯誤[C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md)通常前面出現此錯誤。

## <a name="example"></a>範例

下列範例會產生 C2146。

```
// C2146.cpp
class CDeclaredClass {};

class CMyClass {
   CUndeclared m_myClass;   // C2146
   CDeclaredClass m_myClass2;   // OK
};

int main() {
   int x;
   int t x;   // C2146 : missing semicolon before 'x'
}
```

## <a name="example"></a>範例

也可因為針對 Visual Studio.NET 2003年所進行的編譯器一致性處理而產生這個錯誤： 遺漏`typename`關鍵字。

下列範例是在 Visual Studio.NET 2002年中編譯，但在 Visual Studio.NET 2003年中將會失敗：

```
// C2146b.cpp
// compile with: /c
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};

template <typename T>
X<T>::Y func() { }   // C2146

// OK
template <typename T>
typename X<T>::Y func() { }
```

## <a name="example"></a>範例

您也會看到此錯誤，因為針對 Visual Studio.NET 2003年所進行的編譯器一致性處理而： 明確特製化不會再找出從主要範本的範本參數。

使用`T`從主要範本中不允許明確的特製化。 在 視覺效果的 Visual Studio.NET 2003年和 Visual Studio.NET 版本中是有效的程式碼C++，在特製化的範本參數的所有執行個體取代的明確特製化的型別。

下列範例是在 Visual Studio.NET 中編譯，但在 Visual Studio.NET 2003年中將會失敗：

```
// C2146_c.cpp
// compile with: /c
template <class T>
struct S;

template <>
struct S<int> {
   T m_t;   // C2146
   int m_t2;   // OK
};
```
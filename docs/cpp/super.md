---
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: 3afc2e8049cfcca40db389bed84baa6f42dae126
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213147"
---
# `__super`

**Microsoft 特定的**

可讓您明確陳述您要呼叫將覆寫之函式的基底類別實作。

## <a name="syntax"></a>語法

```
__super::member_function();
```

## <a name="remarks"></a>備註

多載解析階段會考量所有可存取的基底類別方法，並且提供最佳相符結果的函式即為將會呼叫的函式。

**`__super`** 只能出現在成員函式的主體內。

**`__super`** 不能與 using 宣告搭配使用。 如需詳細資訊，請參閱[using](../cpp/using-declaration.md)宣告。

隨著引入了插入程式碼的[屬性](../windows/attributes/attributes-alphabetical-reference.md)，您的程式碼可能會包含一個或多個基類，而您可能不知道這些類別的名稱，但其中包含您想要呼叫的方法。

## <a name="example"></a>範例

```cpp
// deriv_super.cpp
// compile with: /c
struct B1 {
   void mf(int) {}
};

struct B2 {
   void mf(short) {}

   void mf(char) {}
};

struct D : B1, B2 {
   void mf(short) {
      __super::mf(1);   // Calls B1::mf(int)
      __super::mf('s');   // Calls B2::mf(char)
   }
};
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)

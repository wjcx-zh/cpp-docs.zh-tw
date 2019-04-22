---
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: a69d177bb83ce404a18d50c8f966be5d81f5fa72
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779647"
---
# <a name="super"></a>__super

**Microsoft 專屬**

可讓您明確陳述您要呼叫將覆寫之函式的基底類別實作。

## <a name="syntax"></a>語法

```
__super::member_function();
```

## <a name="remarks"></a>備註

多載解析階段會考量所有可存取的基底類別方法，並且提供最佳相符結果的函式即為將會呼叫的函式。

**__super**只可出現在成員函式的主體。

**__super**不能與 using 宣告。 請參閱[using 宣告](../cpp/using-declaration.md)如需詳細資訊。

引進[屬性](../windows/attributes/attributes-alphabetical-reference.md)插入程式碼，您的程式碼可能包含您可能不知道，但該名稱包含您想要呼叫的方法的一個或多個基底的類別。

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

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)
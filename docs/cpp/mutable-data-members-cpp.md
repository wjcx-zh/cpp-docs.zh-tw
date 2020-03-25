---
title: 可變動的資料成員 (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: db3a9594a77a9ada971213eaea74a9842bd96a54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179337"
---
# <a name="mutable-data-members-c"></a>可變動的資料成員 (C++)

這個關鍵字只能套用至非靜態和非常數類別的資料成員。 如果資料成員宣告為可**變動，則**從**const**成員函式將值指派給這個資料成員是合法的。

## <a name="syntax"></a>語法

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>備註

例如，下列程式碼會編譯而不會發生錯誤，因為 `m_accessCount` 已經宣告**為可變動，因此**即使 `GetFlag` 是 const 成員函式，也可以透過 `GetFlag` 修改。

```cpp
// mutable.cpp
class X
{
public:
   bool GetFlag() const
   {
      m_accessCount++;
      return m_flag;
   }
private:
   bool m_flag;
   mutable int m_accessCount;
};

int main()
{
}
```

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)

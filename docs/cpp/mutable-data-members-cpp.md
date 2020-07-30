---
title: 可變動的資料成員 (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: 9370952f503850fbc296c3df912d4a0fafe163f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227344"
---
# <a name="mutable-data-members-c"></a>可變動的資料成員 (C++)

這個關鍵字只能套用至非靜態和非常數類別的資料成員。 如果宣告了資料成員 **`mutable`** ，則從成員函式將值指派給這個資料成員是合法的 **`const`** 。

## <a name="syntax"></a>語法

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>備註

例如，下列程式碼會編譯而不會發生錯誤 `m_accessCount` ，因為已宣告為 **`mutable`** ，因此 `GetFlag` 即使 `GetFlag` 是 const 成員函式，也可以修改。

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

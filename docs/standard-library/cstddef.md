---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 87d268977ee46112fedce517e66a9e68071863db
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457565"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

包含 C 標準程式庫標\<頭 stddef.h >, 並將相關聯的`std`名稱加入至命名空間。 包含此標頭可確保在 C 標準程式庫標頭中使用外部連結宣告的名稱會`std`在命名空間中宣告。

> [!NOTE]
> \<cstddef > 包含類型**byte** , 而且不包含**wchar_t**類型。

## <a name="syntax"></a>語法

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>命名空間和宏

```cpp
namespace std {
    using ptrdiff_t = see definition;
    using size_t = see definition;
    using max_align_t = see definition;
    using nullptr_t = decltype(nullptr);
}

#define NULL  // an implementation-defined null pointer constant
#define offsetof(type, member-designator)
```

### <a name="parameters"></a>參數

*ptrdiff_t*\
執行定義的帶正負號整數類型, 可以保存陣列物件中兩個下標的差異。

*size_t*\
實值定義的不帶正負號的整數類型, 夠大, 足以包含任何物件的大小 (以位元組為單位)。

*max_align_t*\
其對齊需求至少與每個純量類型相同, 而且每個內容都支援其對齊需求的 POD 類型。

*nullptr_t*\
**Nullptr**運算式類型的同義字。 雖然無法取得**nullptr**位址, 但也可以採用另一個可為左值的*nullptr_t*物件的位址。

## <a name="byte-class"></a>byte 類別

```cpp
enum class byte : unsigned char {};

template <class IntType>
    constexpr byte& operator<<=(byte& b, IntType shift) noexcept;
    constexpr byte operator<<(byte b, IntType shift) noexcept;
    constexpr byte& operator>>=(byte& b, IntType shift) noexcept;
    constexpr byte operator>>(byte b, IntType shift) noexcept;

constexpr byte& operator|=(byte& left, byte right) noexcept;
constexpr byte operator|(byte left, byte right) noexcept;
constexpr byte& operator&=(byte& left, byte right) noexcept;
constexpr byte operator&(byte left, byte right) noexcept;
constexpr byte& operator^=(byte& left, byte right) noexcept;
constexpr byte operator^(byte left, byte right) noexcept;
constexpr byte operator~(byte b) noexcept;

template <class IntType>
    IntType to_integer(byte b) noexcept;
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

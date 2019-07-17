---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 15d13a3af35cb41950df8aeba0c86d779e701ddb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244452"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

包含 C 標準程式庫標頭\<stddef.h > 並將關聯的名稱加入`std`命名空間。 包含此標頭中宣告的宣告 C 標準程式庫標頭中使用外部連結的名稱可確保`std`命名空間。

> [!NOTE]
> \<cstddef > 包含型別**位元組**並且不包含型別**wchar_t**。

## <a name="syntax"></a>語法

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>命名空間和巨集

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
實作定義，將帶正負號的整數類型，可保存兩個註標的陣列物件中的差異。

*size_t*\
實作定義不帶正負號的整數類型，夠大，足以容納的大小，以位元組為單位的任何物件。

*max_align_t*\
POD 類型的對齊需求是至少一樣大，每一個純量類型，並支援每個內容的對齊需求。

*nullptr_t*\
類型的同義字**nullptr**運算式。 雖然**nullptr**位址無法採用另一個位址*nullptr_t*可以採取是左值的物件。

## <a name="byte-class"></a>位元組類別

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

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

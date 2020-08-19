---
title: static_assert
ms.date: 07/29/2019
f1_keywords:
- static_assert_cpp
helpviewer_keywords:
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
ms.openlocfilehash: 55181193e0364c1c6b758365c674f8e2c8a3f4c7
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560630"
---
# <a name="static_assert"></a>static_assert

在編譯時期測試軟體判斷提示。 如果指定的常數運算式為 **`false`** ，則編譯器會顯示指定的訊息（如果有提供的話），而且編譯會失敗並出現錯誤 C2338; 否則，宣告沒有任何作用。

## <a name="syntax"></a>語法

```
static_assert( constant-expression, string-literal );

static_assert( constant-expression ); // C++17 (Visual Studio 2017 and later)
```

### <a name="parameters"></a>參數

*常數運算式*\
可以轉換為布林值的整數常數運算式。 如果評估的運算式為零 (false) ，則會顯示 *字串常* 值參數，而且編譯會失敗並出現錯誤。 如果運算式非零 (true) ，則宣告 **`static_assert`** 沒有任何作用。

*字串常值*\
如果 *常數運算式* 參數為零，則會顯示訊息。 訊息是編譯器 [基底字元集](../c-language/ascii-character-set.md) 中的字元字串;也就是說，不是 [多位元組或寬字元](../c-language/multibyte-and-wide-characters.md)。

## <a name="remarks"></a>備註

宣告的 *常數運算式* 參數 **`static_assert`** 表示 *軟體*判斷提示。 軟體判斷提示會指定您希望在程式中的某個特定點為 true 的條件。 如果條件為 true，則宣告 **`static_assert`** 沒有任何作用。 如果條件為 false，則判斷提示會失敗，編譯器會以 *字串常* 值參數顯示訊息，且編譯會失敗並出現錯誤。 在 Visual Studio 2017 和更新版本中，字串常值參數是選擇性的。

**`static_assert`** 宣告會在編譯時期測試軟體判斷提示。 相反地，判斷提示 [宏和 _assert 和 _wassert 函數](../c-runtime-library/reference/assert-macro-assert-wassert.md) 會在執行時間測試軟體判斷提示，並在空間或時間產生執行時間成本。 宣告 **`static_assert`** 特別適用于偵錯工具，因為樣板引數可以包含在 *常數運算式* 參數中。

當遇到宣告時，編譯器會檢查宣告是否 **`static_assert`** 有語法錯誤。 如果運算式不相依于樣板參數，則編譯器會立即評估 *常數運算式* 參數。 否則，編譯器會在範本具現化時評估 *常數運算式* 參數。 因此，編譯器可能會在遇到宣告時發出診斷資訊一次，並且在樣板具現化時再次發出訊息。

您可以 **`static_assert`** 在命名空間、類別或區塊範圍中使用關鍵字。  (**`static_assert`** 關鍵字在技術上是宣告，雖然它不會在您的程式中引入新的名稱，因為它可以在命名空間範圍中使用。 ) 

## <a name="description"></a>描述

在下列範例中，宣告 **`static_assert`** 具有命名空間範圍。 由於編譯器已知 `void *` 類型的大小，因此會立即計算運算式的值。

## <a name="example"></a>範例

```cpp
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");
```

## <a name="description"></a>描述

在下列範例中，宣告 **`static_assert`** 具有類別範圍。 **`static_assert`** 會確認範本參數是*純舊的資料* (POD) 類型。 編譯器會檢查宣告的宣告 **`static_assert`** ，但在中具現化類別樣板之前，不會評估 *常數運算式* 參數 `basic_string` `main()` 。

## <a name="example"></a>範例

```cpp
#include <type_traits>
#include <iosfwd>
namespace std {
template <class CharT, class Traits = std::char_traits<CharT> >
class basic_string {
    static_assert(std::is_pod<CharT>::value,
                  "Template argument CharT must be a POD type in class template basic_string");
    // ...
    };
}

struct NonPOD {
    NonPOD(const NonPOD &) {}
    virtual ~NonPOD() {}
};

int main()
{
    std::basic_string<char> bs;
}
```

## <a name="description"></a>描述

在下列範例中，宣告 **`static_assert`** 具有區塊範圍。 **`static_assert`** 會驗證 VMPage 結構的大小是否等於系統的虛擬記憶體 pagesize。

## <a name="example"></a>範例

```cpp
#include <sys/param.h> // defines PAGESIZE
class VMMClient {
public:
    struct VMPage { // ...
           };
    int check_pagesize() {
    static_assert(sizeof(VMPage) == PAGESIZE,
        "Struct VMPage must be the same size as a system virtual memory page.");
    // ...
    }
// ...
};
```

## <a name="see-also"></a>另請參閱

[判斷提示和使用者提供的訊息 (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
[#error 指示詞 (C/c + +) ](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert 宏、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[範本](../cpp/templates-cpp.md)<br/>
[ASCII 字元集](../c-language/ascii-character-set.md)<br/>
[宣告和定義](declarations-and-definitions-cpp.md)

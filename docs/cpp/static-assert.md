---
title: static_assert |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- static_assert_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ keywords, static_assert
- C2338
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3c3648f0b372df3c898c41197cba86e6ae9f894
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078487"
---
# <a name="staticassert"></a>static_assert

在編譯時期測試軟體判斷提示。 如果指定的常數運算式為 FALSE，則編譯器會顯示指定的訊息，如果提供其中一個，且編譯會失敗並產生錯誤 C2338;否則宣告沒有任何作用。

## <a name="syntax"></a>語法

```
static_assert( constant-expression, string-literal );

static_assert( constant-expression ); // Visual Studio 2017 and later
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*constant-expression*|可以轉換為布林值的整數常數運算式。<br /><br /> 如果評估的運算式為零 (false)，*字串常值*參數會顯示，且編譯會失敗並發生錯誤。 如果運算式為非零值 (true) **static_assert**宣告沒有任何作用。|
|*string-literal*|如果會顯示訊息*常數運算式*參數為零。 訊息是中的字元字串[基底字元集](../c-language/ascii-character-set.md)編譯器; 的而非[多位元組或寬字元](../c-language/multibyte-and-wide-characters.md)。|

## <a name="remarks"></a>備註

*常數運算式*的參數**static_assert**宣告代表*軟體判斷提示*。 軟體判斷提示會指定您希望在程式中的某個特定點為 true 的條件。 如果條件為 true， **static_assert**宣告沒有任何作用。 如果條件為 false，表示判斷提示失敗，則編譯器會顯示在訊息*字串常值*參數，且編譯會失敗並發生錯誤。 在 Visual Studio 2017 和更新版本中，字串常值參數是選擇性的。

**Static_assert**宣告測試軟體判斷提示，在編譯時期。 相反地， [assert 巨集、 _assert、 _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)巨集測試軟體判斷提示，在執行階段，並會產生執行的階段成本空間或時間。 **Static_assert**宣告是特別適用於偵錯，因為樣板引數可以包含在*常數運算式*參數。

編譯器會檢查**static_assert**宣告在遇到宣告時的語法錯誤。 編譯器會評估*常數運算式*它不相依於樣板參數時，立即的參數。 否則，編譯器會評估*常數運算式*參數具現化範本時。 因此，編譯器可能會在遇到宣告時發出診斷資訊一次，並且在樣板具現化時再次發出訊息。

您可以使用**static_assert**在命名空間、 類別或區塊範圍的關鍵字。 ( **Static_assert**關鍵字是宣告就技術上而言，即使它不會引進新的名稱到您的程式，因為它可在命名空間範圍。)

## <a name="description"></a>描述

在下列範例中， **static_assert**宣告具有命名空間範圍。 由於編譯器已知 `void *` 類型的大小，因此會立即計算運算式的值。

## <a name="example"></a>範例

```cpp
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");
```

## <a name="description"></a>描述

在下列範例中， **static_assert**宣告具有類別範圍。 **Static_assert**會驗證樣板參數是*一般舊資料*(POD) 類型。 編譯器會檢查**static_assert**宣告，當它已宣告，但不會評估*常數運算式*直到參數`basic_string`類別樣板具現化中`main()`.

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

在下列範例中， **static_assert**宣告具有區塊範圍。 **Static_assert**驗證 VMPage 結構的大小是系統虛擬記憶體 pagesize 相等。

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
[#error 指示詞 (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert 巨集、_assert、_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[範本](../cpp/templates-cpp.md)<br/>
[ASCII 字元集](../c-language/ascii-character-set.md)<br/>
[宣告和定義](declarations-and-definitions-cpp.md)
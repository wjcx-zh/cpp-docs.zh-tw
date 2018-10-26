---
title: 編譯器警告 （層級 3） C4996 |Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4996
dev_langs:
- C++
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dff9f3c988e7ffdf8f15b5502bb0326e2692a128
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079034"
---
# <a name="compiler-warning-level-3-c4996"></a>編譯器警告 （層級 3） C4996

編譯器遇到已被取代的宣告。 **這項警告一律是審慎的文件庫或包含的標頭檔，您不應該使用已被取代的符號而不需要瞭解後果，否則作者提供的訊息。** 實際的警告訊息是已被取代的修飾詞或屬性宣告中的站台所指定。

這些是一些常見的 C4996 訊息，產生的 C 執行階段程式庫和標準程式庫，但不是詳盡的清單。 遵循下列連結，或閱讀的方式來修正此問題，或關閉的警告。

- [此項目的 POSIX 名稱已被取代。相反地，使用 ISO C 與 c + + 標準的名稱： *new_name*。如需詳細資料，請參閱線上說明。](#posix-function-names)

- [此函式或變數可能不安全。請考慮使用*safe_version*改。若要停用已被取代，請使用\_CRT\_SECURE\_NO\_警告。如需詳細資料，請參閱線上說明。](#unsafe-crt-library-functions)

- [' std::*function_name*::\_未核取\_迭代器::\_Deprecate' 呼叫 std::*function_name*使用參數的可能不安全-此呼叫須呼叫端檢查通過的值正確。若要停用這項警告，請使用 - D_SCL_SECURE_NO_WARNINGS。請參閱有關如何使用 Visual c + + ' Checked Iterators' 的文件](#unsafe-standard-library-functions)

- [此函式或變數已被較新的文件庫或作業系統功能取代。請考慮使用*new_item*改。如需詳細資料，請參閱線上說明。](#obsolete-crt-functions-and-variables)

## <a name="cause"></a>原因

當編譯器遇到函式或變數標示為，就會發生 C4996[過時](../../cpp/deprecated-cpp.md)利用`__declspec(deprecated)`修飾詞，或當您嘗試存取函式、 類別成員或具有 C + + 14 的 typedef [ \[\[過時\]\] ](../../cpp/attributes.md)屬性。 您可以使用`__declspec(deprecated)`修飾詞或`[[deprecated]]`屬性自行在您的程式庫或標頭檔，以警告您有關已被取代的函式、 變數、 成員或 typedef 的用戶端。

## <a name="remarks"></a>備註

許多函式、 成員函式、 樣板函式和在 Visual Studio 中的程式庫中的全域變數會標示*已被取代*。 這些函式會被取代，因為它們可能會有不同的慣用的名稱、 可能不安全或有更安全的變體，或可能已經過時。 許多已被取代的訊息，包括建議的取代已被取代的函式或全域變數。

若要修正此問題，我們通常建議您變更程式碼以改用建議的更安全的或更新函式和全域變數。 如果您需要使用現有的函式或變數，可攜性的原因，警告可以關閉。

### <a name="to-turn-the-warning-off-without-fixing-the-issue"></a>將警告關閉，而不需要修正問題

您可以藉由關閉特定一行程式碼的警告[警告](../../preprocessor/warning.md)pragma， `#pragma warning(suppress : 4996)`。 您也可以關閉警告檔案內使用警告 pragma， `#pragma warning(disable : 4996)`。

您可以關閉警告全域命令列組建中使用 **/wd4996**命令列選項。

若要關閉 Visual Studio IDE 中的整個專案的警告：

- 開啟**屬性頁**為您的專案 對話方塊。 如需如何使用 [屬性頁] 對話方塊的資訊，請參閱[屬性頁](../../ide/property-pages-visual-cpp.md)。
- 選取 **組態屬性**， **C/c + +**，**進階**頁面。
- 編輯**停用特定警告**屬性，即可加入`4996`。 選擇**確定**以套用變更。

您也可以使用前置處理器巨集關閉某些特定的類別之程式庫中使用的取代警告。 以下將說明這些巨集。

若要在 Visual Studio 中定義前置處理器巨集：

- 開啟**屬性頁**為您的專案 對話方塊。 如需如何使用 [屬性頁] 對話方塊的資訊，請參閱[屬性頁](../../ide/property-pages-visual-cpp.md)。
- 依序展開**組態屬性 > C/c + + > 前置處理器**。
- 在 **前置處理器定義**屬性新增巨集名稱。 選擇 [確定]  加以儲存，然後重建您的專案。

若要定義巨集只能在特定的原始程式檔中，加入一行例如`#define EXAMPLE_MACRO_NAME`之前任一行，其中包含的標頭檔。

## <a name="specific-c4996-messages"></a>C4996 的特定訊息

以下是一些常見的 C4996 警告和錯誤的來源。

### <a name="posix-function-names"></a>POSIX 函式名稱

**此項目的 POSIX 名稱已被取代。相反地，使用 ISO C 與 c + + 標準的名稱：** *new_name*。 **請參閱線上說明，如需詳細資訊。**

Microsoft 已重新命名以依照 C99 與 c++03 規則實作所定義的全域函式名稱的 CRT 中的某些 POSIX 函式。 只有原始 POSIX 名稱已被取代，函式本身。 在大多數情況下，POSIX 函式名稱前會加上底線來表示符合標準的名稱。 編譯器會發出取代警告，原始的函式名稱，並建議慣用的名稱。

若要修正此問題，我們通常建議您變更程式碼以改用建議的函式名稱。 不過，更新的名稱是 Microsoft 特定的。 如果您需要使用現有的函式名稱的可攜性的理由，您可以關閉這些警告。 POSIX 函式仍在原來的名稱下的文件庫中。

若要關閉這些函式已被取代警告，請定義前置處理器巨集 **\_CRT\_NONSTDC\_無\_警告**。 您可以定義此巨集，在命令列加上選項`/D_CRT_NONSTDC_NO_WARNINGS`。

### <a name="unsafe-crt-library-functions"></a>不安全的 CRT 程式庫函式

**此函式或變數可能不安全。請考慮使用** *safe_version* **改。若要停用已被取代，請使用\_CRT\_SECURE\_NO\_警告。如需詳細資料，請參閱線上說明。**

Microsoft 已取代一些 CRT 與 c + + 標準程式庫函式和全域變數，以更安全的版本。 在大部分情況下，取消核取的讀取或寫入存取權可能會導致嚴重的安全性問題的緩衝區，可讓已被取代的函式。 編譯器會為這些函式發出已被取代的警告，並建議所應使用的函式。

若要修正此問題，我們建議您使用函式或變數*safe_version*改。 如果您已經確認它並不適用緩衝區覆寫，或 overread 出現在您的程式碼，而且您無法變更的程式碼可攜性的理由，您可以關閉此警告。

若要關閉 CRT 中這些函式已被取代警告，請定義 **\_CRT\_SECURE\_無\_警告**。 若要關閉已被取代的全域變數的相關警告，請定義 **\_CRT\_SECURE\_無\_警告\_GLOBALS**。 如需有關這些已被取代的函式和全域變數的詳細資訊，請參閱 < [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)並[安全程式庫： c + + 標準程式庫](../../standard-library/safe-libraries-cpp-standard-library.md)。

### <a name="unsafe-standard-library-functions"></a>不安全的標準程式庫函式

__' std::__*function_name*__::\_未核取\_迭代器::\_Deprecate' 呼叫 std::__*function_name***使用參數的可能不安全-此呼叫須由呼叫端檢查通過的值是否正確。若要停用這個警告，請使用 -D\_SCL\_SECURE\_NO\_警告。請參閱有關如何使用 Visual c + + ' Checked Iterators' 的文件**

因為某些 c + + 標準程式庫範本函式不會檢查正確的參數，在偵錯組建會出現這個警告。 在大部分情況下，這是因為沒有足夠的資訊可供函式，以檢查容器範圍中，或可能不正確地使用迭代器，與函式。 這項警告有助於您識別這些函式會使用，因為它們可能是嚴重的安全性漏洞，在程式中的來源。 如需詳細資訊，請參閱 [Checked Iterators](../../standard-library/checked-iterators.md)。

比方說，這個警告會出現在偵錯模式如果您傳遞的項目指標`std::copy`而不是純文字的陣列。 若要修正此問題，請使用適當宣告的陣列，讓程式庫可以檢查陣列範圍，並執行界限檢查。

```cpp
// C4996_copyarray.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_copyarray.cpp
#include <algorithm>

void example(char const * const src) {
    char dest[1234];
    char * pdest3 = dest + 3;
    std::copy(src, src + 42, pdest3); // C4996
    std::copy(src, src + 42, dest);   // OK, copy can tell that dest is 1234 elements
}
```

數個標準程式庫演算法已更新為 C + + 14 中有 「 雙重範圍 」 版本。 如果您使用雙重範圍版本時，第二個範圍會提供必要的繫結檢查：

```cpp
// C4996_containers.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_containers.cpp
#include <algorithm>

bool example(
    char const * const left,
    const size_t leftSize,
    char const * const right,
    const size_t rightSize)
{
    bool result = false;
    result = std::equal(left, left + leftSize, right); // C4996
    // To fix, try this form instead:
    // result = std::equal(left, left + leftSize, right, right + rightSize); // OK
    return result;
}
```

此範例示範數個標準程式庫可用來檢查迭代器使用方式的更多方式，當未核取的使用方式可能會造成危險：

```cpp
// C4996_standard.cpp
// compile with: cl /EHsc /W4 /MDd C4996_standard.cpp
#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    // NOTE: This applies only when raw arrays are
    // given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (i.e. an overrun triggers undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (i.e. an overrun triggers a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(),
        stdext::make_checked_array_iterator(p7, 16),
        [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator
    // is marked as checked in debug mode, but it performs no checking,
    // so an overrun triggers undefined behavior
    int a8[16];
    int * p8 = a8;
    transform( v.begin(), v.end(),
        stdext::make_unchecked_array_iterator(p8),
        [](int n) { return n * 8; });
    print("a8: ", a8);
}
```

如果您已經確認您的程式碼不能有緩衝區滿溢會觸發這個警告的標準程式庫函式中的錯誤，您可能想要關閉此警告。 若要關閉這些函式的警告，請定義 **\_SCL\_SECURE\_無\_警告**。

### <a name="checked-iterators-enabled"></a>啟用已檢查的迭代器

如果您不要使用已檢查的迭代器，進行編譯時，也會發生 C4996`_ITERATOR_DEBUG_LEVEL`定義為 1 或 2。 它會設定為 2，根據預設，偵錯模式組建，並為零售組建的 0。 如需詳細資訊，請參閱 [Checked Iterators](../../standard-library/checked-iterators.md) 。

```cpp
// C4996_checked.cpp
// compile with: /EHsc /W4 /MDd C4996_checked.cpp
#define _ITERATOR_DEBUG_LEVEL 2

#include <algorithm>
#include <iterator>

using namespace std;
using namespace stdext;

int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 10, 11, 12 };
    copy(a, a + 3, b + 1);   // C4996
    // try the following line instead:
    // copy(a, a + 3, checked_array_iterator<int *>(b, 3));   // OK
}
```

### <a name="unsafe-mfc-or-atl-code"></a>不安全的 MFC 或 ATL 程式碼

如果您使用 MFC 或 ATL 函式已被取代，基於安全性理由，也可能會發生 C4996。

若要修正此問題，我們強烈建議您變更您的程式碼，改為使用更新的函式。

如需如何隱藏這些警告的詳細資訊，請參閱[_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings)。

### <a name="obsolete-crt-functions-and-variables"></a>已淘汰的 CRT 函式和變數

**此函式或變數已被較新的文件庫或作業系統功能取代。請考慮使用** *new_item* **改。如需詳細資料，請參閱線上說明。**

某些程式庫函式與全域變數因為過時而被取代。 這些函式及變數可能會從後續版本的程式庫中移除。 編譯器會為這些函式發出已被取代的警告，並建議所應使用的函式。

若要修正此問題，我們建議您變更程式碼以使用建議的函式或變數。

若要關閉這些項目已被取代警告，請定義 **\_CRT\_過時\_無\_警告**。 如需詳細資訊，請參閱文件中所列之已被取代的函式或變數。

### <a name="marshalling-errors-in-clr-code"></a>CLR 程式碼中的封送處理錯誤

當您使用 CLR 封送處理程式庫時，也可能會發生 C4996。 在此情況下，C4996 是錯誤而非警告。 當您使用時，就會發生此錯誤[marshal_as](../../dotnet/marshal-as.md)需要兩個資料類型之間轉換[marshal_context 類別](../../dotnet/marshal-context-class.md)。 封送處理程式庫不支援轉換時，您也可以收到此錯誤。 如需封送處理程式庫的詳細資訊，請參閱 [Overview of Marshaling in C++](../../dotnet/overview-of-marshaling-in-cpp.md)。

因為封送處理程式庫需要內容，才能從轉換這個範例會產生 C4996`System::String`至`const char *`。

```cpp
// C4996_Marshal.cpp
// compile with: /clr
// C4996 expected
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = marshal_as<const char*>( message );
   return 0;
}
```

## <a name="example-user-defined-deprecated-function"></a>範例： 使用者已被取代函式

警告的呼叫端，當您不再建議使用的特定函式時，您可以在自己的程式碼中使用已被取代的屬性。 在此範例中，使用函數的程式行及列上已被取代的函式宣告，會產生 C4996。

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

__declspec(deprecated) void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```

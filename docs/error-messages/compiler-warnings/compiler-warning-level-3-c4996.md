---
title: 編譯器警告（層級3） C4996
description: 說明為什麼會發生編譯器警告 C4996，並說明該怎麼做。
ms.date: 11/25/2019
f1_keywords:
- C4996
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
ms.openlocfilehash: 98662dc0b5439c1f8857e4f2ad259793a4d03e41
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "79419375"
---
# <a name="compiler-warning-level-3-c4996"></a>編譯器警告（層級3） C4996

您的程式碼會使用標示為已被*取代*的函式、類別成員、變數或 typedef。 藉由使用[__declspec （已淘汰）](../../cpp/deprecated-cpp.md)修飾詞或 c + + 14 已[ \[ \[ 取代 \] \] ](../../cpp/attributes.md)的屬性來取代符號。 實際的 C4996 警告訊息是由宣告的 `deprecated` 修飾詞或屬性所指定。

> [!IMPORTANT]
> 從宣告符號的標頭檔作者中，此警告一律是刻意出現的訊息。 請勿使用已被取代的符號，而不需要瞭解結果。

## <a name="remarks"></a>備註

Visual Studio 程式庫中的許多函數、成員函式、範本函式和全域變數已被*取代*。 有些（例如 POSIX 和 Microsoft 特有的函式）已被取代，因為它們現在有不同的慣用名稱。 某些 C 執行時間程式庫函式已被取代，因為它們是不安全的，而且具有更安全的變體。 其他則已淘汰，因為它們已過時。 淘汰訊息通常會包含已被取代的函式或全域變數的建議替代功能。

## <a name="turn-off-the-warning"></a>關閉警告

若要修正 C4996 問題，我們通常建議您變更程式碼。 請改用建議的函數和全域變數。 如果您因為可攜性的緣故，而需要使用現有的函式或變數，您可以關閉警告。

若要關閉特定程式程式碼的警告，請使用[warning](../../preprocessor/warning.md) pragma `#pragma warning(suppress : 4996)` 。

若要關閉檔案中的警告，請使用 warning pragma `#pragma warning(disable : 4996)` 。

若要在命令列組建中全域關閉警告，請使用[/wd4996](../../build/reference/compiler-option-warning-level.md)命令列選項。

若要關閉 Visual Studio IDE 中整個專案的警告：

1. 開啟專案的 [**屬性頁**] 對話方塊。 如需如何使用 [屬性頁] 對話方塊的詳細資訊，請參閱[屬性頁](../../build/reference/property-pages-visual-cpp.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**] [  >  **高級**] 頁面。

1. 編輯 [**停用特定警告**] 屬性以新增 `4996` 。 選擇 **[確定]** 以套用變更。

您也可以使用預處理器宏，關閉程式庫中使用的某些特定類別的取代警告。 下列是這些宏的說明。

若要在 Visual Studio 中定義預處理器宏：

1. 開啟專案的 [**屬性頁**] 對話方塊。 如需如何使用 [屬性頁] 對話方塊的詳細資訊，請參閱[屬性頁](../../build/reference/property-pages-visual-cpp.md)。

1. 展開 [設定**屬性] > C/c + + > 預處理器**。

1. 在 [**預處理器定義**] 屬性中，加入宏名稱。 選擇 [確定] **** 加以儲存，然後重建您的專案。

若只要在特定的原始程式檔中定義宏，請在 `#define EXAMPLE_MACRO_NAME` 包含標頭檔的任何一行前面加入一行，例如。

以下是一些 C4996 警告和錯誤的常見來源：

## <a name="posix-function-names"></a>POSIX 函數名稱

**此專案的 POSIX 名稱已被取代。請改用符合 ISO C 和 c + + 標準的名稱：** *新名稱*。 **如需詳細資訊，請參閱線上說明。**

Microsoft 已將 CRT 中的某些 POSIX 和 Microsoft 特定程式庫函式重新命名，以符合保留和全域執行定義名稱的 C99 和 c + + 03 條件約束。 *只有名稱已被取代，而不是*函式本身。 在大部分情況下，函式名稱中會加上前置底線來建立符合的名稱。 編譯器會發出原始函式名稱的取代警告，並建議慣用名稱。

若要修正此問題，我們通常建議您變更程式碼，改為使用建議的函數名稱。 不過，更新的名稱是 Microsoft 專有的。 如果您因為可攜性的緣故，而需要使用現有的函式名稱，可以關閉這些警告。 函式仍可在程式庫中的原始名稱下使用。

若要關閉這些函式的已淘汰警告，請定義預處理器宏** \_ CRT \_ NONSTDC \_ 不 \_ **會出現警告。 您可以在命令列中加入選項來定義此宏 `/D_CRT_NONSTDC_NO_WARNINGS` 。

## <a name="unsafe-crt-library-functions"></a>Unsafe CRT 程式庫函式

**這個函數或變數可能不安全。請考慮**改用*安全版本* **。若要停用取代，請使用 \_ CRT \_ SECURE \_ NO \_ 警告。 如需詳細資訊，請參閱線上說明。**

Microsoft 已淘汰部分 CRT 和 c + + 標準程式庫函式和 globals，因為有更安全的版本可供使用。 大部分被取代的函式允許對緩衝區進行未檢查的讀取或寫入存取。 其誤用可能會導致嚴重的安全性問題。 編譯器會為這些函式發出已被取代的警告，並建議所應使用的函式。

若要修正此問題，建議您改用函數或變數*安全版本*。 有時候，基於可攜性或回溯相容性的理由，您不能這麼做。 請仔細確認您的程式碼中不可能發生緩衝區覆寫或 overread。 然後，您可以關閉警告。

若要關閉 CRT 中這些函式的取代警告，請定義** \_ crt \_ SECURE \_ NO \_ 警告**。

若要關閉有關已被取代之全域變數的警告，請定義** \_ CRT \_ SECURE \_ NO \_ 警告 \_ GLOBALS**。

如需這些已被取代函數和 globals 的詳細資訊，請參閱 CRT 和[安全程式庫： c + + 標準程式庫](../../standard-library/safe-libraries-cpp-standard-library.md)[中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。

## <a name="unsafe-standard-library-functions"></a>不安全的標準程式庫函式

__' std：：__*function_name*__：： \_ Unchecked iterator \_ ：： \_ 取代 ' 呼叫 std：：__*function_name* **的參數可能不安全-此呼叫會依賴呼叫端檢查傳遞的值是否正確。若要停用此警告，請使用-D \_ SCL \_ 不安全的 \_ \_ 警告。請參閱如何使用 Visual C++ 「已檢查的反覆運算**器」的檔

此警告會出現在偵錯工具組建中，因為某些 c + + 標準程式庫範本函式不會檢查參數是否正確。 這通常是因為沒有足夠的資訊可供函式用來檢查容器界限。 或，因為此函式可能會不正確地使用反覆運算器。 此警告可協助您識別這些函式，因為這些函式可能是您程式中嚴重安全性漏洞的來源。 如需詳細資訊，請參閱[已檢查的反覆運算](../../standard-library/checked-iterators.md)器。

例如，如果您將專案指標傳遞至 `std::copy` ，而不是純文字陣列，這個警告就會出現在 [偵錯工具] 模式中。 若要修正此問題，請使用適當宣告的陣列，讓程式庫可以檢查陣列範圍，並執行界限檢查。

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

已更新數個標準程式庫演算法，使其具有 c + + 14 中的「雙重範圍」版本。 如果您使用雙重範圍版本，第二個範圍會提供必要的界限檢查：

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

這個範例會示範數個使用標準程式庫來檢查反覆運算器使用方式的方法，以及未核取的使用方式可能有危險的情況：

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

如果您已確認您的程式碼不能有緩衝區溢位錯誤，可以關閉此警告。 若要關閉這些函式的警告，請定義** \_ SCL \_ 不安全的 \_ \_ 警告**。

## <a name="checked-iterators-enabled"></a>已啟用已檢查的反覆運算器

當 `_ITERATOR_DEBUG_LEVEL` 定義為1或2時，如果您未使用已檢查的反覆運算器，也可能會發生 C4996。 根據預設，它會設定為2的「偵測模式組建」，而「零售組建」則設為0。 如需詳細資訊，請參閱[已檢查的反覆運算](../../standard-library/checked-iterators.md)器。

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

## <a name="unsafe-mfc-or-atl-code"></a>不安全的 MFC 或 ATL 程式碼

如果您基於安全考慮使用已被取代的 MFC 或 ATL 函式，則可能會發生 C4996。

若要修正此問題，我們強烈建議您改為變更程式碼，改為使用更新過的功能。

如需如何隱藏這些警告的相關資訊，請參閱[_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings)。

## <a name="obsolete-crt-functions-and-variables"></a>過時的 CRT 函式和變數

**這個函數或變數已被較新的程式庫或作業系統功能取代。請考慮改為使用** *new_item* **。如需詳細資訊，請參閱線上說明。**

某些程式庫函式與全域變數因為過時而被取代。 這些函式及變數可能會從後續版本的程式庫中移除。 編譯器會為這些函式發出已被取代的警告，並建議所應使用的函式。

若要修正此問題，建議您變更您的程式碼，以使用建議的函式或變數。

若要關閉這些專案的取代警告，請定義** \_ CRT \_ 過時 \_ 不 \_ **會出現警告。 如需詳細資訊，請參閱文件中所列之已被取代的函式或變數。

## <a name="marshaling-errors-in-clr-code"></a>CLR 程式碼中的封送處理錯誤

當您使用 CLR 封送處理程式庫時，也會發生 C4996。 在此情況下，C4996 會是錯誤，而非警告。 當您使用[marshal_as](../../dotnet/marshal-as.md)在需要[marshal_coNtext 類別](../../dotnet/marshal-context-class.md)的兩個資料類型之間進行轉換時，就會發生此錯誤。 當封送處理程式庫不支援轉換時，您也可能會收到這個錯誤。 如需封送處理程式庫的詳細資訊，請參閱[c + + 中的封送處理總覽](../../dotnet/overview-of-marshaling-in-cpp.md)。

這個範例會產生 C4996，因為封送處理程式庫需要內容從轉換成 `System::String` `const char *` 。

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

## <a name="example-user-defined-deprecated-function"></a>範例：使用者定義的已被取代函數

當您不再建議使用特定函式時，可以在自己的程式碼中使用已被取代的屬性來警告呼叫端。 在此範例中，會在兩個位置產生 C4996：一個用於宣告已被取代函式的行，另一個用於使用函式的行。

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

[[deprecated]]
void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```

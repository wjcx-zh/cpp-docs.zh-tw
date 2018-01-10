---
title: "編譯器警告 （層級 3） C4996 |Microsoft 文件"
ms.custom: 
ms.date: 11/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4996
dev_langs: C++
helpviewer_keywords: C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
caps.latest.revision: "34"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e5a4797b4ac5fabc31d747682579c3b3ae6ce900
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4996"></a>編譯器警告 （層級 3） C4996

編譯器遇到已被取代的宣告。 **這項警告永遠是刻意訊息包含的標頭檔，則您不應該瞭解後果，否則使用已被取代的符號之程式庫的作者。** 已被取代的修飾詞或屬性宣告的站台上所指定實際的警告訊息。 

這些是某些常見的 c4996 錯誤訊息，產生的 C 執行階段程式庫和標準程式庫，但不是獨占清單。 請依照下列連結，或閱讀並了解的方法可以修正這個問題，或關閉警告。 

- [此項目的 POSIX 名稱已被取代。相反地，使用 ISO C 和 c + + 一致的名稱： *new_name*。如需詳細資料，請參閱線上說明。](#posix-function-names)

- [此函式或變數可能不安全。請考慮使用*safe_version*改為。若要停用已被取代，請使用\_CRT\_SECURE\_否\_警告。如需詳細資料，請參閱線上說明。](#unsafe-crt-library-functions)

- [' std::*function_name*::\_未核取\_迭代器::\_Deprecate' 呼叫 std::*function_name*參數的可能不安全-此呼叫依賴由呼叫端確認傳遞的值正確無誤。若要停用這項警告，請使用 - D_SCL_SECURE_NO_WARNINGS。請參閱有關如何使用 Visual c + + ' Checked Iterators' 的文件](#unsafe-standard-library-functions)

- [此函式或變數已被取代的較新的文件庫或作業系統功能。請考慮使用*new_item*改為。如需詳細資料，請參閱線上說明。](#obsolete-crt-functions-and-variables)

## <a name="cause"></a>原因

當編譯器遇到函式或標示為的變數，就會發生 C4996[取代](../../cpp/deprecated-cpp.md)使用`__declspec(deprecated)`修飾詞，或當您嘗試存取函式、 類別成員或具有 C + + 14 的 typedef [ \[\[取代\]\] ](../../cpp/attributes2.md)屬性。 您可以使用`__declspec(deprecated)`修飾詞或`[[deprecated]]`自行屬性在文件庫或標頭檔，以警告您有關已被取代的函式、 變數、 成員或 typedef 的用戶端。

## <a name="remarks"></a>備註

許多函式、 成員函式、 樣板函式和在 Visual Studio 中的程式庫中的全域變數標示為*取代*。 這些函式已被取代，因為它們可能會有不同的慣用的名稱、 可能不安全或有更安全的變體，甚至可能已經過時。 許多已被取代的訊息，包括建議的替代已被取代的函式或全域變數。

若要修正此問題，我們通常建議您變更程式碼，改為使用建議的更安全的或更新函式和全域變數。 如果您需要使用現有的函式或變數的可攜性的理由，警告可以關閉。

### <a name="to-turn-the-warning-off-without-fixing-the-issue"></a>將警告關閉，而不修正此問題

您可以使用關閉的特定程式碼行警告[警告](../../preprocessor/warning.md)pragma， `#pragma warning(suppress : 4996)`。 您也可以關閉警告檔案內使用警告 pragma， `#pragma warning(disable : 4996)`。

您可以關閉警告全域命令列組建中使用**/wd4996**命令列選項。

若要關閉 Visual Studio IDE 中的整個專案的警告：

- 開啟**屬性頁**為您的專案 對話方塊。 如需如何使用屬性頁 對話方塊的資訊，請參閱[屬性頁](../../ide/property-pages-visual-cpp.md)。
- 選取**組態屬性**， **C/c + +**，**進階**頁面。
- 編輯**停用特定警告**屬性將`4996`。 選擇**確定**以套用變更。

您也可以使用前置處理器巨集關閉某些程式庫中使用已被取代警告的特定的類別。 以下將詳述這些巨集。

若要在 Visual Studio 中定義前置處理器巨集：

- 開啟**屬性頁**為您的專案 對話方塊。 如需如何使用屬性頁 對話方塊的資訊，請參閱[屬性頁](../../ide/property-pages-visual-cpp.md)。
- 展開**組態屬性 > C/c + + > 前置處理器**。
- 在**前置處理器定義**屬性新增巨集名稱。 選擇 [確定]  加以儲存，然後重建您的專案。

若要定義巨集只能在特定的來源檔案中，加入一行例如`#define EXAMPLE_MACRO_NAME`包含標頭檔的任何一行之前。

## <a name="specific-c4996-messages"></a>C4996 的特定訊息

以下是一些常見的原因 C4996 警告和錯誤。

### <a name="posix-function-names"></a>POSIX 函式名稱

**此項目的 POSIX 名稱已被取代。相反地，使用 ISO C 和 c + + 一致的名稱：** *new_name*。 **請參閱線上說明以取得詳細資料。**

Microsoft 已重新命名以符合 C99 與 C + + 03 規則實作所定義的全域函式名稱的 CRT 中的某些 POSIX 函式。 原始 POSIX 名稱已被取代，函式本身。 在大多數情況下，POSIX 函式名稱前會加上底線來表示符合標準的名稱。 編譯器會發出已被取代警告原始函式名稱，並建議的慣用的名稱。

若要修正此問題，我們通常建議您變更程式碼以改用建議的函式名稱。 不過，更新的名稱是 Microsoft 特定的。 如果您需要使用現有的函式名稱的可攜性的理由，您可以關閉這些警告。 POSIX 函式仍在原來的名稱下文件庫中。

若要關閉這些函式已被取代警告，請定義前置處理器巨集 **\_CRT\_NONSTDC\_否\_警告**。 您可以定義此巨集，在命令列選項，藉以`/D_CRT_NONSTDC_NO_WARNINGS`。


### <a name="unsafe-crt-library-functions"></a>不安全的 CRT 程式庫函式

 **此函式或變數可能不安全。請考慮使用** *safe_version* **改為。若要停用已被取代，請使用\_CRT\_SECURE\_否\_警告。如需詳細資料，請參閱線上說明。**

 Microsoft 已取代一些 CRT 和 c + + 標準程式庫函式和全域變數，以更安全的版本。 在大部分情況下，已被取代的函式可讓未核取的讀取或寫入存取權可能會導致嚴重的安全性問題的緩衝區。 編譯器會為這些函式發出已被取代的警告，並建議所應使用的函式。

 若要修正此問題，我們建議您使用函式或變數*safe_version*改為。 如果您已驗證，就不可能緩衝區覆寫或 overread 會出現在您的程式碼，而且您無法變更的程式碼可攜性的理由，您可以關閉警告。
 
 若要關閉 CRT 中這些函式已被取代警告，請定義 **\_CRT\_SECURE\_否\_警告**。 若要關閉之已被取代的全域變數的相關警告，請定義 **\_CRT\_SECURE\_否\_警告\_GLOBALS**。 如需有關這些已被取代的函式和全域變數的詳細資訊，請參閱[CRT 中安全性功能](../../c-runtime-library/security-features-in-the-crt.md)和[安全程式庫： c + + 標準程式庫](../../standard-library/safe-libraries-cpp-standard-library.md)。

### <a name="unsafe-standard-library-functions"></a>不安全的標準程式庫函式

__' std::__*function_name*__::\_未核取\_迭代器::\_Deprecate' 呼叫 std::__*function_name***參數的可能不安全-此呼叫須由呼叫端確認傳遞的值正確無誤。若要停用這個警告，請使用-D\_SCL\_SECURE\_否\_警告。請參閱有關如何使用 Visual c + + ' Checked Iterators' 的文件**

因為某些 c + + 標準程式庫範本函式不會檢查參數正確，這個警告會出現在偵錯組建。 在大部分情況下，這是因為沒有足夠的資訊提供給函數，以便檢查容器範圍中，或可能不正確地使用迭代器，與函式。 這個警告有助於您識別這些函式使用，因為它們可能會造成嚴重的安全性漏洞，您的程式中的來源。 如需詳細資訊，請參閱 [Checked Iterators](../../standard-library/checked-iterators.md)。

例如，這個警告即會出現在偵錯模式中傳遞的項目指標`std::copy`而非一般陣列。 若要修正此問題，請使用適當地宣告的陣列，讓程式庫可以檢查陣列範圍，並且進行繫結檢查。

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

有數個標準程式庫演算法已更新為 C + + 14 中有 「 雙重範圍 」 版本。 如果您使用的雙重範圍版本時，第二個範圍會提供必要的繫結檢查：

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

這個範例示範幾種標準程式庫可能會用來檢查迭代器使用的多個方法，當未核取的使用方式可能有危險：

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

如果您已確認您的程式碼不能有緩衝區滿溢的情況會觸發這個警告的標準程式庫函式中的錯誤，您可能想要關閉此警告。 若要關閉這些函式的警告，請定義 **\_SCL\_SECURE\_否\_警告**。

### <a name="checked-iterators-enabled"></a>已檢查的迭代器已啟用

如果您不要使用已檢查的迭代器，以編譯時也會發生 C4996`_ITERATOR_DEBUG_LEVEL`定義為 1 或 2。 它會設定為 2，根據預設，偵錯模式組建，以及零售組建的 0。 如需詳細資訊，請參閱 [Checked Iterators](../../standard-library/checked-iterators.md) 。

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

如果您使用 MFC 或 ATL 中已被取代的函式，基於安全性理由，也可能會發生 C4996。

若要修正此問題，我們強烈建議您變更程式碼，改為使用更新的函式。

如需如何隱藏這些警告的資訊，請參閱[_afx_secure_no_warnings，則](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings)。

### <a name="obsolete-crt-functions-and-variables"></a>過時的 CRT 函式和變數

**此函式或變數已被取代的較新的文件庫或作業系統功能。請考慮使用** *new_item* **改為。如需詳細資料，請參閱線上說明。**

某些程式庫函式與全域變數因為過時而被取代。 這些函式及變數可能會從後續版本的程式庫中移除。 編譯器會為這些函式發出已被取代的警告，並建議所應使用的函式。

若要修正此問題，我們建議您變更程式碼以使用建議的函式或變數。

若要關閉這些項目已被取代警告，請定義 **\_CRT\_過時\_否\_警告**。 如需詳細資訊，請參閱文件中所列之已被取代的函式或變數。

### <a name="marshalling-errors-in-clr-code"></a>CLR 程式碼中的封送處理錯誤

當您使用 CLR 封送處理程式庫時，也可能會發生 C4996。 在此情況下，C4996 是錯誤而非警告。 當您使用時，就會發生此錯誤[marshal_as](../../dotnet/marshal-as.md)需要兩個資料類型之間進行轉換[marshal_context 類別](../../dotnet/marshal-context-class.md)。 當封送處理程式庫不支援某項轉換時，您也可以收到這個錯誤。 如需封送處理程式庫的詳細資訊，請參閱 [Overview of Marshaling in C++](../../dotnet/overview-of-marshaling-in-cpp.md)。

這個範例會產生 c4996 錯誤，因為封送處理程式庫需要內容，才能從轉換`System::String`至`const char *`。

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

## <a name="example-user-defined-deprecated-function"></a>範例： 使用者定義已被取代函式

您可以使用自己的程式碼中已被取代的屬性，當您不再建議使用的特定函式警告呼叫端。 在此範例中，使用函數的程式行及行已被取代的函式宣告的會產生 C4996。

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

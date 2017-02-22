---
title: "編譯器警告 (層級 3) C4996 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4996"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4996"
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
caps.latest.revision: 34
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 34
---
# 編譯器警告 (層級 3) C4996
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器遇到已被取代的宣告。  
  
 這則警告或錯誤有幾種可能的含意。  
  
 當編譯器遇到函式或變數標示為[已被取代](../../cpp/deprecated-cpp.md)時，便會發生 `C4996`。 Visual Studio 中有數個函式、成員函式、範本函式，以及程式庫中的全域變數皆標示為已被取代。 這些函式可能有不同的慣用名稱、可能不安全，或可能已有更安全的變體，甚至可能已經過時。 錯誤訊息中可能會為已被取代的函式或全域變數提出替代項目建議。 您可以使用 [警告](../../preprocessor/warning.md) pragma 或 **\/wd4996** 命令列選項關閉此警告。 您也可使用前置處理器巨集關閉某些類別已被取代的警告。  
  
 **此項目的 POSIX 名稱已被取代。請改用符合 ISO C 與 C\+\+ 標準的名稱：** new\_name**。如需詳細資料，請參閱線上說明。**  
  
 CRT 中的某些 POSIX 函式已依照 C99 與 C\+\+03 規則重新命名為實作限定的全域函式名稱。 在大多數情況下，POSIX 函式名稱前會加上底線來表示符合標準的名稱。 編譯器會為原始函式名稱發出已被取代的警告，並建議所應使用的名稱。 只有原始名稱被取代，函式本身仍可繼續使用。 若要關閉這些函式已被取代的警告，請定義前置處理器巨集 **\_CRT\_NONSTDC\_NO\_WARNINGS**。 您可以在命令列中加上選項  `/D_CRT_NONSTDC_NO_WARNINGS` 來加以定義。 若要在 Visual Studio 中定義此巨集，請開啟您專案的 \[屬性頁\] 對話方塊。 展開 \[組態屬性\]、\[C\/C\+\+\]、\[前置處理器\]。 在 \[前置處理器定義\] 中，加入 `_CRT_NONSTDC_NO_WARNINGS`。 選擇 \[確定\] 加以儲存，然後重建您的專案。 若要只在特定的來源檔案中定義此巨集，請在包含標頭檔的該行前加入 `#define _CRT_NONSTDC_NO_WARNINGS` 一行。  
  
 **此函式或變數可能不安全。請考慮改用**  safe\_version **。若要停用已被取代的警告，請使用 \_CRT\_SECURE\_NO\_WARNINGS。如需詳細資料，請參閱線上說明。**  
  
 有些 CRT 函式與 Standard C\+\+ 程式庫函式已經由更安全的新函式所取代。 編譯器會為這些函式發出已被取代的警告，並建議所應使用的函式。 若要關閉 CRT 中這些函式已被取代的警告，請定義 **\_CRT\_SECURE\_NO\_WARNINGS**。 若要為全域變數關閉已被取代的警告，請定義 **\_CRT\_SECURE\_NO\_WARNINGS\_GLOBALS**。 如需這些已被取代的函式及全域變數的詳細資訊，請參閱 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)及 [安全程式庫：C\+\+ 標準程式庫](../../standard-library/safe-libraries-cpp-standard-library.md)。  
  
 **使用參數的函式呼叫可能不安全 \- 此呼叫須由呼叫端確認傳遞值的正確性。 若要停用這項警告，請使用 \- D\_SCL\_SECURE\_NO\_WARNINGS。 請參閱有關如何使用 Visual C\+\+ 'Checked Iterators' 的文件**  
  
 某些 C\+\+ 標準程式庫範本函式不會檢查參數的正確性。 這項警告可協助您確認這些函數的用法。 若要關閉這些函式的警告，請定義 **\_SCL\_SECURE\_NO\_WARNINGS**。 如需詳細資訊，請參閱[已檢查的迭代器](../../standard-library/checked-iterators.md)。  
  
 **此函式或變數已被較新的程式庫或作業系統功能取代。請考慮改用** new\_item**。如需詳細資料，請參閱線上說明。**  
  
 某些程式庫函式與全域變數因為過時而被取代。 這些函式及變數可能會從後續版本的程式庫中移除。 編譯器會為這些函式發出已被取代的警告，並建議所應使用的函式。 若要關閉這些項目之已被取代的警告，請定義 **\_CRT\_OBSOLETE\_NO\_WARNINGS**。 如需詳細資訊，請參閱文件中所列之已被取代的函式或變數。  
  
 **MFC 或 ATL 程式碼中的各種訊息**  
  
 如果您使用因安全考量而被取代的 MFC 或 ATL 函式，也可能會發生 `C4996`。 若要不顯示這些警告，請參閱 [\_AFX\_SECURE\_NO\_WARNINGS](../Topic/_AFX_SECURE_NO_WARNINGS.md) 及 [\_ATL\_SECURE\_NO\_WARNINGS](../Topic/_ATL_SECURE_NO_WARNINGS.md)。  
  
 **CLR 程式碼中的封送處理錯誤**  
  
 當您使用封送處理程式庫時，也可能會發生 `C4996`。 在此情況下，C4996 是錯誤而非警告。 當您使用 [marshal\_as](../../dotnet/marshal-as.md) 轉換兩種需要 [marshal\_context 類別](../../dotnet/marshal-context-class.md) 的資料類型時，會發生此錯誤。 當封送處理不支援某項轉換時，也會發生這個錯誤。 如需封送處理程式庫的詳細資訊，請參閱[C\+\+ 中封送處理的概觀](../../dotnet/overview-of-marshaling-in-cpp.md)。  
  
 **產生 C4996 的範例**  
  
 在第一個例子中，宣告函式的程式行及使用函式的程式行會產生 `C4996`。  
  
## 範例  
 下列範例會產生 C4996。  
  
```cpp  
// C4996.cpp // compile with: /W3 // C4996 warning expected #include <stdio.h> // #pragma warning(disable : 4996) void func1(void) { printf_s("\nIn func1"); } __declspec(deprecated) void func1(int) { printf_s("\nIn func2"); } int main() { func1(); func1(1); }  
```  
  
## 範例  
 用已定義的 `_ITERATOR_DEBUG_LEVEL` 進行編譯時 \(偵錯模式組建設定預設為 1\)，如果您未使用已檢查的迭代器，也可能會發生 C4996。  如需詳細資訊，請參閱 [已檢查的迭代器](../../standard-library/checked-iterators.md)。  
  
 下列 STL 程式碼範例會產生 C4996。  
  
```cpp  
// C4996_b.cpp // compile with: /EHsc /W3 /c #define _ITERATOR_DEBUG_LEVEL 1 #include <algorithm> #include <iterator> using namespace std; using namespace stdext; int main() { int a[] = { 1, 2, 3 }; int b[] = { 10, 11, 12 }; copy(a, a + 3, b + 1);   // C4996 // try the following line instead //   copy(a, a + 3, b); copy(a, a + 3, checked_array_iterator<int *>(b, 3));   // OK }  
  
```  
  
## 範例  
 下列 STL 程式碼範例會產生 C4996 警告。 註解已內嵌。  
  
```cpp  
#include <algorithm> #include <array> #include <iostream> #include <iterator> #include <numeric> #include <string> #include <vector> using namespace std; template <typename C> void print(const string& s, const C& c) { cout << s; for (const auto& e : c) { cout << e << " "; } cout << endl; } int main() { vector<int> v(16); iota(v.begin(), v.end(), 0); print("v: ", v); // OK: vector::iterator is checked in debug mode // (i.e. an overrun will trigger a debug assertion) vector<int> v2(16); transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; }); print("v2: ", v2); // OK: back_insert_iterator is marked as checked in debug mode // (i.e. an overrun is impossible) vector<int> v3; transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; }); print("v3: ", v3); // OK: array::iterator is checked in debug mode // (i.e. an overrun will trigger a debug assertion) array<int, 16> a4; transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; }); print("a4: ", a4); // OK: Raw arrays are checked in debug mode // (i.e. an overrun will trigger a debug assertion) // NOTE: This applies only when raw arrays are given to STL algorithms! int a5[16]; transform(v.begin(), v.end(), a5, [](int n) { return n * 5; }); print("a5: ", a5); // WARNING C4996: Pointers cannot be checked in debug mode // (i.e. an overrun will trigger undefined behavior) int a6[16]; int * p6 = a6; transform(v.begin(), v.end(), p6, [](int n) { return n * 6; }); print("a6: ", a6); // OK: stdext::checked_array_iterator is checked in debug mode // (i.e. an overrun will trigger a debug assertion) int a7[16]; int * p7 = a7; transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; }); print("a7: ", a7); // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode // (i.e. it performs no checking, so an overrun will trigger undefined behavior) int a8[16]; int * p8 = a8; transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; }); print("a8: ", a8); }  
  
```  
  
## 範例  
 下列範例會產生 C4996 錯誤，因為封送處理程式庫需要內容，才能從 `System::String` 轉換為 `const char *`。  
  
```cpp  
// C4996_Marshal.cpp // compile with: /clr // C4996 expected #include <stdlib.h> #include <string.h> #include <msclr\marshal.h> using namespace System; using namespace msclr::interop; int main() { String^ message = gcnew String("Test String to Marshal"); const char* result; result = marshal_as<const char*>( message ); return 0; }  
```
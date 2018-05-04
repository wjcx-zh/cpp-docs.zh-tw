---
title: 為 C 樣式字串相關的 Cstring |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, basic operations
- MFC [C++], string handling class
- string conversion [C++], C-style strings
- strings [C++], string operations
- standard run-time library string functions
- null values, Null-terminated string conversion
- string functions
- strings [C++], in C
- string arguments
- C-style strings
- strings [C++], class CString
- casting CString objects
ms.assetid: 5048de8a-5298-4891-b8a0-c554b5a3ac1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d0683f82204b11d06b1952913d4dbdb1e4a468d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>與 C 樣式字串相關的 CString
A [CString](../atl-mfc-shared/using-cstring.md)物件包含的字元字串資料。 `CString` 繼承一組[方法與運算子](../atl-mfc-shared/reference/cstringt-class.md)類別樣板中所定義[CStringT](../atl-mfc-shared/reference/cstringt-class.md)來處理字串資料。 (`CString`是`typedef`的特製化`CStringT`若要使用的字元資料類型，`CString`支援。)  
  
 `CString` 不像 C 樣式的 null 終止字串一樣在內部存放字元資料。 相對地，`CString` 會追蹤字元資料的長度，以便能更安全地監看資料及其所需空間。  
  
 `CString` 會接受 C 樣式字串，且提供以 C 樣式字串來存取字元資料的方式。 本主題包含下列各節，解釋如何使用 `CString` 物件，就彷彿其為 C 樣式的 null 終止字串。  
  
- [轉換為 C 樣式 null 終止字串](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)  
  
- [使用標準執行階段程式庫字串函式](#_core_working_with_standard_run.2d.time_library_string_functions)  
  
- [直接修改 CString 內容](#_core_modifying_cstring_contents_directly)  
  
- [使用 CString 物件搭配變數引數函式](#_core_using_cstring_objects_with_variable_argument_functions)  
  
- [指定 CString 正式參數](#_core_specifying_cstring_formal_parameters)  
  
##  <a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a> 使用 CString 做為 C 樣式 Null 終止字串  
 若要使用 `CString` 物件做為 C 樣式的字串，請將物件轉型為 `LPCTSTR`。 在下列範例中，`CString` 會傳回唯讀 C 樣式 null 終止字串的指標。 `strcpy` 函式會將一份 C 樣式字串放在變數 `myString`。  
  
```  
CString aCString = "A string";  
char myString[256];  
strcpy(myString, (LPCTSTR)aCString);
```  
  
 您可以使用 `CString` 方法，例如 `SetAt`，來修改字串物件中的個別字元。 不過，`LPCTSTR` 指標是暫時性的，在對 `CString` 做了任何變更後便會失效。 `CString` 也可能超出範圍而自動遭刪除。 我們建議您每次使用時都取得 `LPCTSTR` 物件的全新 `CString` 指標。  
  
 有時候您可能需要一份 `CString` 資料以便直接修改。 請使用更安全的函式 `strcpy_s` (或 Unicode/MBCS 可攜式 `_tcscpy_s`) 將 `CString` 物件複製到個別的緩衝區。 在這裡，字元可以安全地修改，如下列範例所示。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]  
  
> [!NOTE]
>  第三個引數`strcpy_s`(或 Unicode/MBCS 可攜式`_tcscpy_s`) 是`const wchar_t*`(Unicode) 或`const char*`(ANSI)。 上述範例會為這個引數傳遞一個 `CString`。 C++ 編譯器自動套用為 `CString` 類別定義的轉換函式，它會將 `CString` 轉換成 `LPCTSTR`。 定義從一個類型到另一個類型的轉型作業功能，是 C++ 最實用的功能之一。  
  
##  <a name="_core_working_with_standard_run.2d.time_library_string_functions"></a> 使用標準執行階段程式庫字串函式  
 您應該能夠找到 `CString` 方法以執行任何字串作業，且對於這些作業您可能考慮使用標準 C 執行階段程式庫字串函式，例如 `strcmp` (或 Unicode/MBCS 可攜式 `_tcscmp`)。  
  
 如果您必須使用 C 執行階段字串函式，您可以使用 _core_using_cstring_as_a_c.2d.style_null.2d.terminated_string 中所述的技巧。 您可以將 `CString` 物件複製到相等的 C 樣式字串緩衝區、在緩衝區上執行作業，然後將產生的 C 樣式字串指派回 `CString` 物件。  
  
##  <a name="_core_modifying_cstring_contents_directly"></a> 直接修改 CString 內容  
 在大多數情況下，您應該使用 `CString` 成員函式來修改 `CString` 物件的內容，或是將 `CString` 轉換成 C 樣式的字元字串。  
  
 有一些情況下，也可以直接修改 `CString` 內容，例如，當您使用需要字元緩衝區的作業系統函式時。  
  
 `GetBuffer` 和 `ReleaseBuffer` 方法提供對 `CString` 物件內部字元緩衝區的存取，並讓您直接修改它。 下列步驟顯示如何使用這些函式來達成此目的。  
  
#### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>使用 GetBuffer 和 ReleaseBuffer 存取 CString 物件的內部字元緩衝區  
  
1.  針對 `GetBuffer` 物件呼叫 `CString` 並指定您需要的緩衝區長度。  
  
2.  使用 `GetBuffer` 傳回的指標直接將字元寫入 `CString` 物件。  
  
3.  針對 `ReleaseBuffer` 物件呼叫 `CString`，更新所有內部 `CString` 狀態資訊，例如字串的長度。 直接修改 `CString` 物件的內容之後，您必須先呼叫 `ReleaseBuffer` 然後才呼叫任何其他 `CString` 成員函式。  
  
##  <a name="_core_using_cstring_objects_with_variable_argument_functions"></a> 使用 CString 物件搭配變數引數函式  
 有些 C 函數接受可變數目的引數。 值得注意的範例是 `printf_s`。 由於這種函式的宣告方式，編譯器無法確定引數的類型，且無法判斷對每個引數要執行哪種轉換作業。 因此，很重要的一點是您要在傳遞 `CString` 物件給接受可變數目之引數的函式時，使用明確的類型轉型。  
  
 若要在可變引數函式中使用 `CString` 物件，請明確地將 `CString` 轉型成 `LPCTSTR` 字串，如下列範例所示。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]  
  
##  <a name="_core_specifying_cstring_formal_parameters"></a> 指定 CString 正式參數  
 對於需要字串引數的大部分函式，最好是將函式原型中的正式參數指定為字元 (`const`) 的 `LPCTSTR` 指標，而不是 `CString`。 當正式參數指定為字元的 `const` 指標時，可以傳遞指標給 `TCHAR` 陣列、常值字串 [`"hi there"`] 或 `CString` 物件。 `CString` 物件將會自動轉換成 `LPCTSTR`。 只要是您能使用 `LPCTSTR` 的位置，您就也能使用 `CString` 物件。  
  
 您也可以指定正式參數做為常數字串參考 (也就是`const CString&`) 如果不會修改引數。 如果函式將修改字串，請捨棄 `const` 修飾詞。 如果想要使用預設 null 值，請將它初始化為 null 字串 [`""`]，如下所示：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]  
  
 對於大部分函式結果，您可以單純依值傳回 `CString` 物件。  
  
## <a name="see-also"></a>另請參閱  
 [字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CString 引數傳遞](../atl-mfc-shared/cstring-argument-passing.md)


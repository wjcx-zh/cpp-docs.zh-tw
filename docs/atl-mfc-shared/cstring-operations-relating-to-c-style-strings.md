---
title: "CString Operations Relating to C-Style Strings | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "casting CString objects"
  - "CString objects, 基本作業"
  - "C-style strings"
  - "MFC [C++], string handling class"
  - "null 值, Null-terminated string conversion"
  - "standard run-time library string functions"
  - "string arguments"
  - "字串轉換 [C++], C-style strings"
  - "字串函式"
  - "字串 [C++], class CString"
  - "字串 [C++], in C"
  - "字串 [C++], string operations"
ms.assetid: 5048de8a-5298-4891-b8a0-c554b5a3ac1b
caps.latest.revision: 17
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CString Operations Relating to C-Style Strings
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A[CString](../atl-mfc-shared/using-cstring.md) 物件包含字元字串資料。  `CString` 繼承類別範本 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 中定義的[方法和運算子](../atl-mfc-shared/reference/cstringt-class.md)集合，以處理字串資料。  \(`CString` 是會特製化 `CStringT` 以處理 `CString` 所支援之字元資料類型的 `typedef`。\)  
  
 `CString` 不像 C 樣式的 null 終止字串一樣在內部存放字元資料。  相對地，`CString` 會追蹤字元資料的長度，以便能更安全地監看資料及其所需空間。  
  
 `CString` 會接受 C 樣式字串，且提供以 C 樣式字串來存取字元資料的方式。  本主題包含下列各節，解釋如何使用 `CString` 物件，就彷彿其為 C 樣式的 null 終止字串。  
  
-   [轉換成 C 樣式的 null 終止字串](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)  
  
-   [使用標準執行階段程式庫字串函式](#_core_working_with_standard_run.2d.time_library_string_functions)  
  
-   [直接修改 CString 內容](#_core_modifying_cstring_contents_directly)  
  
-   [使用 CString 物件搭配變數引數函式](#_core_using_cstring_objects_with_variable_argument_functions)  
  
-   [指定 CString 正式參數](#_core_specifying_cstring_formal_parameters)  
  
##  <a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a> 使用 CString 做為 C 樣式的 Null 終止字串  
 若要使用 `CString` 物件做為 C 樣式的字串，請將物件轉型為 `LPCTSTR`。  在下列範例中，`CString` 會傳回唯讀 C 樣式 null 終止字串的指標。  `strcpy` 函式會將一份 C 樣式字串放在變數 `myString`。  
  
```  
CString aCString = "A string";  
char myString[256];  
strcpy(myString, (LPCTSTR)aCString);  
  
```  
  
 您可以使用 `CString` 方法，例如 `SetAt`，來修改字串物件中的個別字元。  不過，`LPCTSTR` 指標是暫時性的，在對 `CString` 做了任何變更後便會失效。  `CString` 也可能超出範圍而自動遭刪除。  我們建議您每次使用時都取得 `CString` 物件的全新 `LPCTSTR` 指標。  
  
 有時候您可能需要一份 `CString` 資料以便直接修改。  請使用更安全的函式 `strcpy_s` \(或 Unicode\/MBCS 可攜式 `_tcscpy_s`\) 將 `CString` 物件複製到個別的緩衝區。  在這裡，字元可以安全地修改，如下列範例所示。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/CPP/cstring-operations-relating-to-c-style-strings_1.cpp)]  
  
> [!NOTE]
>  `strcpy_s` \(或 Unicode\/MBCS 可攜式 `_tcscpy_s`\) 的第三個引數是 `const``wchar_t*` \(Unicode\) 或 `const``char*` \(ANSI\)。  上述範例會為這個引數傳遞一個 `CString`。  C\+\+ 編譯器自動套用為 `CString` 類別定義的轉換函式，它會將 `CString` 轉換成 `LPCTSTR`。  定義從一個類型到另一個類型的轉型作業功能，是 C\+\+ 最實用的功能之一。  
  
##  <a name="_core_working_with_standard_run.2d.time_library_string_functions"></a> 使用標準執行階段程式庫字串函式  
 您應該能夠找到 `CString` 方法以執行任何字串作業，且對於這些作業您可能考慮使用標準 C 執行階段程式庫字串函式，例如 `strcmp` \(或 Unicode\/MBCS 可攜式 `_tcscmp`\)。  
  
 如果您必須使用 C 執行階段字串函式，可以使用\_core\_using\_cstring\_as\_a\_c.2d.style\_null.2d.terminated\_string 中所描述的技巧。  您可以將 `CString` 物件複製到相等的 C 樣式字串緩衝區、在緩衝區上執行作業，然後將產生的 C 樣式字串指派回 `CString` 物件。  
  
##  <a name="_core_modifying_cstring_contents_directly"></a> 直接修改 CString 內容  
 在大多數情況下，您應該使用 `CString` 成員函式來修改 `CString` 物件的內容，或是將 `CString` 轉換成 C 樣式的字元字串。  
  
 有一些情況下，也可以直接修改 `CString` 內容，例如，當您使用需要字元緩衝區的作業系統函式時。  
  
 `GetBuffer` 和 `ReleaseBuffer` 方法提供對 `CString` 物件內部字元緩衝區的存取，並讓您直接修改它。  下列步驟顯示如何使用這些函式來達成此目的。  
  
#### 使用 GetBuffer 和 ReleaseBuffer 存取 CString 物件的內部字元緩衝區  
  
1.  針對 `CString` 物件呼叫 `GetBuffer` 並指定您需要的緩衝區長度。  
  
2.  使用 `GetBuffer` 傳回的指標直接將字元寫入 `CString` 物件。  
  
3.  針對 `CString` 物件呼叫 `ReleaseBuffer`，更新所有內部 `CString` 狀態資訊，例如字串的長度。  直接修改 `CString` 物件的內容之後，您必須先呼叫 `ReleaseBuffer` 然後才呼叫任何其他 `CString` 成員函式。  
  
##  <a name="_core_using_cstring_objects_with_variable_argument_functions"></a> 使用 CString 物件搭配變數引數函式  
 有些 C 函數接受可變數目的引數。  值得注意的範例是 `printf_s`。  由於這種函式的宣告方式，編譯器無法確定引數的類型，且無法判斷對每個引數要執行哪種轉換作業。  因此，很重要的一點是您要在傳遞 `CString` 物件給接受可變數目之引數的函式時，使用明確的類型轉型。  
  
 若要在可變引數函式中使用 `CString` 物件，請明確地將 `CString` 轉型成 `LPCTSTR` 字串，如下列範例所示。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/CPP/cstring-operations-relating-to-c-style-strings_2.cpp)]  
  
##  <a name="_core_specifying_cstring_formal_parameters"></a> 指定 CString 正式參數  
 對於需要字串引數的大部分函式，最好是將函式原型中的正式參數指定為字元 \(`LPCTSTR`\) 的 `const` 指標，而不是 `CString`。  當正式參數指定為字元的 `const` 指標時，可以傳遞指標給 `TCHAR` 陣列、常值字串 \[`"hi there"`\] 或 `CString` 物件。  `CString` 物件將會自動轉換成 `LPCTSTR`。  只要是您能使用 `LPCTSTR` 的位置，您就也能使用 `CString` 物件。  
  
 如果將不會修改引數，則也可以指定正式參數做為常數字串參考 \(也就是 `const``CString&`\)。  如果函式將修改字串，請捨棄 `const` 修飾詞。  如果想要使用預設 null 值，請將它初始化為 null 字串 \[`""`\]，如下所示：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/CPP/cstring-operations-relating-to-c-style-strings_3.cpp)]  
  
 對於大部分函式結果，您可以單純依值傳回 `CString` 物件。  
  
## 請參閱  
 [字串](../atl-mfc-shared/strings-atl-mfc.md)   
 [CString Argument Passing](../atl-mfc-shared/cstring-argument-passing.md)
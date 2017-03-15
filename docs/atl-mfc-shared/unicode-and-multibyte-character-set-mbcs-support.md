---
title: "Unicode 及多位元組字元集 (MBCS) 支援 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++]，字元集支援"
  - "MBCS [C++]，字串和 MFC 支援"
  - "字串 [C++]，MFC 中的 MBCS 支援"
  - "字元集 [C++]，多位元組"
  - "Unicode [C++]，MFC 字串"
  - "Unicode [C++]，字串物件"
  - "字串 [C++]，Unicode"
  - "字串 [C++]，字元集支援"
ms.assetid: 44b3193b-c92d-40c5-9fa8-5774da303cce
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Unicode 及多位元組字元集 (MBCS) 支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

某些語言，例如日文和中文，都具有大型字元集。  對這些市場的程式支援，以下為 Microsoft Foundation Class Library \(MFC\) 程式庫提供對管理大型字元集的兩種不同方法啟用:  
  
-   [Unicode](#_core_mfc_support_for_unicode_strings)  
  
-   [多位元組字元集 \(MBCS\)](#_core_mfc_support_for_mbcs_strings)  
  
 對於所有新開發，您應該使用 Unicode。  
  
##  <a name="_core_mfc_support_for_unicode_strings"></a> Unicode 字串的 MFC 支援  
 整個類別庫為 Unicode 字元和字串是有條件地啟用。  特別是， [CString](../atl-mfc-shared/reference/cstringt-class.md) 類別都支援 Unicode。  
  
|||||  
|-|-|-|-|  
|UAFXCW.LIB|UAFXCW.PDB|UAFXCWD.LIB|UAFXCWD.PDB|  
|MFC*xx*U.LIB|MFC*xx*U.PDB|MFC*xx*U.DLL|MFC*xx*UD.LIB|  
|MFC*xx*UD.PDB|MFC*xx*UD.DLL|MFCS*xx*U.LIB|MFCS*xx*U.PDB|  
|MFCS*xx*UD.LIB|MFCS*xx*UD.PDB|MFCM*xx*U.LIB|MFCM*xx*U.PDB|  
|MFCM*xx*U.DLL|MFCM*xx*UD.LIB|MFCM*xx*UD.PDB|MFCM*xx*UD.DLL|  
  
 \(*xx* 表示檔案的版本號碼;例如， "80" 表示第 8.0 版\)。  
  
 `CString` 是基於 `TCHAR` 資料型別。  如果符號 `_UNICODE` 被定義為用來組建程式，則 `TCHAR` 是被定義為16 位元字元編碼類型的 `wchar_t`型別。  否則， `TCHAR` 會被定義為正常 8 位元字元編碼方式的 `char`。  因此，在 Unicode 中， `CString` 是 16 位元字元所組成。  如果沒有 Unicode，它是由 `char`型別組成字元。  
  
 若要完成 Unicode 程式設計應用程式，您也必須:  
  
-   使用 `_T` 巨集條件式程式碼常值字串是可攜式至 Unicode。  
  
-   當您將字串傳出，請注意函式的引數是需要字元的長度或是位元的長度。  如果您使用 Unicode 字串，此差異是非常重要的。  
  
-   使用 C 執行階段字串處理函式的可攜式版本。  
  
-   對於字元和字元指標，請使用下列資料型別:  
  
    -   在`TCHAR` 中您會用到 `char`。  
  
    -   在`LPTSTR` 中您會用到 `char*`。  
  
    -   在`LPCTSTR` 中您會用到 `const char*`。  `CString` 提供 `LPCTSTR` 運算子給在 `CString` 和 `LPCTSTR`之間的轉換。  
  
 `CString` 也提供 Unicode 感知建構函式、指派運算子和比較運算子。  
  
 如需程式設計的 Unicode 的相關資訊，請參閱 [Unicode 主題](../mfc/unicode-in-mfc.md)。  [執行階段程式庫參考](../c-runtime-library/c-run-time-library-reference.md) 定義它所有的字串處理函式的可攜式版本。  請參閱 [國際化](../c-runtime-library/internationalization.md)分類。  
  
##  <a name="_core_mfc_support_for_mbcs_strings"></a> MFC 所支援的 MBCS 字串  
  
> [!WARNING]
>  MBCS 字串是舊版技術，不應該在新的專案中使用。  下列資訊適用於您需要維護現存 MBCS 程式碼的案例，而且不是可以升級程式碼就可使用 Unicode。  
  
 類別庫也可使用多位元組字元集，不過只有雙位元組字元集 \(DBCS\)。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] \(含\) 以後版本， MFC DLL 的 MBCS 版是在 Visual Studio 中可用增益集從 MSDN 下載網站。  如需詳細資訊，請參閱 [MFC MBCS DLL Add\-in](../mfc/mfc-mbcs-dll-add-on.md)。  
  
 在多位元組字元集，一個字元的長度可以是一個或兩個位元組。  如果長度是兩個位元組，它的第一個位元 「前導位元」 是來自已選取的特定範圍，此範圍是由正在使用的字碼頁所訂。  前導位元」和「後隨位元」一起決定特有的字元編碼方式。  
  
 如果符號 `_MBCS` 為您的程式中定義基於`CString` 的型別 `TCHAR`，則對應至`char`。  您可以決定在 `CString` 的哪個位元組是前導位元組和後隨位元組。  C 執行階段程式庫可以提供此判斷。  
  
 在 DBCS 下，特定字串可以包含任何單一位元組的 ANSI 字元、所有雙位元組字元或兩者的組合。  這些可能需要在剖析字串做特殊處理。  這包括 `CString` 物件。  
  
> [!NOTE]
>  Unicode MFC 中的字串還原序列化可以讀取應用程式版本執行的 Unicode 和 MBCS 字串，無論您在哪個應用程式版本上執行。  您的資料檔案是可攜式在 Unicode 和 MBCS 版本程式之間。  
  
 這些被呼叫的`CString` 成員函式使用 C 執行階段函式特殊泛型文字版本，或是使用 Unicode 感知的函式。  因此，例如，如果 `CString` 函式通常會呼叫 `strcmp`，則它會呼叫對應的泛用文字函式 `_tcscmp` 。  根據符號 `_MBCS` 和 `_UNICODE` 如何定義， `_tcscmp` 對應如下:  
  
|||  
|-|-|  
|`_MBCS` 已定義|`_mbscmp`|  
|`_UNICODE` 已定義|`wcscmp`|  
|這些符號均未定義|`strcmp`|  
  
> [!NOTE]
>  `_MBCS` 和 `_UNICODE` 的符號是互斥 \(Mutually Exclusive\) 的選項。  
  
 泛用文字所有的函式對應執行階段字串處理常式會在 [C 執行階段程式庫參考](../c-runtime-library/c-run-time-library-reference.md)中討論。  尤其是請參閱 [國際化](../c-runtime-library/internationalization.md)。  
  
 同樣地，在 `CString` 方法會使用「泛型」資料型別對應。  若要啟用 MBCS 和 Unicode， MFC 會使用 `char``char*`的 `TCHAR` ， `const char*`的 `LPTSTR` 和 `LPCTSTR` 。  這會保證 Unicode 或 MBCS 的正確對應。  
  
## 請參閱  
 [字串](../atl-mfc-shared/strings-atl-mfc.md)   
 [字串操作](../c-runtime-library/string-manipulation-crt.md)
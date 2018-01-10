---
title: "設定 (MBCS) 支援的 Unicode 和多位元組字元 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.assetid: 44b3193b-c92d-40c5-9fa8-5774da303cce
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea35f36012eb893d8784c626c533690e97b517e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode 及多位元組字元集 (MBCS) 支援
某些程式語言，例如日文和中文有大型的字元集。 若要支援這些市場程式設計，Microsoft Foundation 類別庫 (MFC) 會啟用兩個不同的方法來處理大型字元集：  
  
-   [Unicode](#_core_mfc_support_for_unicode_strings)  
  
-   [多位元組字元集 (MBCS)](#_core_mfc_support_for_mbcs_strings)  
  
 您應該使用 Unicode 的所有新的開發。  
  
##  <a name="_core_mfc_support_for_unicode_strings"></a>MFC 支援的 Unicode 字串  
 Unicode 字元和字串有條件地啟用整個類別程式庫。 特別是，類別[CString](../atl-mfc-shared/reference/cstringt-class.md)與 Unicode 相容。  
  
|||||  
|-|-|-|-|  
|UAFXCW。LIB|UAFXCW。PDB|UAFXCWD。LIB|UAFXCWD。PDB|  
|MFC*xx*U.LIB|MFC*xx*U.PDB|MFC*xx*U.DLL|MFC*xx*UD。LIB|  
|MFC*xx*UD。PDB|MFC*xx*UD。DLL|MFCS*xx*U.LIB|MFCS*xx*U.PDB|  
|MFCS*xx*UD。LIB|MFCS*xx*UD。PDB|MFCM*xx*U.LIB|MFCM*xx*U.PDB|  
|MFCM*xx*U.DLL|MFCM*xx*UD。LIB|MFCM*xx*UD。PDB|MFCM*xx*UD。DLL|  
  
 (*xx*代表版本號碼的檔案; 例如，'80' 表示 8.0 版。)  
  
 `CString`根據`TCHAR`資料型別。 如果符號`_UNICODE`為您的程式的組建定義`TCHAR`定義為型別`wchar_t`、 16 位元的字元編碼類型。 否則，`TCHAR`定義為`char`，一般的 8 位元字元編碼方式。 因此，在 Unicode，`CString`是 16 位元的字元所組成。 而不是 Unicode，它以字元組成之型別的`char`。  
  
 您的應用程式的完整 Unicode 程式設計，您也必須：  
  
-   使用`_T`巨集，以條件式程式碼常值字串可以移植到 Unicode。  
  
-   當您傳遞字串時，請注意函式引數是需要以字元為單位的長度或以位元組為單位的長度。 差異是很重要，如果您使用 Unicode 字串。  
  
-   使用 C 執行階段的字串處理函式的可攜式的版本。  
  
-   用於字元和字元指標的下列資料類型：  
  
    -   `TCHAR`您會使用`char`。  
  
    -   `LPTSTR`您會使用`char*`。  
  
    -   `LPCTSTR`您會使用`const char*`。 `CString`提供的運算子`LPCTSTR`之間進行轉換`CString`和`LPCTSTR`。  
  
 `CString`也提供 Unicode 感知的建構函式、 指派運算子和比較運算子。  
  
 如需 Unicode 程式設計的相關資訊，請參閱[Unicode 主題](../mfc/unicode-in-mfc.md)。 [執行階段程式庫參考](../c-runtime-library/c-run-time-library-reference.md)定義的所有字串處理函式的可攜式版本。 請參閱類別[國際化](../c-runtime-library/internationalization.md)。  
  
##  <a name="_core_mfc_support_for_mbcs_strings"></a>MFC 支援 MBCS 字串  
  
 類別庫也會啟用為多位元組字元集，但僅適用於雙位元組字元集 (DBCS) 會設定。  
  
 在多位元組字元集的字元可以是一個或兩個位元組寬。 如果兩個位元組寬，其第一個位元組是特殊 「 前導位元組 」 也就是從特定的範圍，取決於哪一個程式碼正在使用中頁面的選擇。 結合在一起的開頭和 「 後隨位元組 」 指定唯一的字元編碼方式。  
  
 如果符號`_MBCS`程式類型的組建定義`TCHAR`，所在`CString`為基礎，會對應至`char`。 它是由您決定哪一個位元組決定`CString`是前導位元組，以及哪些是後隨位元組。 C 執行階段程式庫提供可協助您判斷的函式。  
  
 在 DBCS 中，給定的字串可以包含所有單一位元組的 ANSI 字元、 所有雙位元組字元或兩者的組合。 這些可能需要特別注意，剖析字串。 這包括`CString`物件。  
  
> [!NOTE]
>  在 MFC 中的 Unicode 字串序列化可以讀取 Unicode 和 MBCS 字串，不論您所執行的應用程式的版本。 您的資料檔案可移植的程式 Unicode 和 MBCS 版本之間。  
  
 `CString`成員函式會使用特殊的 「 泛型文字 」 版本的 C 執行階段函式所呼叫，或者使用 Unicode 感知函式。 因此，例如，如果`CString`函式通常會呼叫`strcmp`，它會呼叫對應的一般文字函式`_tcscmp`改為。 如何根據符號`_MBCS`和`_UNICODE`所定義，`_tcscmp`對應，如下所示：  
  
|||  
|-|-|  
|`_MBCS`定義|`_mbscmp`|  
|`_UNICODE`定義|`wcscmp`|  
|沒有定義的符號|`strcmp`|  
  
> [!NOTE]
>  符號`_MBCS`和`_UNICODE`互為獨佔模式。  
  
 中會討論的所有執行階段的字串處理常式的一般文字函式對應[C 執行階段程式庫參考](../c-runtime-library/c-run-time-library-reference.md)。 特別是，請參閱[國際化](../c-runtime-library/internationalization.md)。  
  
 同樣地，`CString`方法使用 「 泛型 」 的資料型別對應來實作。 若要啟用 MBCS 和 Unicode，MFC 會使用`TCHAR`如`char`，`LPTSTR`如`char*`，和`LPCTSTR`如`const char*`。 這樣可確保正確的對應為 MBCS 或 Unicode。  
  
## <a name="see-also"></a>請參閱  
 [字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [字串操作](../c-runtime-library/string-manipulation-crt.md)


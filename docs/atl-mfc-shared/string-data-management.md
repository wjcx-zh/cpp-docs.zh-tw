---
title: "字串資料管理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad7a17b1b34375fcb45019bcaf8878757288a290
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="string-data-management"></a>字串資料管理
Visual c + + 提供數種方式管理字串資料：  
  
-   [字串操作](../c-runtime-library/string-manipulation-crt.md)處理 C 樣式 null 終止字串  
  
-   管理字串的 Win32 API 函式  
  
-   MFC 類別[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)，這樣會提供彈性、 可調整大小的字串物件  
  
-   類別[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)，可獨立於 MFC 的字串物件與相同的功能`CString`  
  
 幾乎所有的程式會使用字串資料。 MFC 的`CString`類別通常是有彈性的字串處理的最佳解決方案。 7.0 版中，從開始`CString`可以用於 MFC 或 MFC 無關的程式。 這兩個執行階段程式庫和`CString`支援包含多位元組 （寬） 字元，如同 MBCS 或 Unicode 程式設計的字串。  
  
 本文說明類別庫會提供字串操作相關的通用服務。 本文涵蓋的主題包括：  
  
-   [Unicode 和 MBCS 提供可攜性](#_core_unicode_and_mbcs_provide_portability)  
  
-   [CStrings 和 const char 指標](#_core_cstrings_and_const_char_pointers)  
  
-   [CString 參考計數](#_core_cstring_reference_counting)  
  
 [CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)類別會提供支援操作字串。 它被要取代和擴充通常 C 執行階段程式庫字串封裝所提供的功能。 `CString`類別提供成員函式和簡化的字串處理，類似於 Basic 中的運算子。 類別也會提供建構函式和運算子建構、 指派和比較**CStrings**和標準 c + + 字串資料類型。 因為`CString`不衍生自`CObject`，您可以使用`CString`獨立大部分 Microsoft Foundation 類別庫 (MFC) 的物件。  
  
 `CString`物件會遵循"value 語意"。 A`CString`物件都代表唯一的值。 想像`CString`為實際的字串，而不是做為字串的指標。  
  
 A`CString`物件都代表一連串字元的變數數目。 `CString`物件可以視為的字元陣列。  
  
##  <a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode 和 MBCS 提供可攜性  
 MFC 3.0 版和更新版本中，MFC，包括`CString`，已啟用 Unicode 和多位元組字元集 (MBCS)。 這個支援可讓您更輕鬆地撰寫可攜式應用程式，您可以建置為 ANSI 或 Unicode 字元。 若要啟用此可攜性，在每個字元`CString`物件屬於類型**TCHAR**，其定義為`wchar_t`如果定義符號**_UNICODE**當您建置應用程式，或做為`char`如果不是。 A`wchar_t`字元是 16 位元寬。 如果您使用符號來建置啟用 MBCS **_MBCS**定義。 其中一種建置 MFC **_MBCS**符號 （針對 NAFX 文件庫中） 或**_UNICODE** （適用於 UAFX 文件庫中） 的符號定義。  
  
> [!NOTE]
>  `CString`中的範例並隨附文件常值字串的格式正確的 Unicode 可攜性的字串顯示上，使用**_T**巨集，它會轉譯到表單的常值字串：  
  
 `L"literal string"`  
  
> [!NOTE]
>  編譯器會以 Unicode 字串其中。 例如，下列程式碼：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]  
  
> [!NOTE]
>  如果轉換為 Unicode 字串**_UNICODE**定義，或為 ANSI 字串如果不是。 如需詳細資訊，請參閱文章[Unicode 和多位元組字元集 (MBCS) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。  
  
 A`CString`物件最多可以儲存**INT_MAX** (2,147,483,647) 個字元。 **TCHAR**資料類型用來取得或設定內的個別字元`CString`物件。 與不同的字元陣列，是`CString`類別具有內建記憶體配置功能。 這可讓`CString`物件以視需要自動成長 (亦即，您不必擔心成長`CString`物件大小以容納較長的字串)。  
  
##  <a name="_core_cstrings_and_const_char_pointers"></a>CStrings 和 const char 指標  
 A`CString`物件也可以做為常值的 C 樣式字串 ( `PCXSTR`，這是與相同**const char\*** 如果是不在 Unicode)。 [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr)轉換運算子可讓`CString`來自由取代函式呼叫中的字元指標的物件。 **CString (LPCWSTR** `pszSrc` **)**建構函式可讓用來取代的字元指標`CString`物件。  
  
 不會嘗試對摺疊`CString`物件。 如果您讓這兩個`CString`物件包含`Chicago`，例如，在字元`Chicago`會儲存在兩個地方。 （這可能不是 true 的未來版本的 MFC，因此您不應依賴它。）  
  
> [!NOTE]
>  使用[CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)成員函式，當您需要直接存取`CString`的非常數指標的字元。  
  
> [!NOTE]
>  使用[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)和[CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring)成員函式以配置，並設定`BSTR`Automation （先前稱為 OLE Automation） 中使用的物件。  
  
> [!NOTE]
>  如果可行，配置`CString`框架上，而不是在堆積上的物件。 這樣會節省記憶體，並簡化參數傳遞。  
  
 `CString`類別未實作為 Mfc 程式庫集合類別，不過`CString`物件確實可以儲存為集合中的項目。  
  
##  <a name="_core_cstring_reference_counting"></a>CString 參考計數  
 根據 MFC 4.0 版，當[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)複製的物件，MFC 會遞增參考計數，而不是將資料複製。 這可讓傳遞參數值和傳回`CString`物件的值更有效率。 這些作業會導致複製建構函式呼叫，有時候不只一次。 遞增參考計數減少這些一般作業的負擔，並使用 「 建立`CString`更能吸引選項。  
  
 為每個複本被終結時，原始物件的參考計數會遞減。 原始`CString`物件並不會終結其參考計數減為零之前。  
  
 您可以使用`CString`成員函式[CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)停用或啟用參考計數。  
  
## <a name="see-also"></a>請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)


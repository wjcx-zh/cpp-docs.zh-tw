---
title: "String Data Management | Microsoft Docs"
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
  - "Unicode, string objects"
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# String Data Management
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 提供多種處理字串資料:  
  
-   的[字串操作](../c-runtime-library/string-manipulation-crt.md) 與 C\-Style null 結尾字串時使用。  
  
-   處理字串的 Win32 API 函式  
  
-   MFC 的類別 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)，提供彈性，可調整大小的資料物件。  
  
-   將 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)，提供 MFC 獨立資料物件提供功能和 `CString`  
  
 幾乎所有程式與字串資料。  MFC 的 `CString` 類別通常是彈性字串處理的最佳的解決方案。  從 7.0 版開始， `CString` 可用於 MFC 或 MFC 獨立應用程式。  執行階段程式庫和 `CString` 支援包含多位元組 \(寬字元\) 的字串，表示 Unicode 或 MBCS 程式設計。  
  
 本文說明通用服務類別庫 \(Class Library\) 提供與字串管理。  本文內容涵蓋的主題包括:  
  
-   [Unicode 和 MBCS 提供可攜性](#_core_unicode_and_mbcs_provide_portability)  
  
-   [CStrings 和 const 會輸出指標](#_core_cstrings_and_const_char_pointers)  
  
-   [CString 參考計數。](#_core_cstring_reference_counting)  
  
 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) 類別來操作字串的支援。  用來取代並擴充 C 執行階段程式庫字串套件通常提供的功能。  `CString` 類別提供成員函式和運算子處理簡化的字串，類似於在基本出現的警告。  類別會提供建構，指派和比較 **CStrings** 和 Standard C\+\+ 字串資料型別也提供建構函式和運算子。  由於 `CString` 從 `CObject`並非衍生自類別，您可以個別多數 MFC 程式庫使用 `CString` MFC 物件 \(\)。  
  
 `CString` 物件後面加上「實值語意」。`CString` 物件表示唯一值。  視為 `CString` 做為實際字串，而不是指向字串。  
  
 `CString` 物件代表字元的可變數目的序列。  `CString` 物件設想為字元陣列。  
  
##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode 和 MBCS 提供可攜性  
 MFC 3.0 \(含\) 以後版本， MFC，包括 `CString`，就 Unicode 和多位元組字元集 \(MBCS\) 啟用。  這項支援可讓您撰寫可為 Unicode 或 ANSI 字元建立的可移植應用程式。  若要啟用此可攜性，在 `CString` 物件的每一個字元型別 **TCHAR**，定義為 `wchar_t` ，如果定義符號 **\_UNICODE** ，當您建置應用程式，還是 `char` 。  `wchar_t` 字元寬度是 16 位元。  如果您以符號 **\_MBCS** 建置定義，都支援 MBCS。  MFC 會 **\_MBCS** 符號 \(NAFX 程式庫\) 或 \(適用於 UAFX 程式庫\) 中定義的 **\_UNICODE** 符號建置。  
  
> [!NOTE]
>  `CString` 範例中的這個和字串中隨附的文件顯示為 Unicode 可攜性正確格式的常值字串，使用 **\_T** 巨集，其轉譯常值字串的格式:  
  
 `L"literal string"`  
  
> [!NOTE]
>  哪些編譯器將 Unicode 字串。  例如，下列程式碼：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/CPP/string-data-management_1.cpp)]  
  
> [!NOTE]
>  如果 **\_UNICODE** 定義或為 ANSI 字串，如果沒有，會轉譯為 Unicode 字串。  如需詳細資訊，請參閱本文 [Unicode 及多位元組字元集 \(MBCS\) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。  
  
 `CString` 物件可儲存由 **INT\_MAX** 決策 \(2,147,483,647\) 字元。  **TCHAR** 資料型別是用來取得或設定在 `CString` 的個別字元的物件。  不同的字元陣列， `CString` 類別具有固定記憶體配置功能。  這可讓 `CString` 物件自動變大視需要 \(即您不必擔心成長到適當的較長的字串。 `CString` 物件\)。  
  
##  <a name="_core_cstrings_and_const_char_pointers"></a> CStrings 和 const 會輸出指標  
 `CString` 物件也可以如同 C\-Style 字串常值 \( `PCXSTR`，與 **const char\*** ，如果不在 Unicode 之下\)。  [CSimpleStringT::operator PCXSTR](../Topic/CSimpleStringT::operator%20PCXSTR.md) 轉換運算子可讓 `CString` 物件是在函式呼叫的字元指標自由替代。  **CString\( LPCWSTR**`pszSrc`**\)** 建構函式允許字元指標 `CString` 會替代物件。  
  
 不會嘗試摺疊 `CString` 物件。  如果您建立包含 `Chicago`的兩 `CString` 物件，例如，在 `Chicago` 字元在兩個位置中。  \(這不是真正的 MFC 未來版本，因此，您不應使用它\)。  
  
> [!NOTE]
>  在中，您必須直接存取 `CString` 做為非常數指標字元時，請使用 [CSimpleStringT::GetBuffer](../Topic/CSimpleStringT::GetBuffer.md) 和 [CSimpleStringT::ReleaseBuffer](../Topic/CSimpleStringT::ReleaseBuffer.md) 成員函式。  
  
> [!NOTE]
>  使用 [CStringT::AllocSysString](../Topic/CStringT::AllocSysString.md) 和 [CStringT::SetSysString](../Topic/CStringT::SetSysString.md) 成員函式配置和設定用於自動化的 `BSTR` 物件 \(先前稱為 OLE Automation\)。  
  
> [!NOTE]
>  可能的話，請將框架中的 `CString` 物件而不是在堆積上。  這可以節省記憶體並簡化參數傳遞。  
  
 `CString` 類別不是實作為 MFC 程式庫集合類別，不過， `CString` 物件可能必須儲存為項目集合中。  
  
##  <a name="_core_cstring_reference_counting"></a> CString 參考計數。  
 根據 MFC 4.0 版中，當物件， [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) 複製時， MFC 會遞增參考計數而不是重複的資料。  這是透過參數與傳回的值相同。 `CString` 物件由更有效的值。  這些作業會讓複製建構函式時，會呼叫一次以上。  加入參考計數減少這些共同作業的額外負荷且使用 `CString` 更引人注目的選項。  
  
 在終結每個複本，原始物件的參考計數會遞減。  不會終結原始 `CString` 物件，直到它的參考計數減少為零。  
  
 您可以使用 `CString` 成員函式 [CSimpleStringT::LockBuffer](../Topic/CSimpleStringT::LockBuffer.md) 和 [CSimpleStringT::UnlockBuffer](../Topic/CSimpleStringT::UnlockBuffer.md) 停用或啟用參考計數。  
  
## 請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)
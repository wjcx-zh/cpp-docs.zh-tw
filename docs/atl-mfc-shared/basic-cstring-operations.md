---
title: "Basic CString Operations | Microsoft Docs"
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
  - "字元, accessing in CStrings"
  - "CString objects"
  - "CString objects, 基本作業"
  - "literal strings, CString operations"
  - "字串比較, CString operations"
  - "字串常值, CString operations"
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Basic CString Operations
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題將說明下列基本 [CString](../atl-mfc-shared/reference/cstringt-class.md) 作業:  
  
-   [建立從 CString 標準 C 常值字串物件。](#_core_creating_cstring_objects_from_standard_c_literal_strings)  
  
-   [在 CString 存取個別字元。](#_core_accessing_individual_characters_in_a_cstring)  
  
-   [串連兩個 CString 物件](#_core_concatenating_two_cstring_objects)  
  
-   [比較物件 CString](#_core_comparing_cstring_objects)  
  
-   [轉換成 CString 物件](#_core_converting_cstring_objects)  
  
 `Class CString` 根據類別樣板 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)。  `CString` 是 `CStringT``typedef` 。  正確， `CString` 是 `CStringT`的 *明確特製化的*`typedef` ，是一種常見方式使用類別樣板定義類別。  相同的已定義的類別是 `CStringA` 和 `CStringW`。  如需明確特製化的詳細資訊，請參閱 [類別樣板具現化](../Topic/Class%20Template%20Instantiation.md)。  
  
 `CString`、 `CStringA`和 `CStringW` 在 atlstr.h 中定義。  在`CStringT` cstringt.h 中定義。  
  
 `CString`、 `CStringA`和 `CStringW` 一切取得 `CStringT` 定義的方法和運算子的一組為其支援的字串資料的使用。  某些方法重複的和，在某些情況下，以上的 C 執行階段程式庫的資料服務。  
  
 注意: `CString` 為原生類別。  對於要用在 C\+\+. \+\+\/CLI Managed 專案的資料類別，請使用 `System.String`。  
  
##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> 若要從標準 C 常值字串的物件 CString  
 如同您可以指派一 `CString` 物件與另一個，您就可以將 C\-Style 常值字串加入至 `CString` 。  
  
-   指派 C\+\+. 常值字串的值為 `CString` 物件。  
  
     [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_1.cpp)]  
  
-   指派指定的 `CString` 的值至另一 `CString` 物件。  
  
     [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_2.cpp)]  
  
     會 `CString` 物件指派給另一位成員時， `CString` 物件的內容複製到其中。  因此，這兩個字串不會共用到組合字串的實際字元的參考。  如需如何使用 `CString` 物件的詳細資訊做為值，請參閱 [CString Semantics](../atl-mfc-shared/cstring-semantics.md)。  
  
    > [!NOTE]
    >  撰寫應用程式，使其可為 Unicode 或 ANSI 為使用 \_T 巨集，，程式碼的常值字串。  如需詳細資訊，請參閱 [Unicode 及多位元組字元集 \(MBCS\) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。  
  
##  <a name="_core_accessing_individual_characters_in_a_cstring"></a> 在 CString 存取個別字元。  
 您可以使用 `GetAt` 和 `SetAt` 方法，存取在 `CString` 物件的個別字元。  您也可以使用陣列元素或註標 \(Subscript\)，運算子 \(\) 而不是 `GetAt` 取得個別字元。  \(這是由索引類似存取陣列元素，介於標準 C\-Style 字串\)。`CString` 字元的索引值是以零起始。  
  
##  <a name="_core_concatenating_two_cstring_objects"></a> 串連兩個 CString 物件  
 若要串連兩個 `CString` 物件，請使用串連運算子 \(\+ 或 \+\=\)，如下所示。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_3.cpp)]  
  
 至少要串連運算子的引數 \(\+ 或 \+\=\) 必須是 `CString` 物件，不過，您可以提供其他引數使用固定的字串 \(例如， `"big"`\) 或 `char` \(例如， " x "\)。  
  
##  <a name="_core_comparing_cstring_objects"></a> 比較物件 CString  
 `Compare` 方法和\=\=運算子 `CString` 的。  `Compare`、 `operator==`和 `CompareNoCase` 是明確的 MBCS 和 Unicode 的; `CompareNoCase` 也不區分大小寫。  `CString``Collate` 方法會 `Compare`與地區設定 \(Locale\) 通常慢。  使用只有必須遵守排序規則由目前地區設定的 `Collate` 。  
  
 下表顯示在 C 執行階段程式庫中顯示可用的 [CString](../atl-mfc-shared/reference/cstringt-class.md) 比較函式及其對等 Unicode\/MBCS 可移植的函式。  
  
|CString 函式|MBCS 函式|Unicode 函式|  
|----------------|-------------|----------------|  
|`Compare`|`_mbscmp`|`wcscmp`|  
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|  
|`Collate`|`_mbscoll`|`wcscoll`|  
  
 `CStringT` 類別樣板定義關係運算子 \(\<， \<\=、\>\=， \>， \=\=，和\! \=\)，可提供 `CString`使用。  您可以使用這些運算子，如下列範例所示，您可以比較兩個 `CStrings` 。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/CPP/basic-cstring-operations_4.cpp)]  
  
##  <a name="_core_converting_cstring_objects"></a> 轉換成 CString 物件  
 如需轉換的詳細資訊 CString 對其他資料型別的詳細資訊，請參閱 [如何：在各種字串類型之間轉換](../text/how-to-convert-between-various-string-types.md)。  
  
## 使用 wcout 的 CString  
 如下列範例所示，若要使用 CString 和 `wcout` 必須明確轉型成 `const wchar_t*` 的物件:  
  
```  
CString cs("meow");  
  wcout << (const wchar_t*) cs << endl;  
  
```  
  
 沒有型別轉換， `void*` 和 `wcout` 列印物件的位址， `cs` 視為。  這個行為是由其本身正確且符合和 C\+\+ 標準樣板引數推算和多載解析之間的細微互動而產生。  
  
## 請參閱  
 [字串](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)   
 [類別樣板具現化](../Topic/Class%20Template%20Instantiation.md)   
 [類別樣板的明確特製化](../Topic/Explicit%20Specialization%20of%20Class%20Templates.md)   
 [類別樣板的部分特製化](../cpp/template-specialization-cpp.md)   
 [如何：在各種字串類型之間轉換](../text/how-to-convert-between-various-string-types.md)
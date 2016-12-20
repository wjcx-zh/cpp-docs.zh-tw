---
title: "CStringT Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CString"
  - "CStringT"
  - "ATL::CStringT"
  - "ATL.CStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringT class"
  - "shared classes, CStringT"
  - "字串 [C++], 在 ATL 中"
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
caps.latest.revision: 33
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStringT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示 `CStringT` 物件。  
  
## 語法  
  
```  
  
      template< typename   
      BaseType  
      , class   
      StringTraits  
       >  
class CStringT :   
public CSimpleStringT<   BaseType,   _CSTRING_IMPL_::_MFCDLLTraitsCheck<      BaseType,      StringTraits   >   ::c_bIsMFCDLLTraits>  
```  
  
#### 參數  
 `BaseType`  
 字串類別的配置類型。  可以是下列其中一項：  
  
-   `char` \(ANSI 字串\)。  
  
-   `wchar_t` \(Unicode 字串\)。  
  
-   **TCHAR** \(適用於 ANSI 和 Unicode 字串\)。  
  
 `StringTraits`  
 判斷字串類別需要 C 執行階段 \(CRT\) 程式庫支援，並放置字串資源。  可以是下列其中一項：  
  
-   **StrTraitATL\< wchar\_t** &#124; `char` &#124;  **ChTraitsCRT\< wchar\_t TCHAR** &#124; `char` &#124; **\> \> TCHAR**  
  
     類別需要 CRT 支援和搜尋在 `m_hInstResource` 指定模組的資源字串 \(應用程式模組類別的成員\)。  
  
-   **StrTraitATL\< wchar\_t** &#124; `char` &#124;  **ChTraitsOS\< wchar\_t TCHAR** &#124; `char` &#124; **\> \> TCHAR**  
  
     類別並不需要 CRT 支援並不需要搜尋 `m_hInstResource` 指定模組的資源字串 \(應用程式模組類別的成員\)。  
  
-   **StrTraitMFC\< wchar\_t** &#124; `char` &#124;  **ChTraitsCRT\< wchar\_t TCHAR** &#124; `char` &#124; **\> \> TCHAR**  
  
     使用標準 MFC 搜尋演算法，類別需要 CRT 支援和搜尋資源字串。  
  
-   **StrTraitMFC\< wchar\_t** &#124; `char` &#124;  **ChTraitsOS\< wchar\_t TCHAR** &#124; `char` &#124; **\> \> TCHAR**  
  
     使用標準 MFC 搜尋演算法，類別並不需要 CRT 支援並不會搜尋資源字串。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CStringT::CStringT](../Topic/CStringT::CStringT.md)|建構一個 `CStringT` 物件以各種方式。|  
|[CStringT::~CStringT](../Topic/CStringT::~CStringT.md)|終結 `CStringT` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CStringT::AllocSysString](../Topic/CStringT::AllocSysString.md)|從 `CStringT` 資料配置 `BSTR` 。|  
|[CStringT::AnsiToOem](../Topic/CStringT::AnsiToOem.md)|以 ANSI 字元集進行就地轉換成 OEM 字元集。|  
|[CStringT::AppendFormat](../Topic/CStringT::AppendFormat.md)|對現有的 `CStringT` Appends 格式的資料物件。|  
|[CStringT::Collate](../Topic/CStringT::Collate.md)|比較兩個字串 \(區分大小寫，請使用地區設定專用資訊\)。|  
|[CStringT::CollateNoCase](../Topic/CStringT::CollateNoCase.md)|比較兩個字串 \(不區分大小寫，請使用地區設定專用資訊\)。|  
|[CStringT::Compare](../Topic/CStringT::Compare.md)|比較兩個字串 \(區分大小寫\)。|  
|[CStringT::CompareNoCase](../Topic/CStringT::CompareNoCase.md)|比較兩個字串 \(不區分大小寫\)。|  
|[CStringT::Delete](../Topic/CStringT::Delete.md)|刪除一個字元或字元從字串。|  
|[CStringT::Find](../Topic/CStringT::Find.md)|尋找某個字元或子字串在較大的字串中。|  
|[CStringT::FindOneOf](../Topic/CStringT::FindOneOf.md)|尋找集合中的第一個符合的字元。|  
|[CStringT::Format](../Topic/CStringT::Format.md)|格式化字串， `sprintf` 。|  
|[CStringT::FormatMessage](../Topic/CStringT::FormatMessage.md)|格式化訊息字串。|  
|[CStringT::FormatMessageV](../Topic/CStringT::FormatMessageV.md)|使用變數引數清單，格式化訊息字串。|  
|[CStringT::FormatV](../Topic/CStringT::FormatV.md)|使用引數清單變數清單，格式化字串。|  
|[CStringT::GetEnvironmentVariable](../Topic/CStringT::GetEnvironmentVariable.md)|設定字串給指定的環境變數的值。|  
|[CStringT::Insert](../Topic/CStringT::Insert.md)|插入單一字元或子字串在字串中的指定索引。|  
|[CStringT::Left](../Topic/CStringT::Left.md)|擷取字串左側部分。|  
|[CStringT::LoadString](../Topic/CStringT::LoadString.md)|從 Windows 資源載入現有的 `CStringT` 物件。|  
|[CStringT::MakeLower](../Topic/CStringT::MakeLower.md)|將這個字串的所有字元轉換為小寫字母。|  
|[CStringT::MakeReverse](../Topic/CStringT::MakeReverse.md)|反轉字串。|  
|[CStringT::MakeUpper](../Topic/CStringT::MakeUpper.md)|將這個字串的所有字元為大寫字元。|  
|[CStringT::Mid](../Topic/CStringT::Mid.md)|擷取字串中間部分。|  
|[CStringT::OemToAnsi](../Topic/CStringT::OemToAnsi.md)|由 OEM 字元集進行就地轉換成 ANSI 字元集。|  
|[CStringT::Remove](../Topic/CStringT::Remove.md)|移除指定字串中的字元。|  
|[CStringT::Replace](../Topic/CStringT::Replace.md)|使用指定的字元與其他字元。|  
|[CStringT::ReverseFind](../Topic/CStringT::ReverseFind.md)|尋找在較大的字串中的字元，從結尾開始。|  
|[CStringT::Right](../Topic/CStringT::Right.md)|擷取字串右側部分。|  
|[CStringT::SetSysString](../Topic/CStringT::SetSysString.md)|資料設定的現有 `BSTR` 物件從 `CStringT` 物件。|  
|[CStringT::SpanExcluding](../Topic/CStringT::SpanExcluding.md)|從字串中擷取字元，從第一個字元開始，而不是在 `pszCharSet`判斷的字元集。|  
|[CStringT::SpanIncluding](../Topic/CStringT::SpanIncluding.md)|擷取集合只包含字元的子字串。|  
|[CStringT::Tokenize](../Topic/CStringT::Tokenize.md)|擷取在目標字串中指定的語彙基元。|  
|[CStringT::Trim](../Topic/CStringT::Trim.md)|修剪字串的所有前置和後端的空白字元。|  
|[CStringT::TrimLeft](../Topic/CStringT::TrimLeft.md)|前置空白字元的修剪從字串。|  
|[CStringT::TrimRight](../Topic/CStringT::TrimRight.md)|修剪字串的結尾的空白字元。|  
  
### 運算子  
  
|||  
|-|-|  
|[CStringT::operator \=](../Topic/CStringT::operator%20=.md)|指派新值給 `CStringT` 物件。|  
|[CStringT::operator \+](../Topic/CStringT::operator%20+.md)|串連兩個字串或字元和字串。|  
|[CStringT::operator \+\=](../Topic/CStringT::operator%20+=.md)|新字串串連到現有字串的結尾。|  
|[CStringT::operator \=\=](../Topic/CStringT::operator%20==.md)|判斷兩個字串是否為邏輯相等。|  
|[CStringT::operator \!\=](../Topic/CStringT::operator%20!=.md)|判斷兩個字串是否不在邏輯上是相等的。|  
|[CStringT::operator \<](../Topic/CStringT::operator%20%3C.md)|判斷左側的字串小於至右邊的字串小於。|  
|[CStringT::operator \>](../Topic/CStringT::operator%20%3E.md)|判斷左側的字串小於至右邊的字串大於。|  
|[CStringT::operator \<\=](../Topic/CStringT::operator%20%3C=.md)|判斷左側的字串是否小於或等於右邊的字串。|  
|[CStringT::operator \>\=](../Topic/CStringT::operator%20%3E=.md)|判斷左側的字串是否大於或等於右邊的字串。|  
  
## 備註  
 `CStringT` 從 [CSimpleStringT 類別](../../atl-mfc-shared/reference/csimplestringt-class.md)繼承。  進階功能，例如性質的內容，排序和搜尋，由 `CStringT`實作。  
  
> [!NOTE]
>  `CStringT` 物件可以擲回例外狀況。  當物件， `CStringT` 因任何原因，記憶體不足時發生。  
  
 `CStringT` 物件包括字元的可變長度的序列。  `CStringT` 提供使用語法的函式和運算子類似的基本概念。  串連運算子和比較運算子，以簡化的記憶體管理時，比一般字元字元陣列可讓 `CStringT` 物件易於使用。  
  
> [!NOTE]
>  雖然建立包含內嵌的 null 字元的 `CStringT` 執行個體本身，我們建議您針對它。  呼叫方法和運算子包含內嵌的 null 字元的 `CStringT` 物件可能會導致非預期的結果。  
  
 您可以使用 `BaseType` 和 `StringTraits` 不同的參數組合， `CStringT` 物件可以有下列型別，是由 ATL 程式庫預先定義的。  
  
 如果您在 ATL 應用程式:  
  
 `CString`、 `CStringA`和 `CStringW` 從 MFC DLL \(MF C90 .dll\) 匯出，絕不會從使用者 DLL。  這會防止 `CStringT` 是定義。  
  
> [!NOTE]
>  如果您遇到連結器錯誤，在匯出 `CString`\-從 MFC 擴充 DLL 的衍生類別 \(在 Visual C\+\+ .NET 2002 中同時套用運算如知識庫文件， 「連結錯誤，當您匯入 CString 衍生類別」\(CString\-Derived 時\)，則應該移除作業程式碼，，因為在 Visual C\+\+ .NET 2003 中已修正。  您可以在 MSDN Library CD\-ROM 或是在 [http:\/\/support.microsoft.com\/default.aspx?ln\=zh\-tw](http://support.microsoft.com/default.aspx?ln=zh-tw) 中找到知識庫文件。  
  
 下列字串型別在 MFC 架構應用程式內使用:  
  
|CStringT 型別|宣告|  
|-----------------|--------|  
|`CStringA`|一個 ANSI 字元型別字串具有 CRT 支援。|  
|`CStringW`|一個 Unicode 字元型別字串具有 CRT 支援。|  
|`CString`|ANSI 和 Unicode 字元型別具有 CRT 支援。|  
  
 下列資料型別可在 **ATL\_CSTRING\_NO\_CRT** 中定義的專案:  
  
|CStringT 型別|宣告|  
|-----------------|--------|  
|**CAtlStringA**|沒有 CRT 支援\) 的 ANSI 字元型別字串。|  
|**CAtlStringW**|沒有 CRT 支援\) 的 Unicode 字元型別字串。|  
|**CAtlString**|ANSI 和 Unicode 字元型別沒有 CRT 支援。|  
  
 下列資料型別可在 **ATL\_CSTRING\_NO\_CRT** 沒有已定義的專案:  
  
|CStringT 型別|宣告|  
|-----------------|--------|  
|**CAtlStringA**|一個 ANSI 字元型別字串具有 CRT 支援。|  
|**CAtlStringW**|一個 Unicode 字元型別字串具有 CRT 支援。|  
|**CAtlString**|ANSI 和 Unicode 字元型別具有 CRT 支援。|  
  
 `CString` 物件也具有下列特性:  
  
-   由於串連作業，`CStringT` 物件可以擴充。  
  
-   `CStringT` 物件後面加上「實值語意」。視為一 `CStringT` 物件做為實際字串，而不是指向字串。  
  
-   您可以用 `PCXSTR` 函式引數自由替代 `CStringT` 物件。  
  
-   字串緩衝區的自訂記憶體管理。  如需詳細資訊，請參閱 [記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。  
  
## CStringT 預先定義型別  
 由於 `CStringT` 使用樣板引數定義 \( [wchar\_t](../../c-runtime-library/standard-types.md) 或 [char](../../c-runtime-library/standard-types.md)\) 支援的字元型別，方法參數型別可以隨時會變得很複雜。  為了簡化這個問題，會提供一組預先定義的型別定義和使用在 `CStringT` 類別中。  下表列出各種類型:  
  
|名稱|描述|  
|--------|--------|  
|`XCHAR`|單一字元 \( `wchar_t` 或 `char`\) 與字元型別和 `CStringT` 物件相同。|  
|**YCHAR**|單一字元 \( `wchar_t` 或 `char`\) 計數器字元型別做為 `CStringT` 物件。|  
|`PXSTR`|對應至字元字串的指標 \( `wchar_t` 或 `char`\) 與字元型別和 `CStringT` 物件相同。|  
|**PYSTR**|對應至字元字串的指標 \( `wchar_t` 或 `char`\) 計數器字元型別做為 `CStringT` 物件。|  
|`PCXSTR`|為 **const** 字元字串的指標 \( `wchar_t` 或 `char`\) 與字元型別和 `CStringT` 物件相同。|  
|**PCYSTR**|為 **const** 字元字串的指標 \( `wchar_t` 或 `char`\) 計數器字元型別做為 `CStringT` 物件。|  
  
> [!NOTE]
>  程式碼必須使用下列 `CStringT` 記錄的方法的程式碼取代 `CString` 先前使用未記載的方法 \(例如 **AssignCopy**\) \(例如 `GetBuffer` 或 `ReleaseBuffer`\)。  這些方法會從 `CSimpleStringT`繼承。  
  
## 繼承階層架構  
 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)  
  
 `CStringT`  
  
## 需求  
  
|Header|使用於|  
|------------|---------|  
|cstringt.h|MFC 字串物件。|  
|atlstr.h|非 MFC 字串物件。|  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)   
 [CSimpleStringT Class](../../atl-mfc-shared/reference/csimplestringt-class.md)
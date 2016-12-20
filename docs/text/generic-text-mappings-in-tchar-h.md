---
title: "Tchar.h 中的泛型文字對應 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ""tchar.h""
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字元集 [C++], 泛用文字對應"
  - "泛用文字對應 [C++]"
  - "對應泛型文字"
  - "對應 [C++], TCHAR.H"
  - "MBCS [C++], 泛用文字對應"
  - "TCHAR.H 資料類型, 對應"
  - "Unicode [C++], 泛用文字對應"
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
caps.latest.revision: 12
caps.handback.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Tchar.h 中的泛型文字對應
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為了簡化因應國際化用途的傳輸程式碼，[!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] 執行階段程式庫提供了許多資料型別、常式和其他物件的 [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] 特定泛用文字對應。  您可以使用這些定義於 Tchar.h 的對應來撰寫泛型程式碼，根據您使用 `#define` 陳述式所定義的資訊清單常數 \(Manifest Constant\)，可為單一位元組、多位元組或 [!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)] 字元集編譯。  泛用文字對應是與 [!INCLUDE[vcpransi](../preprocessor/includes/vcpransi_md.md)] 不相容的 [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] 擴充。  
  
 使用 Tchar.h，您可以從相同的來源建立單一位元組、多位元組字元集 \(MBCS\) 和 [!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)] 應用程式。  Tchar.h 定義字首是 `_tcs` 的巨集，有正確的前置處理器定義，會適當地對應到 `str`、`_mbs` 或 `wcs`。  若要建置 MBCS，請定義 `_MBCS` 符號。  若要建置 [!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)]，請定義 `_UNICODE` 符號。  若要建置單一位元組應用程式，兩者都不定義 \(預設\)。  根據預設，`_MBCS` 是為 MFC 應用程式定義。  
  
 `_TCHAR` 資料型別是在 Tchar.h 中以條件限定方式定義。  如果 `_UNICODE` 符號是為您的組建定義，則 `_TCHAR` 會定義成 `wchar_t`，否則對於單一位元組和 MBCS 的組建，它會定義為 `char` \(基本 Unicode 寬字元資料型別 `wchar_t` 是 8 位元帶正負號之 `char` 的 16 位元對應\)。若為國際化應用程式，請使用 `_tcs` 函式家族，以 `_TCHAR` 單位操作，而不是位元組。  例如，`_tcsncpy` 複製 `n` 個 `_TCHARs`，而不是 `n` 個位元組。  
  
 因為有些單一位元組字元集 \(SBCS\) 字串處理函式接受 \(帶正負號\) `char*` 參數，所以在定義 `_MBCS` 時，會產生型別不符合的編譯器警告。  有三個方法可以避免這個警告：  
  
1.  在 Tchar.h 中使用型別安全內嵌 \(Inline\) 函式 Thunk。  這是預設行為。  
  
2.  藉著在命令列上定義 `_MB_MAP_DIRECT` 來使用 Tchar.h 中的直接巨集。  如果您這樣做，您必須手動對應型別。  這是最快的方法，但並不是型別安全。  
  
3.  在 Tchar.h 中使用型別安全靜態連結程式庫函式 Thunk。  若要這麼做，請在命令列上定義 `_NO_INLINING` 常數。  這是最慢但型別最安全的方法。  
  
### 泛用文字對應的前置處理器指示詞 \(Preprocessor Directive\)  
  
|\# define|編譯版本|範例|  
|---------------|----------|--------|  
|`_UNICODE`|[!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)] \(寬字元\)|`_tcsrev` 對應到 `_wcsrev`|  
|`_MBCS`|多位元組字元|`_tcsrev` 對應到 `_mbsrev`|  
|無 \(預設未定義 `_UNICODE` 或 `_MBCS`\)|SBCS \([!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)]\)|`_tcsrev` 對應到 `strrev`|  
  
 例如，定義於 Tchar.h 的泛用文字函式 `_tcsrev`，對應到 `_mbsrev` \(如果您在程式裡定義 `_MBCS`\)，或對應到 `_wcsrev` \(如果您定義 `_UNICODE`\)。  否則，`_tcsrev` 會對應到 `strrev`。  為了程式設計方便，會在 Tchar.h 中提供其他資料型別對應，但 `_TCHAR` 是最有用的。  
  
### 泛用文字資料型別對應  
  
|泛型文字<br /><br /> 資料型別名稱|&Unicode<br /><br /> \_MBCS 未定義|\_MBCS<br /><br /> 已定義|\_UNICODE<br /><br /> 已定義|  
|---------------------|-----------------------------|--------------------|-----------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`unsigned int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` 或 `_TEXT`|沒有作用 \(被前置處理器移除\)|沒有作用 \(被前置處理器移除\)|`L` \(將下列字元或字串轉換成其 [!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)] 的對應\)|  
  
 如需常式、變數和其他物件之泛用文字對應的完整清單，請參閱《執行階段程式庫參考》中的[泛型文字對應](../c-runtime-library/generic-text-mappings.md)。  
  
> [!NOTE]
>  請不要將 `str` 函式家族與 Unicode 字串一起使用，這可能會包含內嵌 null 位元組。  同樣地，不要將 `wcs` 函式家族與 MBCS \(或 SBCS\) 字串一起使用。  
  
 下列程式碼片段示範 `_TCHAR` 和 `_tcsrev` 對應到 MBCS、[!INCLUDE[TLA#tla_unicode](../cpp/includes/tlasharptla_unicode_md.md)] 和 SBCS 模型的用法。  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 如果 `_MBCS` 已經定義了，前置處理器將這個片段對應到下列程式碼：  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 如果 `_UNICODE` 已經定義了，前置處理器將這個片段對應到下列程式碼：  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 如果 `_MBCS` 或 `_UNICODE` 都沒有被定義，前置處理器會將此片段對應到單一位元組 [!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)] 編碼，如下所示：  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 因此您可以撰寫、維護和編譯單一原始程式碼檔，與特定於這三種字元集其中一種的常式一起執行。  
  
## 請參閱  
 [文字和字串](../text/text-and-strings-in-visual-cpp.md)   
 [使用含有 \_MBCS 程式碼的 TCHAR.H 資料類型](../text/using-tchar-h-data-types-with-mbcs-code.md)
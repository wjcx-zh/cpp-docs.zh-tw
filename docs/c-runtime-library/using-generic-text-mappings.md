---
title: "使用泛型文字對應 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_UNICODE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_MBCS 資料類型"
  - "_T 類型"
  - "_TCHAR 類型"
  - "_TEXT 類型"
  - "_TINT 類型"
  - "_TSCHAR 類型"
  - "_TUCHAR 類型"
  - "_TXCHAR 類型"
  - "_UNICODE 常數"
  - "泛型文字資料類型"
  - "泛用文字對應"
  - "對應, 泛型文字"
  - "MBCS 資料類型"
  - "T 類型"
  - "TCHAR 類型"
  - "TCHAR.H 資料類型, 在其中定義的對應"
  - "TEXT 類型"
  - "TINT 類型"
  - "TSCHAR 類型"
  - "TUCHAR 類型"
  - "TXCHAR 類型"
  - "UNICODE 常數"
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 使用泛型文字對應
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 為了簡化因應各種國際化市場的開發程式碼， Microsoft 執行階段程式庫提供了許多資料型別、常式和其他物件的 Microsoft 特定泛用文字對應。  這些對應在 TCHAR.H. 中定義。  您可以使用這些名稱對應撰寫可為任何這三種編譯字元集的泛型程式碼：ASCII \(SBCS\)、MBCS 或 Unicode，根據您使用 `#define` 陳述式定義的資訊清單常數 \(Manifest Constant\) 的參數。  泛用文字對應是與 ANSI 不相容的 Microsoft 擴充。  
  
### 泛用文字對應的前置處理器指示詞 \(Preprocessor Directive\)  
  
|\#define|編譯版本|範例|  
|--------------|----------|--------|  
|`_UNICODE`|Unicode \(寬字元\)|`_tcsrev` 對應到 `_wcsrev`|  
|`_MBCS`|多位元組字元|`_tcsrev` 對應到 `_mbsrev`|  
|無 \(預設：非 `_UNICODE` 也不是 `_MBCS` 定義\)|SBCS \(ASCII\)|`_tcsrev`  對應至 `strrev`。|  
  
 例如，定義於 Tchar.h 的泛用文字函式 `_tcsrev`，對應到 `mbsrev` \(如果`MBCS` 已在您在程式裡定義 \)，或對應到 `_wcsrev`  \(如果 `_UNICODE`  已定義\)。  否則 `_tcsrev`  會對應到 `strrev`。  
  
 泛用文字資料型別 `_TCHAR`也會定義在 TCHAR.H，如果 `_MBCS` 定義，會對應至型別 `char`，如果 `_UNICODE` 定義，會對應至型別 `wchar_t`，如果沒有常數被定義，則對應至 `char` 。  為了程式設計方便，會在 TCHAR.H 中提供其他資料型別對應，但 `_TCHAR` 是最有用的的型別。  
  
### 泛用文字資料型別對應  
  
|泛用文字資料型別名稱|SBCS \(\_UNICODE, \_MBCS 未定義\)|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------------|----------------|-------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` 或 `_TEXT`|沒有作用 \(被前置處理器移除\)|沒有作用 \(被前置處理器移除\)|`L` \(將下列字元或字串轉換成其 Unicode 的對應\)|  
  
 如需常式泛用文字對應的完整清單、變數和其他物件的詳細資訊，請參閱 [泛用文字對應](../c-runtime-library/generic-text-mappings.md)。  
  
 下列程式碼片段示範 `_TCHAR` 和 `_tcsrev` 對應到 MBCS、 和 SBCS 模型的用法。  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 如果 `MBCS` 已經定義了，前置處理器會將上述片段對應到下列程式碼：  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 如果 `_UNICODE` 已經定義了，前置處理器會將相同的片段對應到下列程式碼：  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 如果 `_MBCS` 或 `_UNICODE` 都尚未被定義，則前置處理器會將此片段對應到單一位元組的 ASCII 編碼，如下所示：  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 因此您可以撰寫、維護和編譯單一原始程式碼檔，與特定於這三種字元集其中一種的常式一起執行。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [泛型文字對應](../c-runtime-library/generic-text-mappings.md)   
 [資料類型對應](../c-runtime-library/data-type-mappings.md)   
 [常數和全域變數對應](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [常式對應](../c-runtime-library/routine-mappings.md)   
 [泛型文字程式範例](../c-runtime-library/a-sample-generic-text-program.md)
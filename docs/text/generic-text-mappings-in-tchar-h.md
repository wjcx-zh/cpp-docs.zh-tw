---
title: Tchar.h 中的泛用文字對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- tchar.h
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7ed29b03a37c9b911a954192152115b1458fd94
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33867099"
---
# <a name="generic-text-mappings-in-tcharh"></a>Tchar.h 中的泛型文字對應
若要簡化國際用於程式碼的傳輸[!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)]執行階段程式庫提供[!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)]-許多資料類型、 常式與其他物件的特定泛用文字對應。 您可以使用這些對應，Tchar.h，撰寫可針對單一位元組，多位元組，來編譯的泛型程式碼中所定義或[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]字元集，根據您定義使用資訊清單常數`#define`陳述式。 泛用文字對應[!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)]所沒有的擴充功能[!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)]相容。  
  
 您可以藉由使用 Tchar.h，建置單一位元組，多位元組字元集 (MBCS)，和[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]來源相同的應用程式。 Tchar.h 中定義的巨集 (其中有前置詞`_tcs`) 會使用正確的前置處理器定義對應到`str`， `_mbs`，或`wcs`函式，視需要。 若要建立 MBCS，請定義符號`_MBCS`。 若要建置[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]，定義符號`_UNICODE`。 若要建置單一位元組應用程式，定義兩 （預設值）。 根據預設， `_MBCS` MFC 應用程式的定義。  
  
 `_TCHAR` Tchar.h 中有條件地定義資料類型。 如果符號`_UNICODE`為您的組建定義`_TCHAR`定義為`wchar_t`; 否則它定義為單一位元組和 MBCS 組建， `char`。 (`wchar_t`，基本的 Unicode 寬字元資料類型，是以 8 位元帶正負號的 16 位元對應項目`char`。)國際應用程式，使用`_tcs`系列的函式，在操作`_TCHAR`單位、 不是位元組。 例如，`_tcsncpy`複本`n` `_TCHARs`，而非`n`位元組。  
  
 由於某些單一位元組字元設定 (SBCS) 的字串處理函式 （帶正負號） 的 take`char*`參數、 型別不相符編譯器警告結果時`_MBCS`定義。 有三種方式可避免此警告：  
  
1.  使用 Tchar.h 中的型別安全內嵌函式的 thunk。 這是預設行為。  
  
2.  使用 Tchar.h 中的直接巨集，藉由定義`_MB_MAP_DIRECT`命令列上。 如果這麼做，就必須手動對應類型。 這是最快的方法，但不是類型安全。  
  
3.  使用 Tchar.h 中的型別安全靜態連結程式庫函式的 thunk。 若要這樣做，請在命令列上定義常數 `_NO_INLINING`。 這是最慢、但類型最安全的方法。  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>泛型文字對應的前置處理器指示詞  
  
|# 定義|編譯的版本|範例|  
|---------------|----------------------|-------------|  
|`_UNICODE`|[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] （寬字元）|`_tcsrev` 對應到 `_wcsrev`|  
|`_MBCS`|多位元組字元|`_tcsrev` 對應到 `_mbsrev`|  
|無 (預設值沒有`_UNICODE`也`_MBCS`定義)|SBCS ([!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)])|`_tcsrev` 對應到 `strrev`|  
  
 例如，泛用文字函數`_tcsrev`，定義於 Tchar.h 中對應至`_mbsrev`如果您定義`_MBCS`在程式中，或`_wcsrev`如果您定義`_UNICODE`。 若兩者皆否，則 `_tcsrev` 會對應至 `strrev`。 為了方便程式設計，Tchar.h 中提供其他資料類型對應但`_TCHAR`最為實用。  
  
### <a name="generic-text-data-type-mappings"></a>泛型文字資料類型對應  
  
|一般文字<br /><br /> 資料型別名稱|_UNICODE &<br /><br /> _MBCS 未定義|_MBCS<br /><br /> 已定義|_UNICODE<br /><br /> 已定義|  
|--------------------------------------|----------------------------------------|------------------------|---------------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`unsigned int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` 或 `_TEXT`|無效果 (已由前置處理器移除)|無效果 (已由前置處理器移除)|`L` (將下列字元或字串轉換其[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]對應項目)|  
  
 如需泛型文字對應的常式、 變數和其他物件的清單，請參閱[泛用文字對應](../c-runtime-library/generic-text-mappings.md)在執行階段程式庫參考。  
  
> [!NOTE]
>  請勿使用`str`系列的函式與 Unicode 字串，它們可能包含內嵌的 null 位元組。 同樣地，請勿使用`wcs`系列的函式使用 MBCS （或 SBCS） 的字串。  
  
 下列程式碼片段說明使用`_TCHAR`和`_tcsrev`對應至 MBCS [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]，和 SBCS 模型。  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 如果`_MBCS`已定義，前置處理器將這個片段對應此程式碼：  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 如果`_UNICODE`已定義，前置處理器將這個片段對應此程式碼：  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 如果沒有`_MBCS`也`_UNICODE`已定義，前置處理器將片段對應至單一位元組[!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)]，程式碼，如下所示：  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 因此，您可以撰寫、 維護及編譯單一原始程式碼檔案，以執行與所特有的三種字元集的常式。  
  
## <a name="see-also"></a>另請參閱  
 [文字和字串](../text/text-and-strings-in-visual-cpp.md)   
 [使用含有 _MBCS 程式碼的 TCHAR.H 資料類型](../text/using-tchar-h-data-types-with-mbcs-code.md)
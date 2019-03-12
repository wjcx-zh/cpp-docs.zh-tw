---
title: 資料類型對應
ms.date: 11/04/2016
f1_keywords:
- _TXCHAR
- _TUCHAR
- _TINT
- _TSCHAR
- _TCHAR
- TCHAR::H
- TCHAR
- _T
- _TEXT
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- TXCHAR type
- _TSCHAR type
- T type
- _TUCHAR type
- _TEXT type
- _T type
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
ms.openlocfilehash: 60dc4329ae4c908b9bd168584c71c42c12634bb2
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749096"
---
# <a name="data-type-mappings"></a>資料類型對應

這些資料類型對應都是在 TCHAR.H 中定義，並視程式中是否定義常數 `_UNICODE` 或 `_MBCS` 而定。

如需相關資訊，請參閱[使用含有 _MBCS 程式碼的 TCHAR.H 資料類型](../text/using-tchar-h-data-types-with-mbcs-code.md)。

### <a name="generic-text-data-type-mappings"></a>泛型文字資料類型對應

|泛型文字<br /><br /> 資料類型名稱|SBCS (_UNICODE、<br /><br /> _MBCS 未<br /><br /> 定義)|_MBCS<br /><br /> 已定義的|_UNICODE<br /><br /> 已定義的|
|--------------------------------------|----------------------------------------------------|------------------------|---------------------------|
|`_TCHAR`|`char`|`char`|`wchar_t`|
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|
|`_TINT`|`int`|`int`|`wint_t`|
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|
|`_T` 或 `_TEXT`|無效果 (已由前置處理器移除)|無效果 (已由前置處理器移除)|`L` (將下列字元或字串轉換成其 Unicode 對應項目)|

## <a name="see-also"></a>另請參閱

[泛型文字對應](../c-runtime-library/generic-text-mappings.md)<br/>
[常數和全域變數對應](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[常式對應](../c-runtime-library/routine-mappings.md)<br/>
[泛型文字程式範例](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[使用泛型文字對應](../c-runtime-library/using-generic-text-mappings.md)

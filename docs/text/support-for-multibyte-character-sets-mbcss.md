---
title: 多位元組字元集 (MBCS) 的支援
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
ms.openlocfilehash: 0b43168ec4331e99dea7e939b097674cc880804e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375759"
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>多位元組字元集 (MBCS) 的支援

多位元組字元集 (Multibyte Character Set，MBCS) 是支援字元集的舊方法，例如不能以單一位元組表示的日文和中文。 如果您進行新開發，除了終端使用者看不見的系統字串之外，您應該對所有文字字串使用 Unicode。 MBCS 是舊版技術，不建議用於新開發。

最常見的 MBCS 實作是雙位元組字元集 (DBCS)。 一般而言，Visual C++ 尤其是 MFC，已完全支援 DBCS。

如需範例，請參閱 MFC 原始程式碼檔案。

對於其語言使用大型字元集的市場中使用的平台，Unicode 的最佳替代方案是 MBCS。 MFC 使用可國際語系化的資料類型和 C 執行階段函式來支援 MBCS。 您應該在您的相同程式碼中執行相同動作。

在 MBCS 下，字元會以 1 或 2 個位元組編碼。 在 2 個位元組的字元中，第一個或前導位元組表示它和下一個位元組會解譯成一個字元。 第一個位元組來自一個範圍的字碼，保留供做為前導位元組使用。 哪個範圍的位元組可以做為前導位元組，取決於使用中的字碼頁。 例如，日文的字碼頁 932 使用範圍 0x81 到 0x9F 來當做前導位元組，但韓文字碼頁 949 使用不同的範圍。

請在您的 MBCS 程式設計中考慮以下所有項目。

環境中 MBCS 字元中的 MBCS 字元可以顯示在字串中,如檔案和目錄名稱。

### <a name="editing-operations"></a>編輯作業

MBCS 應用程式中的編輯作業，應該可對字元而不是位元組運作。 該字元不應拆分字元,**右箭頭**鍵應向右移動一個字元,等等。 **刪除**應刪除字元;**撤銷**重新插入它。

### <a name="string-handling"></a>字串處理

在使用 MBCS 的應用程式中，字串處理會造成特殊的問題。 在單一字串中會混用這兩種寬度的字元；因此，您必須記得檢查前導位元組。

### <a name="run-time-library-support"></a>執行階段程式庫支援

C 執行階段程式庫和 MFC 支援單一位元組、MBCS 和 Unicode 程式設計。 單位元組位元串使用運行時函`str`數 系列進行處理,MBCS 字串`_mbs`使用相應的 函數進行處理,Unicode 字`wcs`串使用相應的函數進行處理。 MFC 類別成員函式實作會使用可攜式執行階段，在正確的情況下，其會將函式對應至函式的正常 `str` 系列、MBCS 函式或 Unicode 函式，如「MBCS/Unicode 可攜性」中所述。

### <a name="mbcsunicode-portability"></a>MBCS/Unicode 可攜性

使用 tchar.h 標頭檔,可以從同一源生成單位元組、MBCS 和 Unicode 應用程式。 Tchar.h 定義以 *_tcs* () 的`str`預`_mbs`置的`wcs`巨集, 這些巨集將映射到或函數(視適用而言)。 要產生 MBCS,請`_MBCS`定義符號 。 要產生 Unicode,請`_UNICODE`定義符號 。 預設情況下,`_UNICODE`為 MFC 應用程式定義。 有關詳細資訊,請參閱[tchar.h 中的通用文字映射](../text/generic-text-mappings-in-tchar-h.md)。

> [!NOTE]
> 如果同時定義`_UNICODE``_MBCS`和 ,則行為未定義。

Mbctype.h 和 Mbstring.h 標頭檔會定義 MBCS 特有的函式和巨集，在某些情況下您可能需要。 例如，`_ismbblead` 會告訴您在字串中的特定位元組是否為前導位元組。

為獲得國際可移植性,請使用[Unicode](../text/support-for-unicode.md)或多位元組位元集 (MBCS) 對程式進行編碼。

## <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [在我的程式中啟用 MBCS](../text/international-enabling.md)

- [在我的程式開啟 Unicode 和 MBCS](../text/internationalization-strategies.md)

- [使用 MBCS 來建立國際化程式](../text/mbcs-programming-tips.md)

- [請參閱 MBCS 程式設計的摘要](../text/mbcs-programming-tips.md)

- [了解位元組寬度可移植性的一般文字對應](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>另請參閱

[文字和字串](../text/text-and-strings-in-visual-cpp.md)<br/>
[Visual C++ 中的 MBCS 支援](../text/mbcs-support-in-visual-cpp.md)

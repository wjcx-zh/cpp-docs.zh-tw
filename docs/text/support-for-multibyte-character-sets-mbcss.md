---
title: 多位元組字元集 (MBCS) 的支援
ms.date: 11/04/2016
f1_keywords:
- _mbcs
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
ms.openlocfilehash: a642fd136c104b621b83ab6db5a3704ea94fdae1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741981"
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>多位元組字元集 (MBCS) 的支援

多位元組字元集 (Multibyte Character Set，MBCS) 是支援字元集的舊方法，例如不能以單一位元組表示的日文和中文。 如果您進行新開發，除了終端使用者看不見的系統字串之外，您應該對所有文字字串使用 Unicode。 MBCS 是舊版技術，不建議用於新開發。

最常見的 MBCS 實作是雙位元組字元集 (DBCS)。 一般而言，Visual C++ 尤其是 MFC，已完全支援 DBCS。

如需範例，請參閱 MFC 原始程式碼檔案。

對於其語言使用大型字元集的市場中使用的平台，Unicode 的最佳替代方案是 MBCS。 MFC 使用可國際語系化的資料類型和 C 執行階段函式來支援 MBCS。 您應該在您的相同程式碼中執行相同動作。

在 MBCS 下，字元會以 1 或 2 個位元組編碼。 在 2 個位元組的字元中，第一個或前導位元組表示它和下一個位元組會解譯成一個字元。 第一個位元組來自一個範圍的字碼，保留供做為前導位元組使用。 哪個範圍的位元組可以做為前導位元組，取決於使用中的字碼頁。 例如，日文的字碼頁 932 使用範圍 0x81 到 0x9F 來當做前導位元組，但韓文字碼頁 949 使用不同的範圍。

請在您的 MBCS 程式設計中考慮以下所有項目。

環境 MBCS 字元的 MBCS 字元可出現在例如檔案和目錄名稱的字串。

### <a name="editing-operations"></a>編輯作業

MBCS 應用程式中的編輯作業，應該可對字元而不是位元組運作。 插入號不應分割字元**向右箭號**金鑰應該移動一個字元，以滑鼠右鍵，然後依此類推。 **刪除**應該刪除字元;**復原**應該將它重新插入。

### <a name="string-handling"></a>字串處理

在使用 MBCS 的應用程式中，字串處理會造成特殊的問題。 在單一字串中會混用這兩種寬度的字元；因此，您必須記得檢查前導位元組。

### <a name="run-time-library-support"></a>執行階段程式庫支援

C 執行階段程式庫和 MFC 支援單一位元組、MBCS 和 Unicode 程式設計。 會處理單一位元組字串，並以`str`系列的執行階段函式，MBCS 字串處理和對應`_mbs`函式，而 Unicode 字串會使用對應的處理`wcs`函式。 MFC 類別成員函式實作會使用可攜式執行階段，在正確的情況下，其會將函式對應至函式的正常 `str` 系列、MBCS 函式或 Unicode 函式，如「MBCS/Unicode 可攜性」中所述。

### <a name="mbcsunicode-portability"></a>MBCS/Unicode 可攜性

使用 tchar.h 標頭檔，您可以建置單一位元組、 MBCS 和 Unicode 來源相同的應用程式。 Tchar.h 中定義巨集前面加上 *_tcs* ，其對應至`str`， `_mbs`，或`wcs`函式，視需要。 若要建立 MBCS，請定義符號`_MBCS`。 若要建置 Unicode，請定義符號`_UNICODE`。 根據預設，`_UNICODE`定義針對 MFC 應用程式。 如需詳細資訊，請參閱 < [tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)。

> [!NOTE]
>  如果您同時定義行為是未定義`_UNICODE`和`_MBCS`。

Mbctype.h 和 Mbstring.h 標頭檔會定義 MBCS 特有的函式和巨集，在某些情況下您可能需要。 例如，`_ismbblead` 會告訴您在字串中的特定位元組是否為前導位元組。

國際可攜性，程式碼將程式與[Unicode](../text/support-for-unicode.md)或多位元組字元集 (Mbcs)。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [在程式中啟用 MBCS](../text/international-enabling.md)

- [在程式中啟用 Unicode 和 MBCS](../text/internationalization-strategies.md)

- [使用 MBCS 來建立國際化的程式](../text/mbcs-programming-tips.md)

- [請參閱 MBCS 程式設計的摘要](../text/mbcs-programming-tips.md)

- [了解位元組寬度可移植性的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>另請參閱

[文字和字串](../text/text-and-strings-in-visual-cpp.md)<br/>
[Visual C++ 中的 MBCS 支援](../text/mbcs-support-in-visual-cpp.md)

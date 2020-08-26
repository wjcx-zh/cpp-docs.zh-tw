---
title: C 關鍵字
ms.date: 10/09/2018
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: 1b49da349a6552022dfd9e8e66e85634f4694645
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838772"
---
# <a name="c-keywords"></a>C 關鍵字

「關鍵字」是指對 C 編譯器有特殊意義的字詞。 在轉譯階段 7 和 8 中，識別項不能包含與 C 關鍵字相同的拼字和大小寫。  (在*預處理器參考*中查看[轉譯階段](../preprocessor/phases-of-translation.md)的描述;如需識別碼的詳細資訊，請參閱[識別碼](../c-language/c-identifiers.md)。 ) C 語言會使用下列關鍵字：

:::row:::
    :::column:::
        **`auto`**\
        **`double`**\
        **`int`**\
        **`struct`**\
        **`break`**\
        **`else`**\
        **`long`**\
        **`switch`**
    :::column-end:::
    :::column:::
        **`case`**\
        **`enum`**\
        **`register`**\
        **`typedef`**\
        **`char`**\
        **`extern`**\
        **`return`**\
        **`union`**
    :::column-end:::
    :::column:::
        **`const`**\
        **`float`**\
        **`short`**\
        **`unsigned`**\
        **`continue`**\
        **`for`**\
        **`signed`**\
        **`void`**
    :::column-end:::
    :::column:::
        **`default`**\
        **`goto`**\
        **`sizeof`**\
        **`volatile`**\
        **`do`**\
        **`if`**\
        **`static`**\
        **`while`**
    :::column-end:::
:::row-end:::

您無法重新定義關鍵字。 不過，您可以在編譯前，使用 C [前置處理器指示詞](../preprocessor/preprocessor-directives.md)指定要取代為關鍵字的文字。

**Microsoft 特定的**

ANSI C 標準允許保留具有兩個前置底線的識別項，供編譯器實作使用。 因此，Microsoft 的慣例就是在 Microsoft 專有關鍵字名稱前面加上雙底線。 這些字詞不可做為識別項名稱使用。 如需命名識別碼之 ANSI 規則的描述，包括使用雙底線，請參閱[識別碼](../c-language/c-identifiers.md)。

Microsoft C 編譯器可辨識下列關鍵字和特殊識別項：

:::row:::
    :::column:::
        **`__asm`**<sup>3</sup>\
        **`dllimport`**<sup>二級</sup>\
        **`__int8`**<sup>3</sup>\
        **`naked`**<sup>二級</sup>\
        **`__based`**<sup>1、3</sup>
    :::column-end:::
    :::column:::
        **`__except`**<sup>3</sup>\
        **`__int16`**<sup>3</sup>\
        **`__stdcall`**<sup>3</sup>\
        **`__cdecl`**<sup>3</sup>\
        **`__fastcall`**
    :::column-end:::
    :::column:::
        **`__int32`**<sup>3</sup>\
        **`thread`**<sup>二級</sup>\
        **`__declspec`**<sup>3</sup>\
        **`__finally`**<sup>3</sup>\
        **`__int64`**<sup>3</sup>
    :::column-end:::
    :::column:::
        **`__try`**<sup>3</sup>\
        **`dllexport`**<sup>二級</sup>\
        **`__inline`**<sup>3</sup>\
        **`__leave`**<sup>3</sup>
    :::column-end:::
:::row-end:::

<sup>1</sup> **`__based`** 關鍵字的用途有限，可用於32位和64位目標編譯。

<sup>2</sup> 這些是搭配使用時的特殊識別碼， **`__declspec`** 在其他內容中使用則不受限制。

<sup>3</sup> 為了與舊版相容，這些關鍵字在啟用 Microsoft 擴充功能時可以使用兩個前置底線和單一前置底線。

Microsoft 擴充功能預設為啟用。 為了確保您的程式可完整移植，您可以在編譯期間指定 [/Za \(停用語言擴充功能)](../build/reference/za-ze-disable-language-extensions.md) 來停用 Microsoft 擴充功能。 當您這樣做時，某些 Microsoft 專有關鍵字就會停用。

在 Microsoft 擴充功能啟用時，您可以在程式中使用上面所列的關鍵字。 為了提供 ANSI 相容性，大部分關鍵字前面都會加上雙底線。 這四個例外狀況（、 **`dllexport`** **`dllimport`** 、 **`naked`** 和）只能搭配使用， **`thread`** **`__declspec`** 因此不需要前置雙底線。 為了提供回溯相容性，仍支援其餘關鍵字的單一底線版本。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[C 的元素](../c-language/elements-of-c.md)

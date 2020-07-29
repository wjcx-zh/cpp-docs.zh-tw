---
title: C 關鍵字
ms.date: 10/09/2018
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: 081235f987d3f6f8dbfd3abb4af9d70688b7fd98
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200708"
---
# <a name="c-keywords"></a>C 關鍵字

「關鍵字」是指對 C 編譯器有特殊意義的字詞。 在轉譯階段 7 和 8 中，識別項不能包含與 C 關鍵字相同的拼字和大小寫。 （請參閱*預處理器參考*中的[轉譯階段](../preprocessor/phases-of-translation.md)描述。如需識別碼的詳細資訊，請參閱[識別碼](../c-language/c-identifiers.md)）。C 語言會使用下列關鍵字：

:::row:::
    :::column:::
        **`auto`**<br/>
        **`double`**<br/>
        **`int`**<br/>
        **`struct`**<br/>
        **`break`**<br/>
        **`else`**<br/>
        **`long`**<br/>
        **`switch`**<br/>
    :::column-end:::
    :::column:::
        **`case`**<br/>
        **`enum`**<br/>
        **`register`**<br/>
        **`typedef`**<br/>
        **`char`**<br/>
        **`extern`**<br/>
        **`return`**<br/>
        **`union`**<br/>
    :::column-end:::
    :::column:::
        **`const`**<br/>
        **`float`**<br/>
        **`short`**<br/>
        **`unsigned`**<br/>
        **`continue`**<br/>
        **`for`**<br/>
        **`signed`**<br/>
        **`void`**<br/>
    :::column-end:::
    :::column:::
        **`default`**<br/>
        **`goto`**<br/>
        **`sizeof`**<br/>
        **`volatile`**<br/>
        **`do`**<br/>
        **`if`**<br/>
        **`static`**<br/>
        **`while`**<br/>
    :::column-end:::
:::row-end:::

您不能重新定義關鍵字。 不過，您可以在編譯前，使用 C [前置處理器指示詞](../preprocessor/preprocessor-directives.md)指定要取代為關鍵字的文字。

**Microsoft 特定的**

ANSI C 標準允許保留具有兩個前置底線的識別項，供編譯器實作使用。 因此，Microsoft 的慣例就是在 Microsoft 專有關鍵字名稱前面加上雙底線。 這些字詞不可做為識別項名稱使用。 如需命名識別碼之 ANSI 規則的描述，包括使用雙底線，請參閱[識別碼](../c-language/c-identifiers.md)。

Microsoft C 編譯器可辨識下列關鍵字和特殊識別項：

:::row:::
    :::column:::
        **`__asm`**<sup>第</sup><br/>
        **`dllimport`**<sup>2</sup><br/>
        **`__int8`**<sup>第</sup><br/>
        **`naked`**<sup>2</sup><br/>
        **`__based`**<sup>1、3</sup><br/>
    :::column-end:::
    :::column:::
        **`__except`**<sup>第</sup><br/>
        **`__int16`**<sup>第</sup><br/>
        **`__stdcall`**<sup>第</sup><br/>
        **`__cdecl`**<sup>第</sup><br/>
        **`__fastcall`**<br/>
    :::column-end:::
    :::column:::
        **`__int32`**<sup>第</sup><br/>
        **`thread`**<sup>2</sup><br/>
        **`__declspec`**<sup>第</sup><br/>
        **`__finally`**<sup>第</sup><br/>
        **`__int64`**<sup>第</sup><br/>
    :::column-end:::
    :::column:::
        **`__try`**<sup>第</sup><br/>
        **`dllexport`**<sup>2</sup><br/>
        **`__inline`**<sup>第</sup><br/>
        **`__leave`**<sup>第</sup><br/>
    :::column-end:::
:::row-end:::

<sup>1</sup> **`__based`** 關鍵字對32位和64位目標編譯的使用有限。

<sup>2</sup>這些是搭配使用時的特殊識別碼， **`__declspec`** 在其他內容中使用則不受限制。

<sup>3</sup> 為了與舊版相容，這些關鍵字在啟用 Microsoft 擴充功能時可以使用兩個前置底線和單一前置底線。

Microsoft 擴充功能預設為啟用。 為了確保您的程式可完整移植，您可以在編譯期間指定 [/Za \(停用語言擴充功能)](../build/reference/za-ze-disable-language-extensions.md) 來停用 Microsoft 擴充功能。 當您這樣做時，某些 Microsoft 專有關鍵字就會停用。

在 Microsoft 擴充功能啟用時，您可以在程式中使用上面所列的關鍵字。 為了提供 ANSI 相容性，大部分關鍵字前面都會加上雙底線。 這四個例外狀況（ **`dllexport`** 、 **`dllimport`** 、 **`naked`** 和）只能搭配使用， **`thread`** **`__declspec`** 因此不需要前置雙底線。 為了提供回溯相容性，仍支援其餘關鍵字的單一底線版本。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[C 的元素](../c-language/elements-of-c.md)

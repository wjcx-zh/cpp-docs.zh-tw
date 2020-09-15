---
title: C 關鍵字
description: 標準 C 和 Microsoft C 編譯器延伸模組中的關鍵字。
ms.date: 09/12/2020
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: f459b81c2b3f314218108f3f367eec0c1bf17f26
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075734"
---
# <a name="c-keywords"></a>C 關鍵字

*關鍵字* 是對 C 編譯器具有特殊意義的字詞。 在轉譯階段7和8中，識別碼不能具有與 C 關鍵字相同的拼寫和大小寫。 如需詳細資訊，請參閱*預處理器參考*中的[轉譯階段](../preprocessor/phases-of-translation.md)。 如需識別碼的詳細資訊，請參閱 [識別碼](../c-language/c-identifiers.md)。

## <a name="standard-c-keywords"></a>標準 C 關鍵字

C 語言使用下列關鍵字：

:::row:::
    :::column:::
        **`auto`**\
        **`break`**\
        **`case`**\
        **`char`**\
        **`const`**\
        **`continue`**\
        **`default`**\
        **`do`**\
        **`double`**\
        **`else`**\
        **`enum`**
    :::column-end:::
    :::column:::
        **`extern`**\
        **`float`**\
        **`for`**\
        **`goto`**\
        **`if`**\
        **`inline`**<sup>1，a</sup>\
        **`int`**\
        **`long`**\
        **`register`**\
        **`restrict`**<sup>1，a</sup>\
        **`return`**
    :::column-end:::
    :::column:::
        **`short`**\
        **`signed`**\
        **`sizeof`**\
        **`static`**\
        **`struct`**\
        **`switch`**\
        **`typedef`**\
        **`union`**\
        **`unsigned`**\
        **`void`**\
        **`volatile`**
    :::column-end:::
    :::column:::
        **`while`**\
        **`_Alignas`**<sup>2，a</sup>\
        **`_Alignof`**<sup>2，a</sup>\
        **`_Atomic`**<sup>2，b</sup>\
        **`_Bool`**<sup>1，a</sup>\
        **`_Complex`**<sup>1，b</sup>\
        **`_Generic`**<sup>2，a</sup>\
        **`_Imaginary`**<sup>1，b</sup>\
        **`_Noreturn`**<sup>2，a</sup>\
        **`_Static_assert`**<sup>2，a</sup>\
        **`_Thread_local`**<sup>2，b</sup>
    :::column-end:::
:::row-end:::

在 ISO C99 中引進了<sup>1</sup>個關鍵字。

在 ISO C11 中引進<sup>2</sup>個關鍵字。

<sup>從 Visual Studio</sup>  2019 16.8 版開始，當 **`/std:c11`** 指定或編譯器選項時，會在編譯為 C 的程式碼中支援這些關鍵字 **`/std:c17`** 。

<sup>b</sup>  從 Visual Studio 2019 16.8 版開始，在 **`/std:c11`** 指定或編譯器選項時，會辨識這些關鍵字，但編譯器在編譯為 C 的程式碼中並不支援 **`/std:c17`** 。

您無法重新定義關鍵字。 不過，您可以使用 C [預處理器](../preprocessor/preprocessor-directives.md)指示詞，在編譯之前指定文字來取代關鍵字。

## <a name="microsoft-specific-c-keywords"></a>Microsoft 特定的 C 關鍵字

ANSI 和 ISO C 標準允許將具有兩個前置底線的識別碼保留給編譯器執行。 Microsoft 慣例是在 Microsoft 特定的關鍵字名稱之前加上雙底線。 這些字組無法用作識別碼名稱。 如需命名識別碼之規則的描述，包括使用雙底線，請參閱 [識別碼](../c-language/c-identifiers.md)。

Microsoft C 編譯器可辨識下列關鍵字和特殊識別項：

:::row:::
    :::column:::
        **`__asm`**<sup>.5</sup>\
        **`dllimport`**<sup>億</sup>\
        **`__int8`**<sup>.5</sup>\
        **`naked`**<sup>億</sup>\
        **`__based`**<sup>3，5</sup>
    :::column-end:::
    :::column:::
        **`__except`**<sup>.5</sup>\
        **`__int16`**<sup>.5</sup>\
        **`__stdcall`**<sup>.5</sup>\
        **`__cdecl`**<sup>.5</sup>\
        **`__fastcall`**
    :::column-end:::
    :::column:::
        **`__int32`**<sup>.5</sup>\
        **`thread`**<sup>億</sup>\
        **`__declspec`**<sup>.5</sup>\
        **`__finally`**<sup>.5</sup>\
        **`__int64`**<sup>.5</sup>
    :::column-end:::
    :::column:::
        **`__try`**<sup>.5</sup>\
        **`dllexport`**<sup>億</sup>\
        **`__inline`**<sup>.5</sup>\
        **`__leave`**<sup>.5</sup>
    :::column-end:::
:::row-end:::

<sup>3</sup> **`__based`** 關鍵字的用途有限，可用於32位和64位目標編譯。

<sup>4</sup> 這些是搭配使用時的特殊識別碼， **`__declspec`** 在其他內容中使用則不受限制。

<sup>5</sup> 為了與舊版相容，在啟用 Microsoft 擴充功能時，可使用兩個前置底線和單一前置底線來使用這些關鍵字。

Microsoft 擴充功能預設為啟用。 若要協助建立可移植的程式碼，您可以在編譯期間指定 [/Za \( 停用語言延伸) ](../build/reference/za-ze-disable-language-extensions.md) 選項，以停用 Microsoft 擴充功能。 當您使用此選項時，會停用部分 Microsoft 特定的關鍵字。

在 Microsoft 擴充功能啟用時，您可以在程式中使用上面所列的關鍵字。 針對標準合規性，這些關鍵字大多會以雙底線開頭。 這四個例外狀況（、 **`dllexport`** **`dllimport`** 、 **`naked`** 和）只能搭配使用， **`thread`** **`__declspec`** 而且不需要前置雙底線。 為了提供回溯相容性，仍支援其餘關鍵字的單一底線版本。

## <a name="see-also"></a>另請參閱

[C 的元素](../c-language/elements-of-c.md)

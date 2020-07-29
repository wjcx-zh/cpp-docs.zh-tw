---
title: 關鍵字 (C++)
description: 列出 c + + 標準語言關鍵字、Microsoft 專有關鍵詞和內容特定關鍵字。
ms.custom: index-page
ms.date: 07/25/2020
helpviewer_keywords:
- keywords [C++]
ms.assetid: d7ca94a8-f785-41ce-9f73-d3c4fd508489
ms.openlocfilehash: eaf06522a6d48caeeb84ddefb0e2e172f0af419c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213368"
---
# <a name="keywords-c"></a>關鍵字 (C++)

關鍵字是具有特殊意義的預先定義保留識別項。 它們不能當做程式中的識別碼使用。 下列是 Microsoft C++ 的保留關鍵字。 為 c + +/CX 和 c + +/CLI 指定前置底線和名稱的名稱是 Microsoft extensions。

## <a name="standard-c-keywords"></a>Standard c + + 關鍵字

:::row:::
    :::column:::
        [`alignas`](align-cpp.md)<br/>
        [`alignof`](alignof-operator.md)<br/>
        [`and`](bitwise-and-operator-amp.md)<sup>b</sup><br/>
        [`and_eq`](assignment-operators.md)<sup>b</sup><br/>
        [`asm`](../assembler/inline/asm.md)<sup>a</sup><br/>
        [`auto`](auto-keyword.md)<br/>
        [`bitand`](bitwise-and-operator-amp.md)<sup>b</sup><br/>
        [`bitor`](bitwise-inclusive-or-operator-pipe.md)<sup>b</sup><br/>
        [`bool`](bool-cpp.md)<br/>
        [`break`](break-statement-cpp.md)<br/>
        [`case`](switch-statement-cpp.md)<br/>
        [`catch`](try-throw-and-catch-statements-cpp.md)<br/>
        [`char`](fundamental-types-cpp.md)<br/>
        [`char8_t`](fundamental-types-cpp.md)<sup>c</sup><br/>
        [`char16_t`](char-wchar-t-char16-t-char32-t.md)<br/>
        [`char32_t`](char-wchar-t-char16-t-char32-t.md)<br/>
        [`class`](class-cpp.md)<br/>
        [`compl`](one-s-complement-operator-tilde.md)<sup>b</sup><br/>
        **`concept`**<sup>c</sup><br/>
        [`const`](const-cpp.md)<br/>
        [`const_cast`](const-cast-operator.md)<br/>
        **`consteval`**<sup>c</sup><br/>
        [`constexpr`](constexpr-cpp.md)<br/>
    :::column-end:::
    :::column:::
        **`constinit`**<sup>c</sup><br/>
        [`continue`](continue-statement-cpp.md)<br/>
        **`co_await`**<sup>c</sup><br/>
        **`co_return`**<sup>c</sup><br/>
        **`co_yield`**<sup>c</sup><br/>
        [`decltype`](decltype-cpp.md)<br/>
        [`default`](switch-statement-cpp.md)<br/>
        [`delete`](delete-operator-cpp.md)<br/>
        [`do`](do-while-statement-cpp.md)<br/>
        [`double`](fundamental-types-cpp.md)<br/>
        [`dynamic_cast`](dynamic-cast-operator.md)<br/>
        [`else`](if-else-statement-cpp.md)<br/>
        [`enum`](enumerations-cpp.md)<br/>
        [`explicit`](user-defined-type-conversions-cpp.md)<br/>
        **`export`**<sup>c</sup><br/>
        [`extern`](using-extern-to-specify-linkage.md)<br/>
        [`false`](false-cpp.md)<br/>
        [`float`](fundamental-types-cpp.md)<br/>
        [`for`](for-statement-cpp.md)<br/>
        [`friend`](friend-cpp.md)<br/>
        [`goto`](goto-statement-cpp.md)<br/>
        [`if`](if-else-statement-cpp.md)<br/>
        [`inline`](inline-functions-cpp.md)<br/>
    :::column-end:::
    :::column:::
        [`int`](fundamental-types-cpp.md)<br/>
        [`long`](fundamental-types-cpp.md)<br/>
        [`mutable`](mutable-data-members-cpp.md)<br/>
        [`namespace`](namespaces-cpp.md)<br/>
        [`new`](new-operator-cpp.md)<br/>
        [`noexcept`](noexcept-cpp.md)<br/>
        [`not`](logical-negation-operator-exclpt.md)<sup>b</sup><br/>
        [`not_eq`](equality-operators-equal-equal-and-exclpt-equal.md)<sup>b</sup><br/>
        [`nullptr`](nullptr.md)<br/>
        [`operator`](operator-overloading.md)<br/>
        [`or`](logical-or-operator-pipe-pipe.md)<sup>b</sup><br/>
        [`or_eq`](assignment-operators.md)<sup>b</sup><br/>
        [`private`](private-cpp.md)<br/>
        [`protected`](protected-cpp.md)<br/>
        [`public`](public-cpp.md)<br/>
        [`register`](storage-classes-cpp.md#register) [`reinterpret_cast`](reinterpret-cast-operator.md)<br/>
        **`requires`**<sup>c</sup><br/>
        [`return`](return-statement-cpp.md)<br/>
        [`short`](fundamental-types-cpp.md)<br/>
        [`signed`](fundamental-types-cpp.md)<br/>
        [`sizeof`](sizeof-operator.md)<br/>
        [`static`](storage-classes-cpp.md)<br/>
        [`static_assert`](static-assert.md)<br/>
    :::column-end:::
    :::column:::
        [`static_cast`](static-cast-operator.md)<br/>
        [`struct`](struct-cpp.md)<br/>
        [`switch`](switch-statement-cpp.md)<br/>
        [`template`](templates-cpp.md)<br/>
        [`this`](this-pointer.md)<br/>
        [`thread_local`](storage-classes-cpp.md#thread_local)<br/>
        [`throw`](try-throw-and-catch-statements-cpp.md)<br/>
        [`true`](true-cpp.md)<br/>
        [`try`](try-throw-and-catch-statements-cpp.md)<br/>
        [`typedef`](aliases-and-typedefs-cpp.md)<br/>
        [`typeid`](typeid-operator.md)<br/>
        [`typename`](typename.md)<br/>
        [`union`](unions.md)<br/>
        [`unsigned`](fundamental-types-cpp.md)<br/>
        [`using`](using-declaration.md)清點<br/>
        [`using`](namespaces-cpp.md#using_directives)條<br/>
        [`virtual`](virtual-cpp.md)<br/>
        [`void`](void-cpp.md)<br/>
        [`volatile`](volatile-cpp.md)<br/>
        [`wchar_t`](fundamental-types-cpp.md)<br/>
        [`while`](while-statement-cpp.md)<br/>
        [`xor`](bitwise-exclusive-or-operator-hat.md)<sup>b</sup><br/>
        [`xor_eq`](assignment-operators.md)<sup>b</sup><br/>
    :::column-end:::
:::row-end:::

<sup>a</sup> Microsoft 專有 **`__asm`** 關鍵字會取代 c + + **`asm`** 語法。 **`asm`** 會保留以與其他 c + + 實作為相容性，但不會實作為。 **`__asm`** 在 x86 目標上用於內嵌元件。 Microsoft c + + 不支援其他目標的內嵌組解碼。

<sup>b</sup> [`/permissive-`](../build/reference/permissive-standards-conformance.md) 指定或[ `/Za` \( 停用語言擴充](../build/reference/za-ze-disable-language-extensions.md)功能時，擴充運算子同義字是關鍵字。 當 Microsoft 擴充功能啟用時，它們不是關鍵字。

當指定時支援<sup>c</sup> [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) 。

## <a name="microsoft-specific-c-keywords"></a>Microsoft 特定的 c + + 關鍵字

在 c + + 中，包含兩個連續底線的識別碼會保留給編譯器的執行。 Microsoft 慣例是在 Microsoft 專有關鍵詞前面加上雙底線。 這些單字不能用來做為識別碼名稱。

Microsoft 擴充功能預設為啟用。 若要確保您的程式具備完整的可攜性，您可以在 [`/permissive-`](../build/reference/permissive-standards-conformance.md) 編譯期間指定或停用 [ [ `/Za` \( 語言擴充](../build/reference/za-ze-disable-language-extensions.md)功能]）選項，以停用 Microsoft 擴充功能。 這些選項會停用某些 Microsoft 專有關鍵詞。

啟用 Microsoft 擴充功能後，您可以在程式中使用 Microsoft 專有的關鍵字。 為符合 ANSI 標準，這些關鍵字前面都加上雙底線。 為了回溯相容性，支援許多雙底線關鍵字的單一底線版本。 **`__cdecl`** 關鍵字沒有前置底線。

**`__asm`** 關鍵字會取代 c + + **`asm`** 語法。 **`asm`** 會保留以與其他 c + + 實作為相容性，但不會實作為。 使用 **`__asm`**。

**`__based`** 關鍵字對32位和64位目標編譯的使用有限。

:::row:::
    :::column:::
        [`__alignof`](alignof-operator.md)<sup>e</sup><br/>
        [`__asm`](../assembler/inline/asm.md)<sup>e</sup><br/>
        [`__assume`](../intrinsics/assume.md)<sup>e</sup><br/>
        [`__based`](based-pointers-cpp.md)<sup>e</sup><br/>
        [`__cdecl`](cdecl.md)<sup>e</sup><br/>
        [`__declspec`](declspec.md)<sup>e</sup><br/>
        [`__event`](event.md)<br/>
        [`__except`](try-except-statement.md)<sup>e</sup><br/>
        [`__fastcall`](fastcall.md)<sup>e</sup><br/>
        [`__finally`](try-finally-statement.md)<sup>e</sup><br/>
        [`__forceinline`](inline-functions-cpp.md)<sup>e</sup><br/>
    :::column-end:::
    :::column:::
        [`__hook`](hook.md)<sup>d</sup><br/>
        [`__if_exists`](if-exists-statement.md)<br/>
        [`__if_not_exists`](if-not-exists-statement.md)<br/>
        [`__inline`](inline-functions-cpp.md)<sup>e</sup><br/>
        [`__int16`](int8-int16-int32-int64.md)<sup>e</sup><br/>
        [`__int32`](int8-int16-int32-int64.md)<sup>e</sup><br/>
        [`__int64`](int8-int16-int32-int64.md)<sup>e</sup><br/>
        [`__int8`](int8-int16-int32-int64.md)<sup>e</sup><br/>
        [`__interface`](interface.md)<br/>
        [`__leave`](try-finally-statement.md)<sup>e</sup><br/>
        [`__m128`](m128.md)<br/>
    :::column-end:::
    :::column:::
        [`__m128d`](m128d.md)<br/>
        [`__m128i`](m128i.md)<br/>
        [`__m64`](m64.md)<br/>
        [`__multiple_inheritance`](inheritance-keywords.md)<sup>e</sup><br/>
        [`__ptr32`](ptr32-ptr64.md)<sup>e</sup><br/>
        [`__ptr64`](ptr32-ptr64.md)<sup>版</sup><br/>
        [`__raise`](raise.md)<br/>
        [`__restrict`](extension-restrict.md)<sup>e</sup><br/>
        [`__single_inheritance`](inheritance-keywords.md)<sup>版</sup><br/>
        [`__sptr`](sptr-uptr.md)<sup>版</sup><br/>
        [`__stdcall`](stdcall.md)<sup>e</sup><br/>
    :::column-end:::
    :::column:::
        [`__super`](super.md)<br/>
        [`__thiscall`](thiscall.md)<br/>
        [`__unaligned`](unaligned.md)<sup>e</sup><br/>
        [`__unhook`](unhook.md)<sup>d</sup><br/>
        [`__uptr`](sptr-uptr.md)<sup>e</sup><br/>
        [`__uuidof`](uuidof-operator.md)<sup>e</sup><br/>
        [`__vectorcall`](vectorcall.md)<sup>e</sup><br/>
        [`__virtual_inheritance`](inheritance-keywords.md)<sup>e</sup><br/>
        [`__w64`](w64.md)<sup>e</sup><br/>
        [`__wchar_t`](fundamental-types-cpp.md)<br/>
    :::column-end:::
:::row-end:::

用於事件處理的<sup>d</sup>內建函式。

<sup>e</sup>為了與舊版的回溯相容性，在啟用 Microsoft 擴充功能（預設值）時，可以使用這些關鍵字搭配兩個前置底線和單一前置底線。

## <a name="microsoft-keywords-in-__declspec-modifiers"></a>__Declspec 修飾詞中的 Microsoft 關鍵字

這些識別碼是修飾詞的擴充屬性 **`__declspec`** 。 在該內容中，它們會被視為關鍵字。

:::row:::
    :::column:::
        [`align`](align-cpp.md)<br/>
        [`allocate`](allocate.md)<br/>
        [`allocator`](allocator.md)<br/>
        [`appdomain`](appdomain.md)<br/>
        [`code_seg`](code-seg-declspec.md)<br/>
        [`deprecated`](deprecated-cpp.md)
    :::column-end:::
    :::column:::
        [`dllexport`](dllexport-dllimport.md)<br/>
        [`dllimport`](dllexport-dllimport.md)<br/>
        [`jitintrinsic`](jitintrinsic.md)<br/>
        [`naked`](naked-cpp.md)<br/>
        [`noalias`](noalias.md)<br/>
        [`noinline`](noinline.md)
    :::column-end:::
    :::column:::
        [`noreturn`](noreturn.md)<br/>
        [`nothrow`](nothrow-cpp.md)<br/>
        [`novtable`](novtable.md)<br/>
        [`process`](process.md)<br/>
        [`property`](property-cpp.md)<br/>
        [`restrict`](restrict.md)
    :::column-end:::
    :::column:::
        [`safebuffers`](safebuffers.md)<br/>
        [`selectany`](selectany.md)<br/>
        [`spectre`](spectre.md)<br/>
        [`thread`](thread.md)<br/>
        [`uuid`](uuid-cpp.md)
    :::column-end:::
:::row-end:::

## <a name="ccli-and-ccx-keywords"></a>C + +/CLI 和 c + +/CX 關鍵字

:::row:::
    :::column:::
        [`__abstract`](../dotnet/declaration-of-a-managed-class-type.md)<sup>f</sup><br/>
        [`__box`](../dotnet/value-type-semantics.md)<sup>f</sup><br/>
        [`__delegate`](../dotnet/delegates-and-events.md)<sup>f</sup><br/>
        [`__gc`](../dotnet/declaration-of-a-clr-reference-class-object.md)<sup>f</sup><br/>
        [`__identifier`](../extensions/identifier-cpp-cli.md)<br/>
        [`__nogc`](../dotnet/declaration-of-a-clr-reference-class-object.md)<sup>f</sup><br/>
        [`__noop`](../intrinsics/noop.md)<br/>
        **`__pin`**<sup>f</sup><br/>
        **`__property`**<sup>f</sup><br/>
        **`__sealed`**<sup>f</sup><br/>
    :::column-end:::
    :::column:::
        [`__try_cast`](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)<sup>f</sup><br/>
        [`__value`](../dotnet/value-type-semantics.md)<sup>f</sup><br/>
        [`abstract`](../extensions/abstract-cpp-component-extensions.md)<sup>g</sup><br/>
        [`array`](../extensions/arrays-cpp-component-extensions.md)<sup>g</sup><br/>
        [`as_friend`](../preprocessor/hash-using-directive-cpp.md)<br/>
        [`delegate`](../extensions/delegate-cpp-component-extensions.md)<sup>g</sup><br/>
        [`enum class`](../extensions/enum-class-cpp-component-extensions.md)<br/>
        [`enum struct`](../extensions/enum-class-cpp-component-extensions.md)<br/>
        [`event`](../extensions/event-cpp-component-extensions.md)<sup>g</sup><br/>
    :::column-end:::
    :::column:::
        [`finally`](../dotnet/finally.md)<br/>
        [`for each in`](../dotnet/for-each-in.md)<br/>
        [`gcnew`](../extensions/ref-new-gcnew-cpp-component-extensions.md)<sup>g</sup><br/>
        [`generic`](../extensions/generics-cpp-component-extensions.md)<sup>g</sup><br/>
        [`initonly`](../dotnet/initonly-cpp-cli.md)<br/>
        [`interface class`](../extensions/interface-class-cpp-component-extensions.md)<sup>g</sup><br/>
        [`interface struct`](../extensions/interface-class-cpp-component-extensions.md)<sup>g</sup><br/>
        [`interior_ptr`](../extensions/interior-ptr-cpp-cli.md)<sup>g</sup><br/>
        [`literal`](../extensions/literal-cpp-component-extensions.md)<sup>g</sup><br/>
    :::column-end:::
    :::column:::
        [`new`](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)<sup>g</sup><br/>
        [`property`](../extensions/property-cpp-component-extensions.md)<sup>g</sup><br/>
        [`ref class`](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
        [`ref struct`](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
        [`safecast`](../extensions/safe-cast-cpp-component-extensions.md)<br/>
        [`sealed`](../extensions/sealed-cpp-component-extensions.md)<sup>g</sup><br/>
        [`typeid`](../extensions/typeid-cpp-component-extensions.md)<br/>
        [`value class`](../extensions/classes-and-structs-cpp-component-extensions.md)<sup>g</sup><br/>
        [`value struct`](../extensions/classes-and-structs-cpp-component-extensions.md)<sup>g</sup><br/>
    :::column-end:::
:::row-end:::

<sup>f</sup>僅適用于 Managed Extensions for C++。 這個語法現在不建議使用。 如需詳細資訊，請參閱[執行階段平台的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)。

<sup>f</sup>適用于 c + +/cli

## <a name="see-also"></a>另請參閱

[語彙慣例](lexical-conventions.md)<br/>
[C + + 內建運算子、優先順序和關聯性](cpp-built-in-operators-precedence-and-associativity.md)

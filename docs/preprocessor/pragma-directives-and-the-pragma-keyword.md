---
title: Pragma 指示詞與 __pragma 關鍵字
ms.date: 08/29/2019
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
ms.openlocfilehash: 6cfbcd325dc895719bad5dccc9c19bcda90cdaa0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858070"
---
# <a name="pragma-directives-and-the-__pragma-keyword"></a>Pragma 指示詞與 __pragma 關鍵字

Pragma 指示詞會指定電腦或作業系統特定的編譯器功能。 適用于 Microsoft 編譯器的 **__pragma**關鍵字，可讓您在巨集定義中編寫 pragma 指示詞的程式碼。

## <a name="syntax"></a>語法

> **#pragma** *token-字串*\
> **__pragma （** *token 字串* **）**

## <a name="remarks"></a>備註

C 和 C++ 的每個實作都支援其主機電腦或作業系統獨有的一些功能。 例如，某些程式必須對記憶體中的資料位置進行精確的控制，或是控制某些函數接收參數的方式。 **#Pragma**指示詞提供一種方式，讓每個編譯器提供電腦和作業系統特有的功能，同時維持與 C 和C++語言的整體相容性。

Pragma 是機器或作業系統特定的定義，而且對於每個編譯器通常都不同。 Pragma 可以用於條件指示詞，以提供新的預處理器功能，或提供執行定義的資訊給編譯器。

*Token 字串*是一系列的字元，可提供特定的編譯器指示和引數（如果有的話）。 數位記號（ **#** ）必須是包含 pragma 之行上的第一個非空白字元。 空白字元可以分隔數位記號和 "pragma" 這個字。 在 **#pragma**之後，撰寫翻譯工具可剖析為前置處理標記的任何文字。 **#Pragma**的引數受限於宏擴充。

編譯器會在找到無法辨識的 pragma 時發出警告，並繼續進行編譯。

Microsoft C 和 C++ 編譯器可辨識下列 pragma：

||||
|-|-|-|
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[comment](../preprocessor/comment-c-cpp.md)|
|[component](../preprocessor/component.md)|[符合](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|
|[data_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|
|[function](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|
|[intrinsic](../preprocessor/intrinsic.md)|[迴圈](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|
|[受控](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)|[omp](../preprocessor/omp.md)|
|[once](../preprocessor/once.md)|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|
|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|
|[region、endregion](../preprocessor/region-endregion.md)|[runtime_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|
|[setlocale](../preprocessor/setlocale.md)|[strict_gs_check](../preprocessor/strict-gs-check.md)|[納入](../preprocessor/managed-unmanaged.md)|
|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|[warning](../preprocessor/warning.md)||

<sup>1</sup>只有C++編譯器才支援。

## <a name="pragmas-and-compiler-options"></a>Pragma 和編譯器選項

有些 pragma 提供與編譯器選項相同的功能。 當 pragma 在原始程式碼中出現時，它會覆寫編譯器選項指定的行為。 例如，如果您指定了[了/zp8](../build/reference/zp-struct-member-alignment.md)，您可以針對程式碼的特定區段，使用[pack](../preprocessor/pack.md)來覆寫此編譯器設定：

```cmd
cl /Zp8 some_file.cpp
```

```cpp
// some_file.cpp - packing is 8
// ...
#pragma pack(push, 1) - packing is now 1
// ...
#pragma pack(pop) - packing is 8 again
// ...
```

## <a name="the-__pragma-keyword"></a>__Pragma （）關鍵字

編譯器也支援 Microsoft 專有的 **__pragma**關鍵字，其功能與 **#pragma**指示詞相同。 差別在於， **__pragma**關鍵字在巨集定義中可供內嵌使用。 **#Pragma**指示詞無法在巨集定義中使用，因為編譯器會將指示詞中的數位記號字元（' # '）解讀為[字串化運算子（#）](../preprocessor/stringizing-operator-hash.md)。

下列程式碼範例會示範如何在宏中使用 **__pragma**關鍵字。 這段程式碼摘錄自＜編譯器 COM 支援範例＞中 ACDUAL 範本的 mfcdual.h 標頭：

```cpp
#define CATCH_ALL_DUAL \
CATCH(COleException, e) \
{ \
_hr = e->m_sc; \
} \
AND_CATCH_ALL(e) \
{ \
__pragma(warning(push)) \
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \
AFX_MANAGE_STATE(pThis->m_pModuleState); \
__pragma(warning(pop)) \
_hr = DualHandleException(_riidSource, e); \
} \
END_CATCH_ALL \
return _hr; \
```

## <a name="see-also"></a>請參閱

[C/C++預處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)\
[C pragma](../c-language/c-pragmas.md)\
[關鍵字](../cpp/keywords-cpp.md)

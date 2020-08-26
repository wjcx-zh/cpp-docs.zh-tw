---
title: C Pragma
ms.date: 07/26/2020
helpviewer_keywords:
- pragmas, C/C++
ms.assetid: 3d6d36b4-d565-4632-a4cd-e39aeaded5ad
ms.openlocfilehash: ce8efb54eacf40a9feb7b629c2a61a32b3a71b79
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845207"
---
# <a name="c-pragmas"></a>C Pragma

**Microsoft 特定的**

*Pragma*會指示編譯器在編譯時期執行特定的動作。 不同編譯器的 pragma 也會不同。 例如，您可以使用 `optimize` pragma 來設定要在程式上執行的優化。 Microsoft C pragma 包括：

:::row:::
    :::column:::
        [`alloc_text`](../preprocessor/alloc-text.md)\
        [`auto_inline`](../preprocessor/auto-inline.md)\
        [`bss_seg`](../preprocessor/bss-seg.md)\
        [`check_stack`](../preprocessor/check-stack.md)\
        [`code_seg`](../preprocessor/code-seg.md)\
        [`comment`](../preprocessor/comment-c-cpp.md)\
        [`component`](../preprocessor/component.md)\
        [`const_seg`](../preprocessor/const-seg.md)\
        [`data_seg`](../preprocessor/data-seg.md)
    :::column-end:::
    :::column:::
        [`deprecated`](../preprocessor/deprecated-c-cpp.md)\
        [`detect_mismatch`](../preprocessor/detect-mismatch.md)\
        [`fenv_access`](../preprocessor/fenv-access.md)\
        [`float_control`](../preprocessor/float-control.md)\
        [`fp_contract`](../preprocessor/fp-contract.md)\
        [`function`](../preprocessor/function-c-cpp.md)\
        [`hdrstop`](../preprocessor/hdrstop.md)\
        [`include_alias`](../preprocessor/include-alias.md)\
        [`inline_depth`](../preprocessor/inline-depth.md)
    :::column-end:::
    :::column:::
        [`inline_recursion`](../preprocessor/inline-recursion.md)\
        [`intrinsic`](../preprocessor/intrinsic.md)\
        [`make_public`](../preprocessor/make-public.md)\
        [`managed`](../preprocessor/managed-unmanaged.md)\
        [`message`](../preprocessor/message.md)\
        [`omp`](../preprocessor/omp.md)\
        [`once`](../preprocessor/once.md)\
        [`optimize`](../preprocessor/optimize.md)\
        [`pack`](../preprocessor/pack.md)
    :::column-end:::
    :::column:::
        [`pop_macro`](../preprocessor/pop-macro.md)\
        [`push_macro`](../preprocessor/push-macro.md)\
        [`region`, `endregion`](../preprocessor/region-endregion.md)\
        [`runtime_checks`](../preprocessor/runtime-checks.md)\
        [`section`](../preprocessor/section.md)\
        [`setlocale`](../preprocessor/setlocale.md)\
        [`strict_gs_check`](../preprocessor/strict-gs-check.md)\
        [`unmanaged`](../preprocessor/managed-unmanaged.md)\
        [`warning`](../preprocessor/warning.md)
    :::column-end:::
:::row-end:::

如需 Microsoft C 編譯器 pragma 的描述，請參閱 Pragma 指示詞 [和 `__Pragma` 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md) 。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[原始程式檔和來來源程式](../c-language/source-files-and-source-programs.md)

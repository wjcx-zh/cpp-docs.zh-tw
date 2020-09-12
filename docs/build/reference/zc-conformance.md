---
title: /Zc (一致性)
description: /Zc 一致性編譯器選項會啟用或停用符合或回溯相容行為的支援。
ms.date: 09/10/2020
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 13e06cd75f1ee684c2ee1ad6239aeb77b805675e
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041519"
---
# <a name="zc-conformance"></a>`/Zc` (一致性) 

您可以使用 **`/Zc`** 編譯器選項來指定標準或 Microsoft 特定的編譯器行為。

## <a name="syntax"></a>語法

> **`/Zc:`**_選項_{，_option_}

## <a name="remarks"></a>備註

當 Visual Studio 已對與標準不相容的 C 或 c + + 執行延伸模組時，您可以使用 [ **`/Zc`** 一致性] 選項來指定符合標準的或 Microsoft 特定的行為。 針對某些選項，Microsoft 特有的行為是預設值，以防止對現有程式碼進行大規模的重大變更。 在其他情況下，預設值是標準行為，也就是安全性、效能或相容性的增強功能，比重大變更的成本更高。 在較新版本的 Visual Studio 中，每個一致性選項的預設設定可能會變更。 如需每個一致性選項的詳細資訊，請參閱特定選項的主題。 [`/permissive-`](permissive-standards-conformance.md)編譯器選項會隱含地將不是預設設定的一致性選項設定為一致的設定。

這些是 **`/Zc`** 編譯器選項：

| 選項 | 行為 |
|--|--|
| [`/Zc:alignedNew`](zc-alignednew.md) | 在 c + + 17) 中預設啟用 c + + 17 過度對齊的動態配置 (。 |
| [`/Zc:auto`](zc-auto-deduce-variable-type.md) | 針對預設的 (強制執行新的標準 c + + 意義 **`auto`**) 。 |
| [`/Zc__cplusplus`](zc-cplusplus.md) | 啟用 `__cplusplus` 宏以根據預設，將支援的標準 (報告) 。 |
| [`/Zc:externConstexpr`](zc-externconstexpr.md) | **`constexpr`** 預設) 啟用變數 (預設的外部連結。 |
| [`/Zc:forScope`](zc-forscope-force-conformance-in-for-loop-scope.md) | 根據預設，強制執行標準 c + + **`for`** 範圍規則 () 。 |
| [`/ZcimplicitNoexcept`](zc-implicitnoexcept-implicit-exception-specifiers.md) | 依預設，在必要的函式上啟用隱含 **`noexcept`** () 。 |
| [`/Zc:inline`](zc-inline-remove-unreferenced-comdat.md) | 移除未參考的函式或資料（如果它是 COMDAT），或只有預設為內部連結 (預設) 。 |
| [`/Zc:noexceptTypes`](zc-noexcepttypes.md) | 在 **`noexcept`** c + + 17 或更新版本中，預設會強制執行 c + + 17 規則 () 。 |
| [`/Zc:preprocessor`](zc-preprocessor.md) | 根據預設，請使用新的符合預處理器 (off，但 C11/C17) 除外。 |
| [`/Zc:referenceBinding`](zc-referencebinding-enforce-reference-binding-rules.md) | UDT 暫時不會系結至預設)  (關閉的非 const 左值參考。 |
| [`/Zc:rvalueCast`](zc-rvaluecast-enforce-type-conversion-rules.md) | 依預設，強制執行標準 c + + 明確類型轉換規則 () 。 |
| [`/Zc:sizedDealloc`](zc-sizeddealloc-enable-global-sized-dealloc-functions.md) | 依預設， (開啟 c + + 14 全域大小的解除配置函數) 。 |
| [`/Zc:strictStrings`](zc-strictstrings-disable-string-literal-type-conversion.md) | 預設會停用字串 `char*` 常 `wchar_t*` 值或轉換 (關閉) 。 |
| [`/Zc:ternary`](zc-ternary.md) | 依預設，對運算元類型強制執行條件運算子規則 (off) 。 |
| [`/Zc:threadSafeInit`](zc-threadsafeinit-thread-safe-local-static-initialization.md) | 預設) 啟用安全線程本機靜態初始化 (。 |
| [`/Zc:throwingNew`](zc-throwingnew-assume-operator-new-throws.md) | 假設 **`operator new`** 在失敗 (預設會擲回) 。 |
| [`/Zc:trigraphs`](zc-trigraphs-trigraphs-substitution.md) | 啟用三並詞 (過時，預設) 。 |
| [`/Zc:twoPhase`](zc-twophase.md) | 使用不符合規範的範本剖析行為 (預設) 。 |
| [`/Zc:wchar_t`](zc-wchar-t-wchar-t-is-native-type.md) | **`wchar_t`** 是原生類型，預設) 不是 typedef (。 |

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)

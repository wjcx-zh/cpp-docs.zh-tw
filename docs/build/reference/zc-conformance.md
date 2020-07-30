---
title: /Zc (一致性)
ms.date: 03/06/2018
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 6d6d3b7736fd1775372a3b2093c53e177db5099e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234350"
---
# <a name="zc-conformance"></a>`/Zc`標準

您可以使用 **`/Zc`** 編譯器選項來指定標準或 Microsoft 特定的編譯器行為。

## <a name="syntax"></a>語法

> **`/Zc:`**_選項_{，_option_}

## <a name="remarks"></a>備註

當 Visual Studio 將擴充功能實作為與標準不相容的 C 或 c + + 時，您可以使用 **`/Zc`** 一致性選項來指定符合標準或 Microsoft 特定的行為。 針對某些選項，Microsoft 特有的行為是預設值，以防止對現有程式碼進行大規模的重大變更。 在其他情況下，預設值是標準行為，在此情況下，安全性、效能或相容性的改善會超過中斷性變更的成本。 在較新版本的 Visual Studio 中，每個一致性選項的預設設定可能會變更。 如需每個一致性選項的詳細資訊，請參閱特定選項的主題。 [`/permissive-`](permissive-standards-conformance.md)編譯器選項會以隱含方式將預設未設定的一致性選項設定為其一致的設定。

以下是 **`/Zc`** 編譯器選項：

| 選項 | 行為 |
|--|--|
| [`/Zc:alignedNew`](zc-alignednew.md) | 啟用 c + + 17 過度對齊的動態配置（在 c + + 17 中預設為開啟）。 |
| [`/Zc:auto`](zc-auto-deduce-variable-type.md) | 針對（預設為開啟）強制執行新的 Standard c + + 意義 **`auto`** 。 |
| [`/Zc__cplusplus`](zc-cplusplus.md) | 啟用 `__cplusplus` 宏以報告支援的標準（預設為關閉）。 |
| [`/Zc:externConstexpr`](zc-externconstexpr.md) | 啟用變數的外部連結 **`constexpr`** （預設為關閉）。 |
| [`/Zc:forScope`](zc-forscope-force-conformance-in-for-loop-scope.md) | 強制執行標準 c + + **`for`** 範圍規則（預設為開啟）。 |
| [`/ZcimplicitNoexcept`](zc-implicitnoexcept-implicit-exception-specifiers.md) | 啟用隱含 **`noexcept`** 的必要函數（預設為開啟）。 |
| [`/Zc:inline`](zc-inline-remove-unreferenced-comdat.md) | 如果未參考的函式或資料已 COMDAT，或是只有內部連結（預設為關閉），請將其移除。 |
| [`/Zc:noexceptTypes`](zc-noexcepttypes.md) | 強制執行 c + + 17 **`noexcept`** 規則（在 c + + 17 或更新版本中預設為開啟）。 |
| [`/Zc:referenceBinding`](zc-referencebinding-enforce-reference-binding-rules.md) | UDT 暫存不會系結至非 const 左值參考（預設為關閉）。 |
| [`/Zc:rvalueCast`](zc-rvaluecast-enforce-type-conversion-rules.md) | 強制執行標準 c + + 明確類型轉換規則（預設為關閉）。 |
| [`/Zc:sizedDealloc`](zc-sizeddealloc-enable-global-sized-dealloc-functions.md) | 啟用 c + + 14 全域大小的解除配置函式（預設為開啟）。 |
| [`/Zc:strictStrings`](zc-strictstrings-disable-string-literal-type-conversion.md) | 停用字串常 `char*` 值或 `wchar_t*` 轉換（預設為關閉）。 |
| [`/Zc:ternary`](zc-ternary.md) | 強制執行運算元類型的條件運算子規則（預設為關閉）。 |
| [`/Zc:threadSafeInit`](zc-threadsafeinit-thread-safe-local-static-initialization.md) | 啟用安全線程本機靜態初始化（預設為開啟）。 |
| [`/Zc:throwingNew`](zc-throwingnew-assume-operator-new-throws.md) | 假設 **`operator new`** 失敗時擲回（預設為關閉）。 |
| [`/Zc:trigraphs`](zc-trigraphs-trigraphs-substitution.md) | 啟用三並詞（預設為已淘汰，關閉）。 |
| [`/Zc:twoPhase`](zc-twophase.md) | 使用不符合標準的範本剖析行為（預設為符合）。 |
| [`/Zc:wchar_t`](zc-wchar-t-wchar-t-is-native-type.md) | **`wchar_t`** 是原生類型，而非 typedef （預設為開啟）。 |

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)

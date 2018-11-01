---
title: /Zc (一致性)
ms.date: 03/06/2018
f1_keywords:
- /zc
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: b1f612040eea0078b0f27cf72327db94fe9e2939
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665425"
---
# <a name="zc-conformance"></a>/Zc (一致性)

您可以使用 **/Zc**編譯器選項，以指定標準或 Microsoft 專屬編譯器行為。

## <a name="syntax"></a>語法

> **/ Zc:**_選項_{，_選項_}

## <a name="remarks"></a>備註

當 Visual Studio 已實作 C 或 c + + 不是與標準相容的延伸模組時，您可以使用`/Zc`一致性選項，以指定標準符合或 Microsoft 專有的行為。 一些選項，如 Microsoft 特有的行為會是預設值，以防止大規模重大變更對現有程式碼。 在其他情況下，預設值會是標準的行為，其中改善安全性、 效能或相容性遠大於的重大變更的成本。 較新版本的 Visual Studio 可能會變更每個合規性選項的預設設定。 如需有關每個合規性選項的詳細資訊，請參閱特定選項的主題。 [/Permissive--](permissive-standards-conformance.md)編譯器選項會隱含地設定未設定預設會將其符合標準設定的合規性選項。

這些是`/Zc`編譯器選項：

|選項|行為|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|啟用 C + + 17 過度對齊動態配置 （預設在 C + + 17）。|
|[自動\[-\]](zc-auto-deduce-variable-type.md)|強制執行新的 Standard c + + 意義，如`auto`(在預設情況下)。|
|[__cplusplus\[-\]](zc-cplusplus.md)|啟用 **__cplusplus**巨集來回報受支援的標準 （預設為關閉）。|
|[externConstexpr\[-\]](zc-externconstexpr.md)|啟用外部連結的`constexpr`變數 （預設為關閉）。|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|強制執行標準 c + +`for`範圍規則 (在預設情況下)。|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|啟用隱含`noexcept`對必要函式 (在預設情況下)。|
|[內嵌\[-\]](zc-inline-remove-unreferenced-comdat.md)|如果為 COMDAT 或只有內部連結移除未參考的函式或資料 （預設為關閉）。|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|強制執行 c++17 noexcept 規則 (在預設情況下在 C + + 17 或更新版本)。|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|UDT 暫時不會繫結至非 const 左值參考 （預設為關閉）。|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|強制執行標準 c + + 明確類型轉換規則 （預設為關閉）。|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|啟用 C + + 14 全域調整大小的解除配置函式 (在預設情況下)。|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|停用字串常值至`char*`或`wchar_t*`轉換 （預設為關閉）。|
|[ternary\[-\]](zc-ternary.md)|強制執行條件式運算子運算元類型的規則 （預設為關閉）。|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|啟用安全執行緒本機靜態初始設定 (在預設情況下)。|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|假設`operator new`失敗時擲回 （預設為關閉）。|
|[三併詞\[-\]](zc-trigraphs-trigraphs-substitution.md)|啟用三併詞 （已過時，關閉的預設值）。|
|[twoPhase-](zc-twophase.md)|使用不合格的樣板剖析 （符合預設情況下） 的行為。|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` 原生型別不是 typedef (在預設情況下)。|

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="see-also"></a>另請參閱

[編譯器選項](compiler-options.md)<br/>
[設定編譯器選項](setting-compiler-options.md)

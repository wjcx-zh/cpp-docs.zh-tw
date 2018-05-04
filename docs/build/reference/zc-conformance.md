---
title: /Zc （一致性） |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zc
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8b87774b9c011d6ea5ab92d3c1b44e4af2b6091
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="zc-conformance"></a>/Zc (一致性)

您可以使用 **/Zc**編譯器選項來指定標準或 Microsoft 專屬編譯器行為。

## <a name="syntax"></a>語法

> **/ Zc:**_選項_{，_選項_}

## <a name="remarks"></a>備註

當 Visual Studio 已實作的 C 或 c + + 不是與標準相容的擴充功能時，您可以使用`/Zc`一致性選項來指定標準符合或 Microsoft 特定的行為。 某些選項，Microsoft 特定行為的預設值是，若要避免大規模的重大變更對現有程式碼。 在其他情況下，預設會為標準的行為，其中改善安全性、 效能或相容性優先於高層的重大變更的成本。 較新版本的 Visual Studio 可能會變更每個一致性選項的預設設定。 如需有關每個一致性選項的詳細資訊，請參閱特定選項的主題。 [/ 寬鬆-](permissive-standards-conformance.md)編譯器選項會隱含地設定不由其符合設定的預設設定的一致性選項。

這些是`/Zc`編譯器選項：

|選項|行為|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|啟用 C + + 17 過度對齊動態配置 （預設在 C + + 17）。|
|[自動\[-\]](zc-auto-deduce-variable-type.md)|強制執行針對新的標準 c + + 意義`auto`(在預設情況下)。|
|[externConstexpr\[-\]](zc-externconstexpr.md)|啟用外部連結的`constexpr`變數 （預設為關閉）。|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|強制執行標準 c + +`for`設定規則的範圍 (在預設情況下)。|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|啟用隱含`noexcept`對必要函式 (在預設情況下)。|
|[內嵌\[-\]](zc-inline-remove-unreferenced-comdat.md)|如果它是 COMDAT 或只有內部連結中移除未參考的函式或資料 （預設為關閉）。|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|強制執行 C + + 17 noexcept 規則 (上依預設，在 C + + 17 或更新版本)。|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|UDT 暫存不會繫結到非 const 左值參考 （預設為關閉）。|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|強制執行標準 c + + 明確類型轉換規則 （預設為關閉）。|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|啟用 C + + 14 全域調整大小解除配置函式 (在預設情況下)。|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|停用字串常值至`char*`或`wchar_t*`轉換 （預設為關閉）。|
|[ternary\[-\]](zc-ternary.md)|強制執行條件運算子的運算元類型的規則 （預設為關閉）。|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|啟用安全執行緒本機靜態初始設定 (在預設情況下)。|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|假設`operator new`在失敗時擲回 （預設為關閉）。|
|[三併詞\[-\]](zc-trigraphs-trigraphs-substitution.md)|啟用三併詞 （已過時，關閉的預設值）。|
|[twoPhase-](zc-twophase.md)|使用不合格的範本，剖析行為 （預設為不符合）。|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` 是原生類型，而不是 typedef (在預設情況下)。|

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

## <a name="see-also"></a>另請參閱

[編譯器選項](compiler-options.md)  
[設定編譯器選項](setting-compiler-options.md)

---
title: /Zc:wchar_t (wchar_t 是原生類型)
ms.date: 03/01/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
ms.openlocfilehash: 114ed4a279b66571c0dc81fc1139dcdc59c17eae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234311"
---
# <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t (wchar_t 是原生類型)

**`wchar_t`** 根據 c + + 標準剖析為內建類型。

## <a name="syntax"></a>語法

> **/Zc： wchar_t**[ **-** ]

## <a name="remarks"></a>備註

如果 **/zc： wchar_t**是 on， **`wchar_t`** 則在編譯為 c + + 的程式碼中，是內建整數類型的關鍵字。 如果指定了 **/zc： wchar_t-** （含減號），或在編譯為 C 的程式碼中， **`wchar_t`** 則不是內建類型。 相反 **`wchar_t`** 地， **`typedef`** **`unsigned short`** 在標準標頭 stddef.h 中會將定義為的。 （Microsoft 執行會將它定義在 stddef.h 所包含的另一個標頭中，以及其他標準標頭）。

我們不建議使用 **/zc： wchar_t-** 因為 c + + 標準要求 **`wchar_t`** 必須是內建類型。 使用 **`typedef`** 版本可能會造成可攜性問題。 如果您從舊版 Visual Studio 升級，且因為程式碼嘗試以隱含方式將轉換成，而遇到編譯器錯誤[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) **`wchar_t`** **`unsigned short`** ，建議您變更程式碼以修正錯誤，而不是設定 **/zc： wchar_t-**。

根據預設，在 c + + 編譯中， **/zc： wchar_t**選項是 on，而在 c 編譯中則會忽略。 [/Permissive-](permissive-standards-conformance.md)選項不會影響 **/zc： wchar_t**。

Microsoft 會 **`wchar_t`** 將實作為雙位元組不帶正負號的值。 它會對應至 Microsoft 特定的原生類型 **`__wchar_t`** 。 如需的詳細資訊 **`wchar_t`** ，請參閱[資料類型範圍](../../cpp/data-type-ranges.md)和[基本類型](../../cpp/fundamental-types-cpp.md)。

如果您撰寫的新程式碼必須與仍使用版本的舊版程式碼交互操作 **`typedef`** **`wchar_t`** ，您可以為和的變化提供多載 **`unsigned short`** **`__wchar_t`** **`wchar_t`** ，以便將您的程式碼與使用 **/zc： wchar_t**或不含它編譯的程式碼進行連結。 否則，您必須提供兩個不同的程式庫組建，一個包含，一個不含 **/zc： wchar_t**啟用。 縱使在這種情況，我們仍然建議您以編譯新程式碼所使用的相同編譯器建置較舊的程式碼。 切勿混合不同編譯器所編譯的二進位檔。

指定 **/zc： wchar_t**時，會定義** \_ wchar \_ t \_ 定義**和** \_ 原生 \_ wchar \_ t \_ 定義**的符號。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。

如果您的程式碼使用編譯器 COM 全域函式，因為 **/zc： wchar_t**預設為開啟，建議您將明確的參考變更為 comsupp.lib （從[批註 pragma](../../preprocessor/comment-c-cpp.md)或在命令列上）至 comsuppw.lib 或 comsuppwd.lib。 （如果您必須使用 **/zc： wchar_t**進行編譯，請使用 comsupp.lib）。如果您包含 comdef.h 標頭檔，則會為您指定正確的程式庫。 如需編譯器 COM 支援的詳細資訊，請參閱[編譯器 Com 支援](../../cpp/compiler-com-support.md)。

**`wchar_t`** 當您編譯 C 程式碼時，不支援內建類型。 如需 Visual C++ 之一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **語言**] 頁面。

1. 修改 [將**Wchar_t 視為內建類型**] 屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A> ＞。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)<br/>

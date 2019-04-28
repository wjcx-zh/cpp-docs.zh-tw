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
ms.openlocfilehash: b2563ba0ae2a07bc9f9d81128745ed4b9651fb6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315634"
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t 是原生類型)

根據 C++ 標準將 `wchar_t` 解析為內建類型。

## <a name="syntax"></a>語法

> **/Zc:wchar_t**[**-**]

## <a name="remarks"></a>備註

如果 **/zc: wchar_t**所在`wchar_t`是編譯為程式碼中的內建整數類資料類型的關鍵字C++。 如果 **/zc: wchar_t-** （以負號開頭） 指定，或在程式碼編譯為 C，`wchar_t`不是內建的型別。 相反地，`wchar_t`指`typedef`如`unsigned short`標準標頭檔 stddef.h 中。 （Microsoft 實作定義其在 stddef.h 中包含的另一個標頭和其他標準標頭中）。

我們不建議 **/zc: wchar_t-** 因為C++標準要求`wchar_t`是內建的類型。 使用 `typedef` 版本可能會造成可攜性問題。 如果您從視覺效果的舊版升級C++而遇到編譯器錯誤[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)因為程式碼嘗試以隱含方式轉換`wchar_t`要`unsigned short`，我們建議您變更程式碼以修正錯誤，而不是設定 **/zc: wchar_t-**。

**/Zc: wchar_t**選項是否開啟，預設會在C++編譯，而且會忽略在 C 編譯中。 [/Permissive--](permissive-standards-conformance.md)選項並不會影響 **/zc: wchar_t**。

Microsoft 將 `wchar_t` 實作為二位元的不帶正負號值。 它會對應至 Microsoft 特定原生類型`__wchar_t`。 如需詳細資訊`wchar_t`，請參閱 <<c2> [ 資料類型範圍](../../cpp/data-type-ranges.md)並[基本類型](../../cpp/fundamental-types-cpp.md)。

如果您要撰寫新程式碼必須與仍使用舊版程式碼交互操作`typedef`新版`wchar_t`，您可以提供多載兩個`unsigned short`並`__wchar_t`的變化`wchar_t`，如此一來，您的程式碼可以連結使用程式碼編譯 **/zc: wchar_t**或沒有它所編譯的程式碼。 否則，您必須提供兩個不同組建的程式庫，一個使用，不含 **/zc: wchar_t**啟用。 縱使在這種情況，我們仍然建議您以編譯新程式碼所使用的相同編譯器建置較舊的程式碼。 切勿混合不同編譯器所編譯的二進位檔。

當 **/zc: wchar_t**指定，則 **\_WCHAR\_T\_定義** 並 **\_原生\_WCHAR\_T\_定義** 符號定義。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。

如果您的程式碼會使用編譯器 COM 全域函式，因為 **/zc: wchar_t**現在在預設情況下，我們建議您變更 comsupp.lib 的明確參考 (從[註解 pragma](../../preprocessor/comment-c-cpp.md)或命令列） 為 comsuppw.lib 或 comsuppwd.lib。 (如果您必須以編譯 **/zc: wchar_t-**，使用 comsupp.lib。)如果您包含 comdef.h 標頭檔，則會為您指定正確的程式庫。 編譯器 COM 支援的相關資訊，請參閱[編譯器 COM 支援](../../cpp/compiler-com-support.md)。

`wchar_t`編譯 C 程式碼時，不支援內建的類型。 如需有關具有視覺效果的一致性問題C++，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **組態屬性** > **C /C++** > **語言**頁面。

1. 修改**將 wchar_t 當做 Built-in 類型**屬性。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)<br/>

---
title: /w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)
description: Microsoft C/C++編譯器選項的參考：/W、/W0、/W1、/W2、/W3、/W4、/W1、/W2、/W3、/W4、/Wall、/wd、/we、/Wo、/WV 和/WX。
ms.date: 01/31/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarningLevel
- VC.Project.VCCLWCECompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarnAsError
- VC.Project.VCCLWCECompilerTool.WarnAsError
- /wx
- VC.Project.VCCLWCECompilerTool.WarningLevel
- /wall
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- /Wv
- /w0
- /w1
- /w2
- /w3
- /w4
- /wd
- /we
- /wo
helpviewer_keywords:
- /W1 compiler option [C++]
- w compiler option [C++]
- -wo compiler option [C++]
- Warning Level compiler option
- W1 compiler option [C++]
- -we compiler option [C++]
- /WX compiler option [C++]
- -wd compiler option [C++]
- WX compiler option [C++]
- wo compiler option [C++]
- Wall compiler option [C++]
- /w compiler option
- W2 compiler option [C++]
- -W2 compiler option [C++]
- wd compiler option [C++]
- /we compiler option [C++]
- we compiler option [C++]
- -W1 compiler option [C++]
- -W4 compiler option [C++]
- -Wall compiler option [C++]
- /Wall compiler option [C++]
- -W0 compiler option [C++]
- W0 compiler option [C++]
- -WX compiler option [C++]
- /wo compiler option [C++]
- W4 compiler option [C++]
- W3 compiler option [C++]
- /wd compiler option [C++]
- warnings, as errors compiler option
- /W3 compiler option [C++]
- /W0 compiler option [C++]
- /W4 compiler option [C++]
- -W3 compiler option [C++]
- -w compiler option [C++]
- /W2 compiler option [C++]
- /Wv compiler option [C++]
ms.openlocfilehash: 80b6d0c1fe684de9af62683a75f0fd1107a94089
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972166"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、/we、/wo、/Wv、/WX (警告層級)

指定編譯器如何對指定的編譯產生警告。

## <a name="syntax"></a>語法

> **/w**\
> **/W0**\
> **/W1**\
> **/W2**\
> **/W3**\
> **/W4**\
> **/Wall**\
> **/Wv**\[ **：** _版本_] \
> **/Wx**\
> **/w1**_警告_\
> **/w2**_警告_\
> **/w3**_警告_\
> **/w4**_警告_\
> **/wd**_警告_\
> **/we**_警告_\
> **/wo**_警告_

## <a name="remarks"></a>備註

警告選項會指定要顯示的編譯器警告，以及整個編譯的警告行為。

警告選項和相關引數會在下表中說明：

選項 | 描述
------ | -----------
**/w** | 抑制所有編譯器警告。
**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4** | 指定編譯器要產生的警告層級。 有效的警告層級範圍從0到4：<br />**/W0**會隱藏所有警告。 它相當於 **/w**。<br />**/W1**顯示層級1（嚴重）警告。 **/W1**是命令列編譯器中的預設設定。<br />**/W2**會顯示層級1和層級2（重大）警告。<br />**/W3**會顯示層級1、層級2和層級3（生產品質）警告。 **/W3**是 IDE 中的預設設定。<br />**/W4**會顯示層級1、層級2和層級3警告，以及預設不會關閉的所有層級4（資訊）警告。 建議您使用此選項來提供不類似不起毛的警告。 針對新的專案，最好在所有編譯中使用 **/W4** 。 此選項有助於確保難以找到的程式碼缺失最少。
**/Wall** | 顯示 **/W4**顯示的所有警告以及 **/W4**不包含的所有其他警告，例如，預設為關閉的警告。 如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。
**/Wv**\[ **：** _版本_] | 只顯示*版本*編譯器版本和更早版本中引進的警告。 當您遷移至較新版本的編譯器時，可以使用此選項來隱藏程式碼中的新警告。 它可讓您在修正時，維護現有的組建進程。 選擇性參數*版本*採用*nn*\[格式。*mm*\[。*aaaaa-bbbbb-ccccc-dddddd-eeeeee*]]，其中*nn*是主要版本號碼， *mm*是選擇性的次要版本號碼，而*aaaaa-bbbbb-ccccc-dddddd-eeeeee*則是編譯器的選擇性組建編號。 例如，使用 **/Wv： 17** ，只顯示 Visual Studio 2012 （主要版本17）或更早版本中引進的警告。 也就是說，它會顯示版本低於或小於17的任何編譯器版本的警告。 它會隱藏 Visual Studio 2013 （主要版本18）和更新版本中引進的警告。 根據預設， **/Wv**會使用目前的編譯器版本號碼，而且不會隱藏警告。 如需編譯器版本隱藏哪些警告的相關資訊，請參閱編譯器[版本的編譯器警告](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md)。
**/WX** | 將所有編譯器警告視為錯誤。 針對新的專案，最好在所有編譯中使用 **/wx** ;解決所有警告可確保難以找到的程式碼缺失越少。<br /><br /> 連結器也具有 **/wx**選項。 如需詳細資訊，請參閱 [/WX (將連結器警告視為錯誤)](wx-treat-linker-warnings-as-errors.md)。

下列選項彼此互斥。 從這個群組指定的最後一個選項就是套用的一個：

選項 | 描述
------ | -----------
**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/w4**_nnnn_ | 針對_nnnn_所指定的警告編號，設定警告層級。 這些選項可讓您在設定特定警告層級時，變更該警告的編譯器行為。 您可以搭配其他警告選項使用這些選項，針對警告強制執行您自己的編碼標準，而不是 Visual Studio 所提供的預設值。<br /><br /> 例如， **/w34326**會導致將 C4326 產生為層級3警告，而不是層級1。 如果您同時使用 **/w34326**選項和 **/W2**選項進行編譯，則不會產生警告 C4326。
**/wd**_nnnn_ | 抑制_nnnn_所指定的編譯器警告。<br /><br /> 例如， **/wd4326**會隱藏編譯器警告 C4326。
**/we**_nnnn_ | 將_nnnn_所指定的編譯器警告視為錯誤。<br /><br /> 例如， **/we4326**會導致編譯器將警告編號 C4326 視為錯誤。
**/wo**_nnnn_ | 報告只由_nnnn_指定一次的編譯器警告。<br /><br /> 例如， **/wo4326**會使警告 C4326 只報告一次，這是編譯器第一次遇到的時候。

如果您在建立先行編譯標頭檔時使用任何警告選項，則會保留這些設定。 使用先行編譯標頭檔時，這些相同的警告選項會再度生效。 若要覆寫先行編譯的標頭警告選項，請在命令列上設定另一個警告選項。

您可以使用[#pragma warning](../../preprocessor/warning.md)指示詞，控制在編譯時期於特定原始程式檔中報告的警告層級。

在原始程式碼中的警告 pragma 指示詞不會受到 **/w**選項的影響。

[組建錯誤檔](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)描述警告和警告層級，並指出某些語句可能不會如您預期地編譯的原因。

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>若要在 Visual Studio 開發環境中設定編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 若要設定 **/W0**、 **/W1**、 **/W2**、 **/W3**、 **/W4**、 **/Wall**、 **/Wv**、 **/wx**或 **/WX-** 選項，請選取  **Configuration Properties**  > **C/C++**  > **General**。

   - 若要設定 **/W0**、 **/W1**、 **/W2**、 **/W3**、 **/W4**或 **/Wall**選項，請修改 [**警告層級**] 屬性。

   - 若要設定 **/wx**或 **/WX-** 選項，請修改 [將**警告視為錯誤**] 屬性。

   - 若要設定 **/Wv**選項的版本，請在 [**警告版本**] 屬性中輸入編譯器版本號碼。

1. 若要設定 **/wd**或 **/we**選項，請 > [ **C/C++**  > **Advanced** ] 屬性頁中選取 [ **Configuration Properties** ]。

   - 若要設定 **/wd**選項，請選取 [**停用特定警告**] 屬性下拉式清單控制項，然後選擇 [**編輯**]。 在 [**停用特定警告**] 對話方塊的 [編輯] 方塊中，輸入警告編號。 若要輸入一個以上的警告，請使用分號（ **;** ）來分隔這些值。 例如，若要停用 C4001 和 C4010，請輸入**4001; 4010**。 選擇 **[確定]** 儲存您的變更，並返回 [**屬性頁**] 對話方塊。

   - 若要設定 **/we**選項，請選取 [將**特定警告視為錯誤**] 屬性下拉式清單控制項，然後選擇 [**編輯**]。 在 [將**特定警告視為錯誤**] 對話方塊的 [編輯] 方塊中，輸入警告編號。 若要輸入一個以上的警告，請使用分號（ **;** ）來分隔這些值。 例如，若要將 C4001 和 C4010 視為錯誤，請輸入**4001; 4010**。 選擇 **[確定]** 儲存您的變更，並返回 [**屬性頁**] 對話方塊。

1. 若要設定 **/wo**選項，請 > [ **C/C++**  > **命令列**] 屬性頁中選取 [設定**屬性**]。 在 [**其他選項**] 方塊中，輸入編譯器選項。

1. 選取 [確定] 儲存您的變更。

### <a name="to-set-the-compiler-option-programmatically"></a>若要以程式設計方式設定編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>請參閱

[MSVC 編譯器選項](compiler-options.md)\
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)

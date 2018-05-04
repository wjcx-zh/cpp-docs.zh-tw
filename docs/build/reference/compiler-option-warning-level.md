---
title: -w、-W0，-W1、-W2，-W3、-W4，-w1，-w2，-w3，-w4，-牆上、-wd，-我們-wo-Wv，-WX （警告等級） |Microsoft 文件
ms.custom: ''
ms.date: 01/31/2018
ms.technology:
- cpp-tools
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60fc8072a95787f9e6f50e7e5c50408ef66e3261
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w、 /W0、 /W1、 /W2、 /W3、 /W4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd，/ /wo，我們 /Wv，/WX （警告等級）

指定編譯器如何對指定的編譯產生警告。

## <a name="syntax"></a>語法

> **/w**  
> **/W0**  
> **/W1**  
> **/W2**  
> **/W3**  
> **/W4**  
> **/Wall**  
> **/Wv**\[**:**_version_]  
> **/WX**  
> **/w1**_warning_  
> **/w2**_warning_  
> **/w3**_警告_  
> **/w4**_警告_  
> **/wd**_警告_  
> **/we**_警告_  
> **/wo**_警告_  

## <a name="remarks"></a>備註

警告選項指定要顯示與整個編譯警告行為的編譯器警告。

下表將描述警告選項和相關的引數：

|選項|描述|
------------|-----------------|
|**/w**|隱藏所有的編譯器警告。|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|指定要由編譯器產生的警告層級。 有效的警告層級的範圍從 0 到 4:<br />**/W0**會抑制所有警告。 這相當於 **/w**。<br />**/ W1**會顯示警告層級 1 （嚴重）。 **/ W1**是命令列編譯器中的預設設定。<br />**/W2**顯示層級 1 和 2 （重大） 的警告層級。<br />**/W3**顯示層級 1、 層級 2 和 3 （實際執行品質） 警告層級。 **/W3**是在 IDE 中的預設設定。<br />**/W4**顯示層級 1、 2、 層級和層級 3 警告，和所有層級 4 （資訊） 的警告不預設關閉的。 我們建議您使用此選項，以提供類似 lint 的警告。 對於新專案時，可能最好使用 **/W4**中所有編譯; 這樣可以確保可能難找到的程式碼缺失數最少。|
|**/Wall**|顯示所顯示的所有警告 **/W4**以及所有其他警告， **/W4**不包含 — 例如，預設為關閉的警告。 如需詳細資訊，請參閱[編譯器警告，是 Off By Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。|
|**/Wv**\[**:**_version_]|顯示編譯器版本中導入的警告*版本*及更早版本。 您可以使用此選項，隱藏程式碼中的新警告，當您移轉至更新版本的編譯器，以及維護您現有的建置程序時加以修正。 選擇性參數*版本*的形式*nn*[。*mm*[。*bbbbb*]] 其中*nn*是主要版本號碼，*公釐*是選用的次要版本號碼，和*bbbbb*是選擇性的組建編號編譯器。 例如，使用 */Wv:17*来顯示在 Visual Studio 2012 （也就是任何具有 17 主要版本號碼的編譯器版本） 或更早，導入的警告，但是 Visual Studio 2013 （主要版本中導入的警告18） 及更新版本。 根據預設， **/Wv**會使用目前的編譯器版本號碼和警告都會被隱藏。 了解哪種編譯器版本隱藏警告的資訊，請參閱[編譯器版本的編譯器警告](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md)。|
|**/WX**|將所有編譯器警告視為錯誤。 對於新專案時，可能最好使用 **/WX**中所有編譯; 解決所有警告可確保難找到可能的程式碼缺失數最少。<br /><br /> 連結器也有 **/WX**選項。 如需詳細資訊，請參閱 [/WX (將連結器警告視為錯誤)](../../build/reference/wx-treat-linker-warnings-as-errors.md)。|
|**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/w4**_nnnn_|設定指定的警告數字的警告層級_nnnn_。 這可讓您設定特定的警告層級時，變更該警告的編譯器行為。 您可以與其他警告選項搭配使用這些選項，強制執行您自己撰寫程式碼的警告，而不是預設的 Visual Studio 所提供的標準。<br /><br /> 例如， **/w34326**會使 C4326 必須產生做為層級 3 警告，而不是層級 1。 如果您使用同時編譯 **/w34326**選項和 **/W2**選項時，警告 C4326 不會產生。|
|**/wd**_nnnn_|隱藏所指定的編譯器警告_nnnn_。<br /><br /> 例如， **/wd4326 會**會隱藏編譯器警告 C4326。|
|**/we**_nnnn_|將所指定的編譯器警告_nnnn_視為錯誤。<br /><br /> 例如， **/we4326**導致 C4326 視為編譯器錯誤的警告編號。|
|**/wo**_nnnn_|編譯器警告也就指定的報表_nnnn_一次。<br /><br /> 例如， **/wo4326**警告 C4326 只報告的原因，第一次時發現編譯器。|

如果您的任何警告的選項建立時使用先行編譯標頭使用[/Yc](../../build/reference/yc-create-precompiled-header-file.md)選項，使用先行編譯標頭使用的任何[/Yu](../../build/reference/yu-use-precompiled-header-file.md)選項會使這些相同的警告選項才會生效一次。 您可以覆寫使用命令列上的另一個警告選項在先行編譯標頭中設定的警告選項。

您可以使用[#pragma 警告](../../preprocessor/warning.md)指示詞，以控制層級的警告，在編譯時期報告特定的原始程式檔中。

在原始程式碼中的警告 pragma 指示詞不會受到 **/w**選項。

[建置錯誤文件](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)描述警告和警告層級，並指出為何某些陳述式可能無法進行編譯依照您的需求。

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 若要設定 **/W0**， **/W1**， **/W2**， **/W3**， **/W4**， **/wall**m **/Wv**， **/WX**或 **/WX-** 選項中，選取**組態屬性** > **C /C + +** > **一般**屬性頁。

   - 若要設定 **/W0**， **/W1**， **/W2**， **/W3**， **/W4**，或 **/wall**選項，修改**警告層級**屬性。

   - 若要設定 **/WX**或 **/WX-** 選項，修改**警告視為錯誤**屬性。

   - 若要設定的版本 **/Wv**選項，請輸入中的編譯器版本號碼**警告版本**屬性。

1. 若要設定 **/wd**或 **/we**選項中，選取**組態屬性** > **C/c + +**  >  **進階**屬性頁。

   - 若要設定 **/wd**選項中，選取**停用特定警告**屬性下拉式清單控制項，然後選擇 **編輯**。 在編輯方塊中**停用特定警告** 對話方塊中，輸入警告數字。 若要輸入多個警告，請使用分號分隔值 (**;**)。 例如，若要停用 C4001 和 C4010，輸入**4001; 4010**。 選擇**確定**以儲存變更並返回**屬性頁**對話方塊。

   - 若要設定 **/we**選項，選取**特定警告視為錯誤**屬性下拉式清單控制項，然後選擇 **編輯**。 在編輯方塊中**特定警告視為錯誤** 對話方塊中，輸入警告數字。 若要輸入多個警告，請使用分號分隔值 (**;**)。 例如，若要 C4001 和 C4010 視為錯誤，請輸入**4001; 4010**。 選擇**確定**以儲存變更並返回**屬性頁**對話方塊。

1. 若要設定 **/wo**選項中，選取**組態屬性** > **C/c + +** > **命令列**屬性頁。 輸入中的編譯器選項**其他選項**方塊。

1. 選擇**確定**以儲存變更。

### <a name="to-set-the-compiler-option-programmatically"></a>若要以程式設計方式設定編譯器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)  
[設定編譯器選項](../../build/reference/setting-compiler-options.md)  

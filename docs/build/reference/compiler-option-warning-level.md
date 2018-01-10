---
title: "-w、-W0，-W1、-W2，-W3、-W4，-w1，-w2，-w3，-w4，-牆上、-wd，-我們-wo-Wv，-WX （警告等級） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
ms.assetid: d6bc7bf5-c754-4879-909c-8e3a67e2629f
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4f38328f94fd68b3b5402d08ddb6d2bd97e3de76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w、 /W0、 /W1、 /W2、 /W3、 /W4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd，/ /wo，我們 /Wv，/WX （警告等級）
指定編譯器如何對指定的編譯產生警告。  
  
## <a name="syntax"></a>語法  
  
```  
/w  
/W0  
/W1  
/W2  
/W3  
/W4  
/Wall  
/Wv[<version>]  
/WX  
/w1<warning>   
/w2<warning>   
/w3<warning>   
/w4<warning>   
/wd<warning>   
/we<warning>   
/wo<warning>  
```  
  
## <a name="remarks"></a>備註  
 警告選項指定要顯示與整個編譯警告行為的編譯器警告。  
  
 下表將描述警告選項和相關的引數：  
  
|選項|描述|  
|------------|-----------------|  
|**/w**|隱藏所有的編譯器警告。|  
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|指定要由編譯器產生的警告層級。 有效的警告層級的範圍從 0 到 4:<br /><br /> -   **/W0**會抑制所有警告。<br />-   **/ W1**會顯示警告層級 1 （嚴重）。 **/ W1**是預設值。<br />-   **/W2**顯示層級 1 和 2 （重大） 的警告層級。<br />-   **/W3**顯示層級 1、 層級 2 和 3 （實際執行品質） 警告層級。<br />-   **/W4**顯示層級 1、 2、 層級和層級 3 警告，和所有層級 4 （資訊） 的警告不預設關閉的。 建議只有當您想要提供類似 lint 的警告時，才使用這個選項。 不過，對於新專案時，可能最好使用**/W4**中所有編譯; 這樣可以確保可能難找到的程式碼缺失數最少。|  
|**/Wall**|顯示所顯示的所有警告**/W4**以及所有其他警告， **/W4**不包含 — 例如，預設為關閉的警告。 如需詳細資訊，請參閱[編譯器警告，是 Off By Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。|  
|**/Wv**`:version`|隱藏警告的編譯器版本比更新版本中導入`version`。 您可以使用此選項，以判斷是否有新的警告時使用較舊版本的編譯器編譯警告的程式碼中，並暫時隱藏新的警告，從您的建置流程時加以修正。 選擇性參數`version`的形式`nn`[。`mm`[.`bbbbb`]] 其中`nn`是主要版本號碼，`mm`是選用的次要版本號碼，和`bbbbb`是選擇性的組建編號的編譯器。 例如，使用`/Wv:17.00.00000`来隱藏在 Visual c + + 2012年和更新版本導入的警告。 根據預設， **/Wv**會使用目前的編譯器版本號碼和警告都會被隱藏。 了解哪種編譯器版本隱藏警告的資訊，請參閱[編譯器版本的編譯器警告](../..//error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md)。|  
|**/WX**|將所有編譯器警告視為錯誤。 對於新專案時，可能最好使用**/WX**中所有編譯; 解決所有警告可確保難找到可能的程式碼缺失數最少。<br /><br /> 連結器也有**/WX**選項。 如需詳細資訊，請參閱 [/WX (將連結器警告視為錯誤)](../../build/reference/wx-treat-linker-warnings-as-errors.md)。|  
|**/w1**`n`<br /><br /> **/w2**`n`<br /><br /> **/w3**`n`<br /><br /> **/w4**`n`|設定指定的警告數字的警告層級`n`。 這可讓您設定特定的警告層級時，變更該警告的編譯器行為。 您可以與其他警告選項搭配使用這些選項，強制執行您自己撰寫程式碼的警告，而不是預設的 Visual Studio 所提供的標準。<br /><br /> 例如，`/w34326`會使 C4326 必須產生做為層級 3 警告，而不是層級 1。 如果您使用同時編譯`/w34326`選項和`/W2`選項時，警告 C4326 不會產生。|  
|**/wd**`n`|隱藏所指定的編譯器警告`n`。<br /><br /> 例如，`/wd4326`會隱藏編譯器警告 C4326。|  
|**/we**`n`|將所指定的編譯器警告`n`視為錯誤。<br /><br /> 例如，`/we4326`導致 C4326 視為編譯器錯誤的警告編號。|  
|**/wo**`n`|編譯器警告也就指定的報表`n`一次。<br /><br /> 例如，`/wo4326`警告 C4326 只報告的原因，第一次時發現編譯器。|  
  
 如果您的任何警告的選項建立時使用先行編譯標頭使用[/Yc](../../build/reference/yc-create-precompiled-header-file.md)選項，使用先行編譯標頭使用的任何[/Yu](../../build/reference/yu-use-precompiled-header-file.md)選項會使這些相同的警告選項才會生效一次。 您可以覆寫使用命令列上的另一個警告選項在先行編譯標頭中設定的警告選項。  
  
 您可以使用[#pragma 警告](../../preprocessor/warning.md)指示詞，以控制層級的警告，在編譯時期報告特定的原始程式檔中。  
  
 在原始程式碼中的 Pragma 警告指示詞不會受到**/w**選項。  
  
 [建置錯誤文件](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)描述警告和警告層級，並指出為何某些陳述式可能無法進行編譯依照您的需求。  
  
### <a name="to-set-the-compiler-option-in-the-visual-studio-development-environment"></a>若要在 Visual Studio 開發環境中設定編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +**。  
  
3.  在**一般**屬性頁面上，修改**警告層級**或**警告視為錯誤**屬性。  
  
4.  在**進階**屬性頁面上，修改**停用特定警告**屬性。  
  
5.  剩餘的選項，在**命令列**屬性頁面上，輸入中的編譯器選項**其他選項**方塊。  
  
### <a name="to-set-the-compiler-option-programmatically"></a>若要以程式設計方式設定編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A>和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)
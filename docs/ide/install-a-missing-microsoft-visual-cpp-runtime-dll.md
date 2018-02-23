---
title: "安裝遺漏 Microsoft Visual c + + 執行階段 DLL |Microsoft 文件"
description: "如何尋找並安裝遺漏的 Visual c + + 執行階段 Dll。"
ms.date: 08/30/2017
ms.topic: article
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d40e1594b2190d4bbfd2fe52fddaad04af527573
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2018
---
# <a name="install-a-missing-microsoft-visual-c-runtime-dll"></a>安裝遺漏 Microsoft Visual c + + 執行階段 DLL

通常使用 Microsoft Visual c + + 撰寫的程式需要一些其他的 Visual c + + 執行階段程式庫檔案或要執行的 Dll。 這些執行階段 Dll 位於*可轉散發套件*，程式庫檔案安裝程式，每個版本的 Visual c + +。 應由它的安裝程式包含的任何程式所需的可轉散發套件。 如果不是，有時您可以自行安裝可轉散發套件並修正系統錯誤，當您執行程式。 

您可以告訴程式遺漏 Visual c + + 執行階段 DLL，是否您啟動程式，指出項目時，取得系統錯誤 」 程式無法啟動，因為您的電腦從 vcruntime140.dll、 遺漏"一樣。 通常，解除安裝程式，然後再重新安裝，可以解決此問題。 我們強烈建議先，嘗試此步驟之前，任何其他可能的修正方法。

有時候安裝程式的可轉散發套件已過期。 Microsoft 提供更新的版本的執行階段 Dll 不時，給位址 bug 和安全性問題。 為了讓您執行安全且正確的電腦，最好使用 DLL 的任何執行階段的最新的更新。 請檢查是否有可用更新的安裝程式為您的程式，可能會為您提供這項更新。 如果沒有，然後使用更新的安裝程式重新安裝您的程式。

如果重新安裝程式不會進行消失的系統錯誤，然後程式的安裝程式可能已中斷，或已損毀，或您的電腦上的執行階段 Dll 可能會損毀。 嘗試下載一份新的安裝程式為您的程式，並使用它來重新安裝第一個。 如果無法解決問題，或安裝程式無法使用，則它可能值得檢查您的電腦上的 Microsoft Visual c + + 可轉散發套件安裝。 

下表顯示一或多個可轉散發套件，以及下載一份可轉散發套件的連結中包含的 Dll 的清單。 下載可轉散發套件的新複本之前，您應該會看到是否您可以修復現有安裝。

|遺失的 DLL  |可轉散發套件  |
|---------|---------|
|atl80.dll<br />msvcm80.dll<br />msvcp80.dll<br />msvcr80.dll<br />mfc80.dll<br />mfc80u.dll<br />mfcm80.dll<br />mfcm80u.dll|[Microsoft Visual c + + 2005 可轉散發套件 (x86)](https://www.microsoft.com/en-us/download/details.aspx?id=5638)<br />[Microsoft Visual c + + 2005年可轉散發套件 (x64)](https://www.microsoft.com/en-us/download/details.aspx?id=18471)<br />[Microsoft Visual c + + 2005 Service Pack 1 可轉散發套件 MFC 安全性更新](https://www.microsoft.com/en-us/download/details.aspx?id=26347)|
|atl90.dll<br />msvcr90.dll<br />msvcm90.dll<br />msvcp90.dll<br />mfc90.dll<br />mfc90u.dll<br />mfcmifc80.dll<br />mfcm90.dll<br />mfcm90u.dll|[Microsoft Visual c + + 2008 可轉散發套件-x86](https://www.microsoft.com/en-us/download/details.aspx?id=5582)<br />[Microsoft Visual c + + 2008 可轉散發套件的 x64](https://www.microsoft.com/en-us/download/details.aspx?id=2092)<br />[Microsoft Visual c + + 2008 Service Pack 1 可轉散發套件 MFC 安全性更新](https://www.microsoft.com/en-us/download/details.aspx?id=26368)|
|atl100.dll<br />msvcr100.dll<br />msvcp100.dll<br />msdia71.dll<br />vcomp100.dll<br />mfc100.dll<br />mfc100u.dll<br />mfcmifc80.dll<br />mfcm100.dll<br />mfcm100u.dll|[Microsoft Visual c + + 2010 x86 可轉散發套件](https://www.microsoft.com/en-us/download/details.aspx?id=8328)<br />[Microsoft Visual c + + 2010 x64 可轉散發套件](https://www.microsoft.com/en-us/download/details.aspx?id=13523)<br />[Microsoft Visual c + + 2010 Service Pack 1 可轉散發套件 MFC 安全性更新](https://www.microsoft.com/en-us/download/details.aspx?id=26999)|
|atl110.dll<br />msvcr110.dll<br />msvcp110.dll<br />mfc110.dll<br />mfc110u.dll<br />mfcmifc80.dll<br />mfcm110.dll<br />mfcm110u.dll<br />concrt110.dll<br />vccorlib110.dll<br />vcamp110.dll<br />vcomp110.dll|[Microsoft Visual c + + 2012 可轉散發套件 （適用於 Visual Studio 2012 Update 4)](https://www.microsoft.com/en-us/download/details.aspx?id=30679)|
|msvcr120.dll<br />msvcp120.dll<br />mfc120.dll<br />mfc120u.dll<br />mfcmifc80.dll<br />mfcm120.dll<br />mfcm120u.dll<br />concrt120.dll<br />vccorlib120.dll<br />vcamp120.dll<br />vcomp120.dll|[Microsoft Visual c + + 2013年可轉散發套件 （個別下載連結）](https://support.microsoft.com/en-us/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package)<br />[Visual Studio 2013 的多位元組的 MFC 程式庫](https://www.microsoft.com/en-us/download/details.aspx?id=40770)<br />[Visual c + + 2013 Runtime 側載 Windows 8.1 應用程式 （.zip 下載）](http://download.microsoft.com/download/5/F/0/5F0F8404-9329-44A9-8176-ED6F7F746F25/VCLibs_Redist_Packages.zip)|
|vcruntime140.dll<br />vcruntime140_app.dll<br />msvcp140.dll<br />mfc140.dll<br />mfc140u.dll<br />mfcmifc80.dll<br />mfcm140.dll<br />mfcm140u.dll<br />concrt140.dll<br />vccorlib140.dll<br />vcamp140.dll<br />vcomp140.dll|[Microsoft Visual c + + 2017 (x86) 可轉散發套件](https://go.microsoft.com/fwlink/?LinkId=746571)<br />[Microsoft Visual c + + 2017 (x64) 可轉散發套件](https://go.microsoft.com/fwlink/?LinkId=746572)|
|msvcr100_clr0400.dll<br />msvcr110_clr0400.dll<br />msvcr120_clr0400.dll|[下載 .NET Framework](https://www.microsoft.com/net/download/framework)|

### <a name="to-repair-an-existing-redistributable-package"></a>若要修復現有的可轉散發套件

1. 開啟 [控制台]。 在 Windows 10 中，輸入*控制台*桌面工作列上搜尋控制項，然後選擇 **控制台**從提供的選項。

2. 在 [控制台] 中選擇**程式** > **程式和功能**。 選取 Microsoft Visual c + + 可轉散發套件對應至遺漏的 DLL 的版本。 如果**變更**按鈕會出現在清單頂端，選擇它。 如果是唯一的選擇**解除安裝**，您無法修復這個版本的可轉散發套件。

3. 選擇**修復**可轉散發套件的安裝程式 對話方塊中。 您可能需要重新啟動時修復已完成。 
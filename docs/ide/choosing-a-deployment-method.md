---
title: "選擇部署方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- redistributing DLLs
- manifests [C++]
- DLLs [C++], redistributing
- side-by-side assemblies [C++]
- dynamic linking [C++]
- application deployment [C++], methods
- deploying applications [C++], methods
- static linking [C++]
- libraries [C++], application deployment issues
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
caps.latest.revision: "35"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c444b3319c60b80bdfdc14000a41d65869d0514
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="choosing-a-deployment-method"></a>選擇部署方法
除非您的 Visual c + + 應用程式是獨立的而且可以使用複製命令來部署，否則我們建議您部署使用 Windows Installer。 Windows Installer 支援安裝、修復或解除安裝，同時也支援不可部分完成更新應用程式檔案、相依性和登錄項目。  
  
> [!NOTE]
>  雖然[ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) ，就可以在 Visual Studio 中 Visual c + + 原生應用程式的部署，這需要額外的步驟。 如需詳細資訊，請參閱 [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md)。  
  
## <a name="visual-c-libraries-are-shared-dlls"></a>Visual C++ 程式庫是共用 DLL  
 由於 Visual Studio 安裝程式會將 Visual C++ 程式庫安裝在 %windir%\system32\ 目錄中，當您開發與這些程式庫相依的 Visual C++ 應用程式時，該應用程式會如預期執行。 不過，若要在可能沒有安裝 Visual Studio 的電腦上部署該應用程式，建議您先確定已將程式庫和應用程式一併安裝在那些電腦中。  
  
## <a name="redistributing-visual-c-libraries"></a>轉散發 Visual C++ 程式庫  
 在您的部署中，您可以轉散發具有轉散發授權的任何 Visual C++ 程式庫版本。 部署方法有三種：  
  
-   使用集中部署時可轉散發套件，可安裝 Visual c + + 程式庫共用的 Dll 在 %windir%\system32 中為\\。 (必須要有系統管理員權限才能安裝至此資料夾)。在目標電腦上安裝應用程式之前，您可以建立會執行可轉散發套件的指令碼或安裝程式。 可轉散發套件適用於 x86、x64 和 ARM 平台 (VCRedist_x86.exe、VCRedist_x64.exe 或 VCRedist_arm.exe)。 Visual Studio 將這些套件包含在 Visual Studio 的 %programfiles (x86) %\Microsoft `version`\VC\Redist\\`locale ID`\\。 您也可以下載從[Microsoft Download Center](http://go.microsoft.com/fwlink/p/?linkid=132793)。 (在 [下載中心] 上搜尋 「 Visual c + + 可轉散發套件*Visual Studio 版本及更新*"符合您的應用程式。 例如，若您使用 Visual Studio 2012 Update 4 建置應用程式，請搜尋「Visual C++ 可轉散發套件 2012 Update 4」)。如需如何使用可轉散發套件的資訊，請參閱[逐步解說： 部署 Visual c + + 應用程式所使用 Visual c + + 可轉散發套件](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
-   集中部署時使用合併模組，其中每個安裝特定的 Visual c + + 程式庫做為共用的 DLL 在 %windir%\system32\\。 (必須要有系統管理員權限才能安裝至此資料夾)。合併模組會變成應用程式 .msi 安裝程式檔案的一部分。 Visual c + + 可轉散發合併模組包含在 Visual Studio 的 \Program Files (x86) \common 模組\\。 如需詳細資訊，請參閱[所使用合併模組轉散發](../ide/redistributing-components-by-using-merge-modules.md)。  
  
-   本機部署，您將特定的 Visual c + + Dll 複製從 Visual Studio 安裝，通常位於 \Program Files (x86) \Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\—and安裝這些應用程式執行檔相同資料夾中的目標電腦上。 您可以使用此部署方法讓不具系統管理員權限的使用者進行安裝，也可以用於安裝可透過網路共用執行的應用程式。  
  
 如果部署使用可轉散發合併模組，安裝由不具有系統管理權限的使用者執行未安裝 Visual c + + Dll 和應用程式將不會執行。 此外，以合併模組建置 (允許個別使用者安裝) 的應用程式安裝程式會將程式庫安裝在共用位置，此位置會影響系統的所有使用者。 您可以使用本機部署安裝特定使用者的應用程式的目錄中的所需的 Visual c + + Dll，而不會影響其他使用者或要求系統管理員權限。 因為這可能會產生服務性問題，我們不建議本機部署 Visual c + + 可轉散發 Dll。  
  
 不正確的 Visual C++ 程式庫部署方式可能會在執行相依的應用程式時發生執行階段錯誤。 當作業系統載入應用程式時，它會使用所述的搜尋順序[LoadLibraryEx](http://go.microsoft.com/fwlink/p/?linkid=132792)  
  
## <a name="dynamic-linking-is-better-than-static-linking"></a>動態連結比靜態連結適合  
 我們建議您避免轉散發 Visual c + + 程式庫時使用靜態連結。 靜態連結幾乎無法大幅改善應用程式效能，卻會提高服務代價。 例如，請考慮靜態連結至已更新安全性增強之程式庫的應用程式，除非重新編譯並重新部署，否則該應用程式不會因此受益。 相反地，我們建議您將應用程式動態連結至相依的程式庫，以便在部署時更新這些程式庫。  
  
## <a name="see-also"></a>請參閱  
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [不在組建中： 選擇部署策略](http://msdn.microsoft.com/en-us/ecd632d8-063c-4028-b785-81bba045107b)   
 [Windows Installer 部署概觀](http://msdn.microsoft.com/en-us/3ce4610a-b54f-404e-b650-42f4a55dfc3b)   
 [ClickOnce 安全性和部署](/visualstudio/deployment/clickonce-security-and-deployment)   
 [部署範例](../ide/deployment-examples.md)
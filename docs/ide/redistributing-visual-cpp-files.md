---
title: "轉散發 Visual c + + 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 45035847befc08f667c95238ede0604651c7e9b6
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="redistributing-visual-c-files"></a>轉散發 Visual C++ 檔案

> [!NOTE]
> 會在您此處因為您所需的其中一個 Visual c + + 執行階段檔案的下載？ 移至[Microsoft](http://www.microsoft.com/)網站，並輸入**Visual c + + 可轉散發**[搜尋] 方塊中。 下載並安裝您的電腦 (例如，x64 如果您執行 Windows 64 位元) 的架構和 Visual c + + （例如，2015年），您需要的版本的可轉散發套件。

當您部署應用程式時，您也必須部署必要的支援檔案。 如果其中有任何檔案是由 Microsoft 提供，請檢查您否有權限轉散發。 若要檢視 Visual Studio 授權條款，請參閱在 ide 中的 [關於 Microsoft Visual Studio] 對話方塊中的 [授權條款] 連結，或下載[Microsoft 軟體授權條款](http://go.microsoft.com/fwlink/p/?LinkId=831114)檔案。 若要檢視的 「 可轉散發清單 」 特定版本的 Visual Studio 的 Microsoft 軟體授權條款 < 可散發程式碼 > 一節中所參考，請參閱[Microsoft Visual Studio 2017 和 Microsoft Visual Studio 2017 的可散發程式碼SDK （包含公用程式與 BuildServer 檔案）](http://go.microsoft.com/fwlink/p/?LinkId=823098)，或適用於 Visual Studio 2015，請參閱[Microsoft Visual Studio 2015 和 Microsoft Visual Studio 2015 SDK 可散發程式碼](http://go.microsoft.com/fwlink/p/?LinkId=523763)。 如需可轉散發檔案的詳細資訊，請參閱[判斷要轉散發哪些 Dll](../ide/determining-which-dlls-to-redistribute.md)和[部署範例](../ide/deployment-examples.md)。

若要部署可轉散發 Visual c + + 檔案，您可以使用 Visual c + + 可轉散發套件 (VCRedist\_x86.exe，VCRedist\_x64.exe 或 VCRedist\_arm.exe) 包含在 Visual Studio。 在 Visual Studio 2017，這些檔案位於 Program Files [(x86)]\\Microsoft Visual Studio\\2017年\\_edition_\\VC\\可轉散發套件\\MSVC\\_lib 版本_資料夾，其中_edition_是安裝，Visual Studio 版本和_lib 版本_的版本轉散發程式庫。 在 Visual Studio 2015 中，這些檔案位於您的 Visual Studio 安裝目錄下 Program Files [(x86)] \Microsoft Visual Studio*版本*\VC\redist\\*地區設定*\\. 另一個選項是使用可轉散發合併模組 （.msm 檔案） 位於 Program Files [(x86)]; 在 Visual Studio 2017\\Microsoft Visual Studio\\2017年\\_edition_ \\VC\\可轉散發套件\\MSVC\\_lib 版本_\\MergeModules\\資料夾。 Visual Studio 2015 中可以找到這些位於 Program Files [(x86)] \common 模組\\。 也可以直接安裝中的可轉散發 Visual c + + Dll*應用程式本機資料夾*，這是包含可執行應用程式檔案的資料夾。 對於維護原因，建議您不要使用此安裝位置。

Visual C++ 可轉散發套件會安裝並註冊所有 Visual C++ 程式庫。 如果使用可轉散發套件，您必須在目標系統上執行該套件並設定為安裝應用程式的必要條件。 建議您使用這些套件進行部署，以便自動更新 Visual C++ 程式庫。 如需如何使用這些封裝的範例，請參閱[逐步解說： 部署 Visual c + + 應用程式所使用 Visual c + + 可轉散發套件](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。

每個「Visual C++ 可轉散發套件」都會檢查電腦上是否有較新的版本存在。 若發現較新的版本，則不會安裝該套件。 從 Visual Studio 2015 開始，可轉散發套件會顯示錯誤訊息，說明安裝程式失敗。 如果使用執行封裝**/quiet/**旗標，任何錯誤訊息會顯示。 不論是哪一種情況，Microsoft 安裝程式都會記錄錯誤，而且錯誤結果會被傳回給呼叫者。 從 Visual Studio 2015 套件開始，可以避免這個錯誤，藉由檢查登錄，以了解是否已安裝較新版本。 目前安裝的版本會儲存在 HKEY_LOCAL_MACHINE\SOFTWARE [\Wow6432Node] \Microsoft\VisualStudio\\_vs 版本_\VC\Runtimes\\{x86 | x64 |ARM} 索引鍵，其中_vs 版本_版本號碼為 Visual Studio (14.0 Visual Studio 2015 和 Visual Studio 2017，因為已更新的 2017 可轉散發套件 2015年版本相容的二進位檔)，以及金鑰的位置ARM、 x86 或 x64 視平台的已安裝的 vcredist 版本而定。 (您不需要檢查 Wow6432Node 子機碼下，除非您用來檢視已安裝 x86 版本 RegEdit 封裝在 x64 平台。)REG_SZ 字串值中儲存的版本號碼**版本**，也可以在一組**主要**，**次要**， **Bld**，和**Rbld** REG_DWORD 值。 若要避免在安裝時的錯誤，您必須略過的可轉散發套件的安裝目前已安裝的版本較新時。

如果您使用的合併模組包含 Visual C++ DLL
，則必須將它包含在您用來部署應用程式的 Windows Installer 套件 (或類似的安裝套件) 中。 如需詳細資訊，請參閱[所使用合併模組轉散發](../ide/redistributing-components-by-using-merge-modules.md)。 如需範例，請參閱[逐步解說： 部署 Visual c + + 應用程式所使用之安裝專案](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)，其中也會說明如何使用 InstallShield Limited Edition 建立安裝套件。

## <a name="potential-run-time-errors"></a>可能的執行階段錯誤

如果 Windows 找不到您的應用程式所需的 Dll 的可轉散發程式庫，則可能會顯示類似下面的訊息: 「 此應用程式無法啟動，因為*文件庫*找不到.dll。 重新安裝應用程式可能可以解決這個問題。 」

若要解決這種錯誤，請確定您的應用程式安裝程式建置正確，且在目標系統上已正確部署的可轉散發程式庫。 如需詳細資訊，請參閱[了解 Visual c + + 應用程式的相依性](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[使用合併模組轉散發](../ide/redistributing-components-by-using-merge-modules.md)|描述如何使用 Visual c + + 可轉散發合併模組，以 Visual c + + 執行階段程式庫安裝在 %windir%\system32\ 資料夾中的共用 Dll。|
|[轉散發 Visual C++ ActiveX 控制項](../ide/redistributing-visual-cpp-activex-controls.md)|描述如何轉散發使用了 ActiveX 控制項的應用程式。|
|[轉散發資料庫支援檔案](../ide/redistributing-database-support-files.md)|討論如何轉散發資料存取物件 (DAO) 的支援檔案，以及 Microsoft Data Access SDK 中的資料庫技術。|
|[轉散發 MFC 程式庫](../ide/redistributing-the-mfc-library.md)|描述如何轉散發使用了 MFC 的應用程式。|
|[轉散發 ATL 應用程式](../ide/redistributing-an-atl-application.md)|描述如何轉散發使用 ATL 的應用程式。 從 Visual Studio 2012 開始，就不需要適用於 aLT 的轉散發程式庫。|
|[部署範例](../ide/deployment-examples.md)|示範如何部署 Visual C++ 應用程式的範例連結。|
|[部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)|介紹 Visual C++ 部署概念和技術。|
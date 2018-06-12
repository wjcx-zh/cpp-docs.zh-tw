---
title: 使用可轉散發套件部署應用程式 (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37bba00efdf0368973fa4ffbac1cbc6bb6298ce1
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339150"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>逐步解說：使用 Visual C++ 可轉散發套件部署 Visual C++ 應用程式
本文將逐步描述如何使用 Visual C++ 可轉散發套件來部署 Visual C++ 應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 您必須具有下列元件才能完成本逐步解說：  
  
-   已安裝 Visual Studio 的電腦。  
  
-   沒有 Visual C++ 程式庫的另一部電腦。  
  
### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>使用 Visual C++ 可轉散發套件部署應用程式  
  
1.  遵循[逐步解說：使用安裝專案部署 Visual C++ 應用程式](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)中的前三個步驟，建立及建置 MFC 應用程式。  
  
2.  建立檔案並將它命名為 setup.bat，然後將下列命令新增至該檔案。 將 `MyMFCApplication` 變更為您專案的名稱。  
  
    ```cmd
    @echo off  
    vcredist_x86.exe  
    mkdir "C:\Program Files\MyMFCApplication"  
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"  
    ```  
  
3.  建立自我解壓縮安裝檔：  
  
    1.  在命令提示字元或 [執行] 視窗中，執行 iexpress.exe。  
  
    2.  選取 [Create new Self Extraction Directive file] \(建立新的自我解壓縮指示詞檔案\)，然後選擇 [下一步] 按鈕。  
  
    3.  選取 [Extract files and run an installation command] \(解壓縮檔案並執行安裝命令\)，然後選擇 [下一步]。  
  
    4.  在文字方塊中，輸入您 MFC 應用程式的名稱，然後選擇 [下一步]。  
  
    5.  在 [Confirmation prompt] \(確認提示\) 頁面上，選取 [No Prompt] \(不提示\)，然後選擇 [下一步]。  
  
    6.  在 [授權合約] 頁面上，選取 [Do not display a license] \(不顯示授權\)，然後選擇 [下一步]。  
  
    7.  在 [Packaged files] \(封裝檔案\) 頁面上，新增下列檔案，然後選擇 [下一步]。  
  
        -   您的 MFC 應用程式 (.exe 檔案)。  
  
        -   vcredist_x86.exe。 此檔案位於 \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\vcredist_x86\\ 中。  
  
        -   您在前面步驟中建立的 setup.bat 檔案。  
  
    8.  在 [Install Program to Launch] \(要啟動的安裝程式\) 頁面的 [Install Program] \(安裝程式\) 文字方塊中，輸入下列命令列，然後選擇 [下一步]。  
  
         **cmd.exe /c "setup.bat"**  
  
    9. 在 [顯示視窗] 頁面上，選取 [預設]，然後選擇 [下一步]。  
  
    10. 在 [Finished message] \(已完成訊息\) 頁面上，選取 [沒有訊息]，然後選擇 [下一步]。  
  
    11. 在 [Package Name and Options] \(封裝名稱和選項\) 頁面上，輸入您自我解壓縮安裝檔的名稱，選取 [Store files using Long File Name inside Package] \(將使用長檔名的檔案儲存在套件內\) 選項，然後選擇 [下一步]. 檔案名稱的結尾必須是 Setup.exe，例如 MyMFCApplicationSetup.exe。  
  
    12. 在 [Configure restart] \(設定重新啟動\) 頁面上，選取 [不要重新啟動]，然後選擇 [下一步]。  
  
    13. 在 [Save Self Extraction Directive] \(儲存自我解壓縮指示詞\) 頁面上，選取 [Save Self Extraction Directive (SED) file] \(儲存自我解壓縮指示詞 (SED) 檔案\)，然後選擇 [下一步]。  
  
    14. 在 [建立封裝] 頁面上，選擇 [下一步]。  
  
4.  在沒有 Visual C++ 程式庫的另一部電腦上測試自我解壓縮安裝檔：  
  
    1.  在另一部電腦上，下載安裝檔的複本，然後執行複本並遵循其所提供的步驟加以安裝。  
  
    2.  執行 MFC 應用程式。  
  
         自我解壓縮安裝檔會安裝您在步驟 2 中指定之資料夾中的 MFC 應用程式。 由於自我解壓縮安裝檔中隨附 Visual C++ 可轉散發套件安裝程式，因此應用程式會成功執行。  
  
        > [!IMPORTANT]
        >  為了判斷所安裝的執行階段版本，安裝程式會檢查登錄機碼 \HKLM\SOFTWARE\Microsoft\VisualStudio\11.0\VC\Runtimes\\[平台]。 如果目前安裝的版本比安裝程式嘗試安裝的版本還要新，則安裝程式會傳回成功而不安裝較舊版本，並在 [控制台] 的已安裝程式頁面上保留另一個項目。  
  
## <a name="see-also"></a>請參閱  
 [部署範例](../ide/deployment-examples.md)
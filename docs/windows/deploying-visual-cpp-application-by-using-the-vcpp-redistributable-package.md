---
title: 使用可轉散發套件部署應用程式 (C++)
ms.date: 09/17/2018
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
ms.openlocfilehash: ccf6b74096894c2e48258e6e0a60b807c7c6c5b4
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786230"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>逐步解說：使用 Visual C++ 可轉散發套件來部署 Visual C++ 應用程式

本文將逐步描述如何使用 Visual C++ 可轉散發套件來部署 Visual C++ 應用程式。

## <a name="prerequisites"></a>必要條件

您必須具有下列元件才能完成本逐步解說：

- 已安裝 Visual Studio 的電腦。

- 沒有 Visual C++ 程式庫的另一部電腦。

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>使用 Visual C++ 可轉散發套件部署應用程式

1.  藉由遵循[逐步解說：使用安裝專案部署 Visual C++ 應用程式](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)中的步驟來建立及建置 MFC 應用程式：。

1. 建立檔案並將它命名為 setup.bat，然後將下列命令新增至該檔案。 將 `MyMFCApplication` 變更為您專案的名稱。

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

1. 建立自我解壓縮安裝檔：

   1. 在命令提示字元或 [執行] 視窗中，執行 iexpress.exe。

   1. 選取 [Create new Self Extraction Directive file] \(建立新的自我解壓縮指示詞檔案\)，然後選擇 [下一步] 按鈕。

   1. 選取 [Extract files and run an installation command] \(解壓縮檔案並執行安裝命令\)，然後選擇 [下一步]。

   1. 在文字方塊中，輸入您 MFC 應用程式的名稱，然後選擇 [下一步]。

   1. 在 [Confirmation prompt] \(確認提示\) 頁面上，選取 [No Prompt] \(不提示\)，然後選擇 [下一步]。

   1. 在 [授權合約] 頁面上，選取 [Do not display a license] \(不顯示授權\)，然後選擇 [下一步]。

   1. 在 [Packaged files] \(封裝檔案\) 頁面上，新增下列檔案，然後選擇 [下一步]。

      - 您的 MFC 應用程式 (.exe 檔案)。

      - vcredist_x86.exe。 此檔案位於 \Program Files (x86)\Microsoft Visual Studio \<version>\SDK\Bootstrapper\Packages\. 您也可以從 [Microsoft](https://www.microsoft.com/download/confirmation.aspx?id=5555) 下載此檔案。

      - 您在前面步驟中建立的 setup.bat 檔案。

   1. 在 [Install Program to Launch] \(要啟動的安裝程式\) 頁面的 [Install Program] \(安裝程式\) 文字方塊中，輸入下列命令列，然後選擇 [下一步]。

      **cmd.exe /c "setup.bat"**

   1. 在 [顯示視窗] 頁面上，選取 [預設]，然後選擇 [下一步]。

   1. 在 [Finished message] \(已完成訊息\) 頁面上，選取 [沒有訊息]，然後選擇 [下一步]。

   1. 在 [Package Name and Options] \(封裝名稱和選項\) 頁面上，輸入您自我解壓縮安裝檔的名稱，選取 [Store files using Long File Name inside Package] \(將使用長檔名的檔案儲存在套件內\) 選項，然後選擇 [下一步]. 檔案名稱的結尾必須是 Setup.exe，例如 *MyMFCApplicationSetup.exe*。

   1. 在 [Configure restart] \(設定重新啟動\) 頁面上，選取 [不要重新啟動]，然後選擇 [下一步]。

   1. 在 [Save Self Extraction Directive] \(儲存自我解壓縮指示詞\) 頁面上，選取 [Save Self Extraction Directive (SED) file] \(儲存自我解壓縮指示詞 (SED) 檔案\)，然後選擇 [下一步]。

   1. 在 [建立封裝] 頁面上，選擇 [下一步]。 選擇 [完成]。

1. 在沒有 Visual C++ 程式庫的另一部電腦上測試自我解壓縮安裝檔：

   1. 在另一部電腦上，下載安裝檔的複本，然後執行複本並遵循其所提供的步驟加以安裝。 根據選取的選項，安裝可能需要**以系統管理員身分執行**命令。

   1. 執行 MFC 應用程式。

      自我解壓縮安裝檔會安裝您在步驟 2 中指定之資料夾中的 MFC 應用程式。 由於自我解壓縮安裝檔中隨附 Visual C++ 可轉散發套件安裝程式，因此應用程式會成功執行。

      > [!IMPORTANT]
      > 為了判斷所安裝的執行階段版本，安裝程式會檢查登錄機碼 \HKLM\SOFTWARE\Microsoft\VisualStudio\\\<version>\VC\Runtimes\\<platform>。 如果目前安裝的版本比安裝程式嘗試安裝的版本還要新，則安裝程式會傳回成功而不安裝較舊版本，並在 [控制台] 的已安裝程式頁面上保留另一個項目。

## <a name="see-also"></a>另請參閱

[部署範例](deployment-examples.md)<br/>

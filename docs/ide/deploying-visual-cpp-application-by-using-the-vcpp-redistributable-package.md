---
title: 部署應用程式使用的可轉散發套件 （c + +） |Microsoft 文件
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
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>逐步解說：使用 Visual C++ 可轉散發套件部署 Visual C++ 應用程式
本文將逐步說明如何使用 Visual c + + 可轉散發套件部署 Visual c + + 應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 您必須擁有這些元件才能完成此逐步解說：  
  
-   已安裝 Visual Studio 的電腦。  
  
-   額外的電腦未安裝 Visual c + + 程式庫。  
  
### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>若要將應用程式部署使用 Visual c + + 可轉散發套件  
  
1.  建立並建置 MFC 應用程式中的前三個步驟[逐步解說： 部署 Visual c + + 應用程式所使用之安裝專案](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
2.  建立檔案並命名它 setup.bat，加入下列的命令。 變更`MyMFCApplication`專案的名稱。  
  
    ```cmd
    @echo off  
    vcredist_x86.exe  
    mkdir "C:\Program Files\MyMFCApplication"  
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"  
    ```  
  
3.  建立自我解壓縮安裝檔案：  
  
    1.  在命令提示字元或在**執行**視窗中，執行 iexpress.exe。  
  
    2.  選取**建立新的自動解壓縮導向檔案**，然後選擇 [**下一步**] 按鈕。  
  
    3.  選取**解壓縮檔案，並執行安裝指令**，然後選擇 **下一步**。  
  
    4.  在文字方塊中，輸入您的 MFC 應用程式的名稱，然後選擇**下一步**。  
  
    5.  在**確認提示**頁面上，選取**不提示**，然後選擇 **下一步**。  
  
    6.  在**授權合約**頁面上，選取**不會顯示授權**，然後選擇 **下一步**。  
  
    7.  在**封裝檔案**頁面上，加入下列檔案，然後選擇**下一步**。  
  
        -   MFC 應用程式 （.exe 檔案）。  
  
        -   vcredist_x86.exe。 此檔案位於 \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\vcredist_x86\\。  
  
        -   您在前面步驟中建立 setup.bat 檔案。  
  
    8.  在**安裝程式，以啟動**頁面上，於**安裝程式** 文字方塊中，輸入下列命令列，然後選擇**下一步**。  
  
         **cmd.exe /c"setup.bat"**  
  
    9. 在**顯示視窗**頁面上，選取**預設**，然後選擇 **下一步**。  
  
    10. 在**完成的訊息**頁面上，選取**沒有訊息**，然後選擇 **下一步**。  
  
    11. 在**封裝名稱和選項**頁面上，輸入您自動解壓縮安裝檔案名稱，選取**儲存檔案使用封裝內的長檔名**選項，然後再選擇**下一步**. 檔案名稱的結尾必須是 Setup.exe—for 範例中，MyMFCApplicationSetup.exe。  
  
    12. 在**設定重新啟動**頁面上，選取**不重新啟動**，然後選擇 **下一步**。  
  
    13. 在**儲存自動解壓縮導向**頁面上，選取**儲存自動擷取 (SED) 檔案**，然後選擇 **下一步**。  
  
    14. 在**建立套件**頁面上，選擇**下一步**。  
  
4.  測試自動解壓縮安裝檔案的其他電腦上，但不需要的 Visual c + + 程式庫：  
  
    1.  另一部電腦，下載安裝檔案，然後再安裝它執行它，並遵循所提供的步驟。  
  
    2.  執行 MFC 應用程式。  
  
         自我解壓縮的安裝程式檔案會安裝您在步驟 2 中指定的資料夾中的 MFC 應用程式。 因為 Visual c + + 可轉散發套件安裝程式包含自我解壓縮安裝檔案中，會成功執行應用程式。  
  
        > [!IMPORTANT]
        >  若要判斷所安裝的執行階段版本，安裝程式會檢查登錄金鑰 \HKLM\SOFTWARE\Microsoft\VisualStudio\11.0\VC\Runtimes\\[平台]。 如果目前已安裝的版本比安裝程式正在嘗試安裝的版本還要新，則安裝程式傳回成功，而不需要安裝較舊的版本，並且保留在已安裝的程式 頁面上，控制台中的其他項目。  
  
## <a name="see-also"></a>另請參閱  
 [部署範例](../ide/deployment-examples.md)
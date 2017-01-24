---
title: "逐步解說：使用 Visual C++ 可轉散發套件部署 Visual C++ 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "逐步解說, 使用可轉散發套件部署 Visual C++ 應用程式"
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：使用 Visual C++ 可轉散發套件部署 Visual C++ 應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這篇逐步的文件說明如何使用 Visual C\+\+ 可轉散發套件部署 Visual C\+\+ 應用程式。  
  
## 必要條件  
 您必須完成這些元件的逐步解說:  
  
-   使用 Visual Studio 的電腦上安裝。  
  
-   另一部沒有 Visual C\+\+ 程式庫的電腦。  
  
### 使用 Visual C\+\+ 可轉散發套件部署應用程式  
  
1.  依照中的前三個步驟建立並建置 MFC 應用程式在 [Walkthrough: Deploying a Visual C\+\+ Application By Using a Setup Project](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)。  
  
2.  建立檔案，並將它命名為 setup.bat，然後加入下列命令加入其中。  將 `MyMFCApplication` 加入至您的專案名稱。  
  
    ```  
    @echo off  
    vcredist_x86.exe  
    mkdir "C:\Program Files\MyMFCApplication"  
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"  
    ```  
  
3.  建立自動解壓縮安裝檔:  
  
    1.  在命令提示字元或在 \[**執行**\] 視窗中，執行 iexpress.exe。  
  
    2.  選取 \[**建立新的自我提取指示詞檔案**\] 然後選擇 \[**下**\] 按鈕。  
  
    3.  選取 \[**擷取檔案並執行安裝命令**\] 然後選擇 \[**下**\]。  
  
    4.  在文字方塊中，輸入您的 MFC 應用程式名稱並選取 \[**下**\]。  
  
    5.  在 \[**確認提示**\] 頁面上選取 \[**沒有提示**\] \]，然後選取 \[**下**\]。  
  
    6.  在 \[**授權合約**\] 頁面上選取 \[**不要顯示授權**\] \]，然後選取 \[**下**\]。  
  
    7.  在 \[**封裝的檔案**\] 頁面中，將下列檔案並選取 \[**下**\]。  
  
        -   您的 MFC 應用程式 \(.exe 檔案\)。  
  
        -   vcredist\_x86.exe。  這個檔案位於\\ Program Files \\ Microsoft SDKs \\ Windows \\ v7.0A \\啟動載入器\\ Packages \\ vcredist\_x86 \\。  
  
        -   您在先前步驟中建立的 setup.bat 檔。  
  
    8.  在 \[**啟動安裝程式**\] 頁面上，於 \[**安裝程式**\] 文字方塊中，輸入下列命令列然後選取 \[**下**\]。  
  
         **cmd.exe \/c "setup.bat"**  
  
    9. 在 \[**顯示視窗。**\] 頁面上選取 \[**預設**\] \]，然後選取 \[**下**\]。  
  
    10. 在 \[**完成的訊息。**\] 頁面上選取 \[**沒有訊息**\] \]，然後選取 \[**下**\]。  
  
    11. 在 \[**套件名稱和選項。**\] 頁面中，輸入專案的自動解壓縮安裝檔，請選取 \[**使用長檔名中封裝，儲存檔案**\] 選項，然後選擇 \[**下**\]。  檔案名稱結尾必須是 Setup.exe。例如， MyMFCApplicationSetup.exe。  
  
    12. 在 \[**設定重新啟動**\] 頁面上選取 \[**不會重新啟動。**\] \]，然後選取 \[**下**\]。  
  
    13. 在 \[**儲存自已擷取指示詞**\] 頁面上選取 \[**儲存自已擷取指示詞 \(SED\) 檔案。**\] \]，然後選取 \[**下**\]。  
  
    14. 在 \[**建立封裝**\] 頁面上，選取 \[**下**\]。  
  
4.  測試包含在另一部電腦上執行自動解壓縮安裝檔，沒有 Visual C\+\+ 程式庫:  
  
    1.  在另一部電腦上，請下載設定檔案的複本，然後安裝它以以及它所提供的步驟。  
  
    2.  執行 MFC 應用程式。  
  
         自動解壓縮安裝檔會將 MFC 應用程式安裝於您在步驟 2 中指定的資料夾中。  因為 Visual C\+\+ 可轉散發套件安裝程式包含在自動解壓縮安裝檔中，所以應用程式才能執行成功。  
  
        > [!IMPORTANT]
        >  判斷的執行階段版本安裝，安裝程式會檢查登錄機碼 \\HKLM\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\VC\\Runtimes\\\[平台\]。  如果目前已安裝版本的安裝程式嘗試安裝的版本新，安裝程式在安裝程式頁面傳回成功，而不需要安裝舊版並將其他項目保持在主控台。  
  
## 請參閱  
 [部署範例](../ide/deployment-examples.md)
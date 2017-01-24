---
title: "如何：建立使用者控制項並裝載至對話方塊中 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++], 裝載 Windows Form 控制項"
  - "Windows Form [C++], MFC 支援"
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：建立使用者控制項並裝載至對話方塊中
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文中的步驟假設您是要建立對話方塊架構的 \([CDialog Class](../mfc/reference/cdialog-class.md)\) Microsoft Foundation Classes \(MFC\) 專案，但是您也可以在現有的 MFC 對話方塊中加入 Windows Form 控制項的支援。  
  
### 若要建立 .NET 使用者控制項  
  
1.  建立名稱為 `WindowsFormsControlLibrary1` 的 Visual C\# Windows Form 控制項程式庫專案。  
  
     按一下 \[**檔案**\] 功能表上的 \[**新增**\]，然後按一下 \[**專案**\]。  在 \[**Visual C\#**\] 資料夾中，選取 \[**Windows Form 控制項程式庫**\]。  
  
     按一下 \[**確定**\]，接受 `WindowsFormsControlLibrary1` 專案名稱。  
  
     根據預設，.NET 控制項的名稱將會是 `UserControl1`。  
  
2.  在 `UserControl1` 中加入子控制項。  
  
     在 \[**工具箱**\] 中，開啟 \[**所有 Windows Form**\] 清單。  將 \[**Button**\] 控制項拖曳至 `UserControl1` 設計介面。  
  
     另外再加入 \[**TextBox**\] 控制項。  
  
3.  按兩下 \[**方案總管**\] 中的 \[**UserControl1.Designer.cs**\]，予以開啟進行編輯。  將 TextBox 和 Button 的宣告從 `private` 變更為 `public`。  
  
4.  建置專案。  
  
     在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
### 若要建立 MFC 主應用程式  
  
1.  建立 MFC 應用程式專案。  
  
     按一下 \[**檔案**\] 功能表上的 \[**新增**\]，然後按一下 \[**專案**\]。  在 \[**Visual C\+\+**\] 資料夾中，選取 \[**MFC 應用程式**\]。  
  
     在 \[**名稱**\] 方塊中，輸入 `MFC01`。  將方案設定變更為 \[**加入至方案**\]。  按一下 \[**確定**\]。  
  
     在 \[**MFC 應用程式精靈**\] 中，針對 \[應用程式類型\] 選取 \[**對話方塊架構**\]。  接受其餘的預設設定並且按一下 \[**完成**\]。  這時會建立具有 MFC 對話方塊的 MFC 應用程式。  
  
2.  在 MFC 對話方塊中加入預留位置控制項。  
  
     在 \[**檢視**\] 功能表上按一下 \[**資源檢視**\]。  在 \[**資源檢視**\] 中，展開 \[**對話方塊**\] 資料夾，然後按兩下 `IDD_MFC01_DIALOG`。  此對話方塊資源隨即出現在 \[**資源編輯器**\] 中。  
  
     在 \[**工具箱**\] 中，開啟 \[**對話方塊編輯器**\] 清單。  將 \[**靜態文字**\] 控制項拖曳至對話方塊資源。  \[**靜態文字**\] 控制項將會當做 .NET Windows Form 控制項的預留位置。  將其大小調整為大約 Windows Form 控制項的大小。  
  
     在 \[**屬性**\] 視窗中，將 \[**靜態文字**\] 控制項的 \[**ID**\] 變更為 `IDC_CTRL1`，並將 \[**TabStop**\] 屬性變更為 \[**True**\]。  
  
3.  設定 Common Language Runtime \(CLR\) 支援的專案。  
  
     在 \[**方案總管**\] 中，以滑鼠右鍵按一下 MFC01 專案節點，然後按一下 \[**屬性**\]。  
  
     在 \[**屬性頁**\] 對話方塊的 \[**組態屬性**\] 之下，選取 \[**一般**\]。  在 \[**專案預設值**\] 區段中，將 \[**Common Language Runtime 支援**\] 設定為 \[**Common Language Runtime 支援 \(\/clr\)**\]。  
  
     在 \[**組態屬性**\] 之下，展開 \[**C\/C\+\+**\]，然後選取 \[**一般**\] 節點。  將 \[**偵錯資訊格式**\] 設定為 \[**程式資料庫 \(\/Zi\)**\]。  
  
     選取 \[**程式碼產生**\] 節點。  將 \[**啟用最少重建**\] 設定為 \[**否 \(\/Gm\-\)**\]。  並且將 \[**基礎執行階段檢查**\] 設定為 \[**預設值**\]。  
  
     按一下 \[**確定**\] 套用變更。  
  
4.  將參考加入至 .NET 控制項。  
  
     在 \[**方案總管**\] 中，以滑鼠右鍵按一下 MFC01 專案節點，然後按一下 \[**加入**\], \[**參考**\]。  在 \[**屬性頁**\] 上，按一下 \[**加入新參考**\]，選取 \[**WindowsFormsControlLibrary1**\] \(在 \[**專案**\] 索引標籤下\)，然後按一下 \[**確定**\]。  這時會加入採用 [\/FU](../build/reference/fu-name-forced-hash-using-file.md) 編譯器選項格式的參考，以便編譯程式。  同時也會將 WindowsFormsControlLibrary1.dll 的複本放在 \\MFC01\\ 專案資料夾中，以便執行程式。  
  
5.  在 Stdafx.h 中尋找此行：  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     將下列程式碼行加入至那行上面：  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  加入建立 Managed 控制項的程式碼。  
  
     首先，請宣告 Managed 控制項。  在 MFC01Dlg.h 中，移至對話方塊類別的宣告部分，然後在 Protected 範圍內加入使用者控制項的資料成員，如下所示。  
  
    ```  
    class CMFC01Dlg : public CDialog  
    {  
       // ...  
       // Data member for the .NET User Control:  
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;  
    ```  
  
     接下來，提供 Managed 控制項的實作。  在 MFC01Dlg.cpp 內由 \[MFC 應用程式精靈\] 所產生的 `CMFC01Dlg::DoDataExchange` 對話方塊覆寫中 \(而不是同一個檔案中的 `CAboutDlg::DoDataExchange`\)，加入下列程式碼，建立 Managed 控制項並且使其與靜態的預留位置 IDC\_CTRL1 產生關聯。  
  
    ```  
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
    {  
       CDialog::DoDataExchange(pDX);  
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);  
    }  
    ```  
  
7.  建置及執行專案。  
  
     在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**MFC01**\]，然後按一下 \[**設定為啟始專案**\]。  
  
     在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
     在 \[**偵錯**\] 功能表上，按一下 \[**啟動但不偵錯**\]。  MFC 對話方塊應顯示 Windows Form 控制項。  
  
## 請參閱  
 [將 Windows Form 使用者控制項裝載至 MFC 對話方塊中](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)
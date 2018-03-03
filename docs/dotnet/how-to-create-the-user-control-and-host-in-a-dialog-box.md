---
title: "如何： 在對話方塊中建立使用者控制項並裝載 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 81a618c46f08366b9de2a02cbf84f73d42e7b108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>如何：建立使用者控制項並裝載至對話方塊中
這篇文章中的步驟假設您正在建立對話方塊架構 ([CDialog 類別](../mfc/reference/cdialog-class.md)) Microsoft Foundation Classes (MFC) 專案，但是您也可以將 Windows Form 控制項的支援加入現有的 MFC 對話方塊。  
  
### <a name="to-create-the-net-user-control"></a>若要建立.NET 使用者控制項  
  
1.  建立名為 Visual C# Windows Form 控制項程式庫專案`WindowsFormsControlLibrary1`。  
  
     在 [檔案]  功能表上，按一下 [新增]  及 [專案] 。 在**Visual C#**資料夾中，選取**Windows Form 控制項程式庫**。  
  
     接受`WindowsFormsControlLibrary1`專案名稱，請按一下**確定**。  
  
     根據預設，.NET 控制項的名稱會是`UserControl1`。  
  
2.  將子控制項加入`UserControl1`。  
  
     在**工具箱**，開啟**所有 Windows Form**清單。 拖曳**按鈕**控制權傳輸至`UserControl1`設計介面。  
  
     也新增**文字方塊**控制項。  
  
3.  在**方案總管 中**，連按兩下**UserControl1.Designer.cs**開啟進行編輯。 變更文字方塊和按鈕的宣告`private`至`public`。  
  
4.  建置專案。  
  
     在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
### <a name="to-create-the-mfc-host-application"></a>若要建立 MFC 主應用程式  
  
1.  建立 MFC 應用程式專案。  
  
     在 [檔案]  功能表上，按一下 [新增]  及 [專案] 。 在**Visual c + +**資料夾中，選取**MFC 應用程式**。  
  
     在 [名稱] 方塊中，輸入 `MFC01`。 將方案設定變更為**將加入至方案**。 按一下 [確定 **Deploying Office Solutions**]。  
  
     在**MFC 應用程式精靈**，應用程式類型 選取**對話方塊架構**。 接受其餘的預設設定，然後按一下**完成**。 這會建立具有 MFC 對話方塊的 MFC 應用程式。  
  
2.  加入 MFC 對話方塊中的預留位置控制項。  
  
     在**檢視**功能表上，按一下 **資源檢視**。 在**資源檢視**，依序展開**對話方塊**資料夾，然後按兩下`IDD_MFC01_DIALOG`。 對話方塊資源會出現在**資源編輯器**。  
  
     在**工具箱**，開啟**對話方塊編輯器**清單。 拖曳**靜態文字**對話方塊資源控制。 **靜態文字**控制項將做為.NET Windows Form 控制項的預留位置。 其大小調整為大約 Windows Form 控制項的大小。  
  
     在**屬性**視窗中，變更**識別碼**的**靜態文字**控制權傳輸至`IDC_CTRL1`並變更**TabStop**屬性**True**。  
  
3.  設定專案的 Common Language Runtime (CLR) 支援。  
  
     在**方案總管 中**MFC01 專案節點，以滑鼠右鍵按一下，然後按**屬性**。  
  
     在**屬性頁**對話方塊的 **組態屬性**，選取**一般**。 在**專案預設值**區段中，將**Common Language Runtime 支援**至**Common Language Runtime 支援 (/ clr)**。  
  
     在下**組態屬性**，依序展開**C/c + +**選取**一般**節點。 設定**偵錯資訊格式**至**程式資料庫 (/Zi)**。  
  
     選取**程式碼產生**節點。 設定**啟用最少重建**至**否 (/ Gm-)**。 也設定**基本執行階段會檢查**至**預設**。  
  
     按一下**確定**才能套用變更。  
  
4.  新增.NET 控制項的參考。  
  
     在**方案總管 中**MFC01 專案節點上按一下滑鼠右鍵，然後按**新增**，**參考**。 上**屬性頁**，按一下 [**加入新參考**，選取**WindowsFormsControlLibrary1** (下**專案**] 索引標籤)，然後按一下**確定**。 這將參考加入的形式[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項，使程式會進行編譯。 它也會將複本置於 WindowsFormsControlLibrary1.dll \MFC01\ 專案資料夾中，因此程式會執行。  
  
5.  在 Stdafx.h，找到這一行：  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     它的上方，將下列幾行：  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  加入程式碼來建立受管理的控制項。  
  
     首先，宣告 managed 的控制項。 在 MFC01Dlg.h，移至對話方塊類別的宣告並加入使用者控制項的資料成員中受保護範圍，如下所示。  
  
    ```  
    class CMFC01Dlg : public CDialog  
    {  
       // ...  
       // Data member for the .NET User Control:  
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;  
    ```  
  
     接下來，提供受管理的控制項的實作。 MFC01Dlg.cpp，在對話方塊中的覆寫`CMFC01Dlg::DoDataExchange`產生 MFC 應用程式精靈 (不`CAboutDlg::DoDataExchange`，這是在相同的檔案)，加入下列程式碼，建立受管理的控制項，並將它與靜態預留位置 IDC_CTRL1 關聯。  
  
    ```  
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
    {  
       CDialog::DoDataExchange(pDX);  
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);  
    }  
    ```  
  
7.  建置並執行專案。  
  
     在**方案總管] 中**，以滑鼠右鍵按一下**MFC01** ，然後按一下 [**設定為啟始專案**。  
  
     在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
     在**偵錯**功能表上，按一下 **啟動但不偵錯**。 MFC 對話方塊應該會顯示在 Windows Form 控制項。  
  
## <a name="see-also"></a>請參閱  
 [將 Windows Forms 使用者控制項裝載至 MFC 對話方塊中](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)
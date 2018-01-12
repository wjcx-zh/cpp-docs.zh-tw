---
title: "如何： 建立使用者控制項並裝載 MDI 檢視 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8b9b3c8ff385aed22785386c035ed537d8d97e97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>如何：建立使用者控制項並裝載 MDI 檢視
下列步驟示範如何建立.NET Framework 使用者控制項，撰寫使用者控制項中的控制項類別程式庫 （特別是，Windows 控制項程式庫專案），然後將專案編譯成組件。 從 MFC 應用程式使用衍生自的類別可以使用控制項[CView 類別](../mfc/reference/cview-class.md)和[CWinFormsView 類別](../mfc/reference/cwinformsview-class.md)。  
  
 如需如何建立 Windows Form 使用者控制項和撰寫控制項類別程式庫的資訊，請參閱[How to： 撰寫使用者控制項](/dotnet/framework/winforms/controls/how-to-author-composite-controls)。  
  
> [!NOTE]
>  在某些情況下，Windows Form 控制項，例如協力廠商方格控制項，可能無法正常運作的 MFC 應用程式中裝載時。 建議的因應措施是將 Windows Form 使用者控制項放在 MFC 應用程式，並將第三方方格控制項在使用者控制項內。  
  
 此程序假設您建立 Windows Form 控制項程式庫專案中的程序根據名為 WindowsFormsControlLibrary1， [How to： 在對話方塊中建立使用者控制項並裝載](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。  
  
### <a name="to-create-the-mfc-host-application"></a>若要建立 MFC 主應用程式  
  
1.  建立 MFC 應用程式專案。  
  
     在**檔案**功能表上，選取**新增**，然後按一下 **專案**。 在**Visual c + +**資料夾中，選取**MFC 應用程式**。  
  
     在**名稱**方塊中，輸入`MFC02`並變更**方案**設**將加入至方案**。 按一下 [確定 **Deploying Office Solutions**]。  
  
     在**MFC 應用程式精靈**，接受所有預設值，然後按**完成**。 這會建立多重文件介面 MFC 應用程式。  
  
2.  設定專案的 Common Language Runtime (CLR) 支援。  
  
     在**方案總管 中**，以滑鼠右鍵按一下`MFC01`專案節點，然後選取**屬性**從內容功能表。 **屬性頁** 對話方塊隨即出現。  
  
     在下**組態屬性**，選取**一般**。 在下**專案預設值**區段中，將**Common Language Runtime 支援**至**Common Language Runtime 支援 (/ clr)**。  
  
     在下**組態屬性**，依序展開**C/c + +**按一下**一般**節點。 設定**偵錯資訊格式**至**程式資料庫 (/Zi)**。  
  
     按一下**程式碼產生**節點。 設定**啟用最少重建**至**否 (/ Gm-)**。 也設定**基本執行階段會檢查**至**預設**。  
  
     按一下**確定**以套用變更。  
  
3.  在 stdafx.h，加入下列一行：  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
4.  新增.NET 控制項的參考。  
  
     在**方案總管 中**，以滑鼠右鍵按一下`MFC02`專案節點，然後選取**新增**，**參考**。 在**屬性頁**，按一下**加入新參考**，選取 WindowsFormsControlLibrary1 (下**專案** 索引標籤)，然後按一下**確定**. 這將參考加入的形式[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項，使程式會進行編譯，也會複製到 WindowsFormsControlLibrary1.dll`MFC02`專案目錄，以便執行程式。  
  
5.  在 stdafx.h，找到這一行：  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     將上方的下列幾行：  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  修改檢視類別，讓它繼承自[CWinFormsView](../mfc/reference/cwinformsview-class.md)。  
  
     在 MFC02View.h，取代[CView](../mfc/reference/cview-class.md)與[CWinFormsView](../mfc/reference/cwinformsview-class.md) ，使程式碼顯示，如下所示：  
  
    ```  
    class CMFC02View : public CWinFormsView  
    {  
    };  
    ```  
  
     如果您想 MDI 應用程式中加入額外的檢視，您必須呼叫[CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate)為您建立每個檢視。  
  
7.  修改 MFC02View.cpp 檔案以變更 CWinFormsView CView IMPLEMENT_DYNCREATE 巨集和訊息對應中，並取代現有的空白建構函式的建構函式，如下所示：  
  
    ```  
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)  
  
    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)   
    {  
    }  
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)  
    //leave existing body as is  
    END_MESSAGE_MAP()  
    ```  
  
8.  建置並執行專案。  
  
     在**方案總管 中**，MFC02 上按一下滑鼠右鍵，然後選取**設定為啟始專案**。  
  
     在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
     在**偵錯**功能表上，按一下 **啟動但不偵錯**。  
  
## <a name="see-also"></a>請參閱  
 [將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
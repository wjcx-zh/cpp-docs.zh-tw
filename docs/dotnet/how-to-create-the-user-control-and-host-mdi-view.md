---
title: HOW TO：建立使用者控制項並裝載 MDI 檢視
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 7d535fce47be5504f6f521cda1267344206287da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387431"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>HOW TO：建立使用者控制項並裝載 MDI 檢視

下列步驟示範如何建立.NET Framework 使用者控制項，撰寫使用者控制項中的控制項類別程式庫 （具體而言，是 Windows 控制項程式庫專案），然後將專案編譯成組件。 控制項可以使用從 MFC 應用程式，會使用衍生自[CView 類別](../mfc/reference/cview-class.md)並[CWinFormsView 類別](../mfc/reference/cwinformsview-class.md)。

如需如何建立 Windows Forms 使用者控制項和撰寫控制項類別程式庫的詳細資訊，請參閱[How to:撰寫使用者控制項](/dotnet/framework/winforms/controls/how-to-author-composite-controls)。

> [!NOTE]
>  在某些情況下，Windows Forms 控制項，例如協力廠商的方格控制項，可能無法正常運作時裝載於 MFC 應用程式。 建議的解決方法是將 Windows Form 使用者控制項放在 MFC 應用程式，並將協力廠商的方格控制項，在使用者控制項。

此程序假設您建立 Windows Form 控制項程式庫專案中的程序命名 WindowsFormsControlLibrary1， [How to:在對話方塊中建立使用者控制項並裝載](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)。

### <a name="to-create-the-mfc-host-application"></a>若要建立 MFC 主應用程式

1. 建立 MFC 應用程式專案。

   在上**檔案**功能表上，選取**新增**，然後按一下**專案**。 在  **Visual C++** 資料夾中，選取**MFC 應用程式**。

   在**名稱**方塊中，輸入`MFC02`並將變更**解決方案**設為**新增至方案**。 按一下 [確定] 。

   在  **MFC 應用程式精靈**，接受所有預設值，然後按一下 **完成**。 這會建立多個的文件介面的 MFC 應用程式。

1. 設定專案的 Common Language Runtime (CLR) 支援。

   在 [**方案總管] 中**，以滑鼠右鍵按一下`MFC01`專案節點，然後選取**屬性**從內容功能表。 **屬性頁** 對話方塊隨即出現。

   底下**組態屬性**，選取**一般**。 底下**專案預設值**區段中，將**Common Language Runtime 支援**來**Common Language Runtime 支援 (/ clr)**。

   底下**組態屬性**，展開**C /C++** 再利用**一般**節點。 設定**偵錯資訊格式**要**程式資料庫 (/Zi)**。

   按一下 **程式碼產生**節點。 設定**啟用最少重建**要**否 (/ /gm-)**。 Ssprop_param_table_default**基本執行階段會檢查**要**預設**。

   按一下 **確定**以套用變更。

1. 在 stdafx.h 中加入下面這一行：

    ```
    #using <System.Windows.Forms.dll>
    ```

1. 新增.NET 控制項的參考。

   在 **方案總管**，以滑鼠右鍵按一下`MFC02`專案節點，然後選取**新增**，**參考**。 在**屬性頁**，按一下**加入新參考**，選取 [WindowsFormsControlLibrary1 (下**專案**] 索引標籤)，然後按一下 **[確定]**. 這會將參考新增的形式[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項，如此將會編譯程式; 它也會將 windowsformscontrollibrary1.dll 複製到`MFC02`專案目錄，以便執行程式。

1. 在 stdafx.h 中尋找此行：

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   加入這行上面：

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. 修改檢視類別，使它繼承自[CWinFormsView](../mfc/reference/cwinformsview-class.md)。

   在 MFC02View.h，取代[CView](../mfc/reference/cview-class.md)具有[CWinFormsView](../mfc/reference/cwinformsview-class.md)使程式碼看起來像這樣：

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   如果您想將額外的檢視新增至您的 MDI 應用程式，您必須呼叫[CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate)為您建立每個檢視。

1. 修改 MFC02View.cpp 檔，IMPLEMENT_DYNCREATE 巨集和訊息對應中的 CView 變更為 CWinFormsView，並以如下所示的建構函式取代現有的空白建構函式：

    ```
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)

    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)
    {
    }
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)
    //leave existing body as is
    END_MESSAGE_MAP()
    ```

1. 建置並執行專案。

   在 **方案總管**，以滑鼠右鍵按一下 MFC02，然後選取**設定為啟始專案**。

   在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

   在 **偵錯**功能表上，按一下**啟動但不偵錯**。

## <a name="see-also"></a>另請參閱

[將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

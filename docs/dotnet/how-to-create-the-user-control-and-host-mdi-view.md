---
title: HOW TO：建立使用者控制項並裝載 MDI 視圖
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 634dd9c1ad2ce9199cec0dfa7ef067bd45f242f6
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "70311882"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>HOW TO：建立使用者控制項並裝載 MDI 視圖

下列步驟示範如何建立 .NET Framework 使用者控制項、在控制項類別庫中撰寫使用者控制項（具體而言，Windows 控制項程式庫專案），然後將專案編譯成元件。 然後，可以使用從[CView 類別](../mfc/reference/cview-class.md)和[CWinFormsView 類別](../mfc/reference/cwinformsview-class.md)衍生之類別的 MFC 應用程式來取用控制項。

如需如何建立 Windows Forms 使用者控制項和撰寫控制項類別庫的相關資訊，請參閱[如何：撰寫使用者控制項](/dotnet/framework/winforms/controls/how-to-author-composite-controls)。

> [!NOTE]
>  在某些情況下，當裝載于 MFC 應用程式時，Windows Forms 控制項（例如協力廠商方格控制項）的行為可能不可靠。 建議的解決方法是將 Windows Forms 使用者控制項放在 MFC 應用程式中，並將協力廠商方格控制項放在使用者控制項內。

此程式假設您已建立名為 WindowsFormsControlLibrary1 的 Windows Forms 控制項程式庫專案，依據[how to：在對話方塊](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)中建立使用者控制項和主機。

### <a name="to-create-the-mfc-host-application"></a>建立 MFC 主應用程式

1. 建立 MFC 應用程式專案。

   **在 [檔案**] 功能表上，選取 [**新增**]，然後按一下 [**專案**]。 在 [**視覺C++效果**] 資料夾中，選取 [ **MFC 應用程式**]。

   在 [**名稱**] 方塊中`MFC02` ，輸入並變更**解決方案**設定以**新增至方案**。 按一下 [確定 **Deploying Office Solutions**]。

   在**MFC 應用程式精靈**中，接受所有預設值，然後按一下 **[完成]** 。 這會建立具有多個檔介面的 MFC 應用程式。

1. 設定 Common Language Runtime （CLR）支援的專案。

   在**方案總管**中，以滑鼠右鍵`MFC01`按一下專案節點，然後從內容功能表中選取 [**屬性**]。 [**屬性頁**] 對話方塊隨即出現。

   在 [設定**屬性**] 下，選取 **[一般**]。 在 [**專案預設值**] 區段下，將 [ **common language runtime 支援**] 設定為 [ **common language runtime 支援（/clr）** ]。

   在 [設定**屬性**] 底下，展開 [ **C/C++**  ]，然後按一下 [**一般**] 節點。 將 [**偵錯工具資訊格式**] 設定為 **[程式資料庫（/zi）** ]。

   按一下 [程式**代碼產生**] 節點。 將 [**啟用最少重建**] 設定為 **[否] （/Gm-）** 。 也將 [**基本執行時間檢查**] 設定為 [**預設**]。

   按一下 **[確定]** 以套用變更。

1. 在*pch* （Visual Studio 2017 和更早版本的*stdafx.h* ）中，新增下列程式程式碼：

    ```
    #using <System.Windows.Forms.dll>
    ```

1. 加入 .NET 控制項的參考。

   在**方案總管**中，以滑鼠右鍵`MFC02`按一下專案節點，然後選取 [**新增**]、[**參考**]。 在**屬性頁**中，按一下 **[加入新參考**]，選取 [WindowsFormsControlLibrary1] （在 [**專案**] 索引標籤下），然後按一下 **[確定]** 。 這會以[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項的形式加入參考，讓程式進行編譯;它也會將 WindowsFormsControlLibrary1 複製到`MFC02`專案目錄中，以便程式執行。

1. 在 stdafx.h 中，尋找下面這一行：

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   將下列幾行新增至其上方：

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. 修改 view 類別，使其繼承自[CWinFormsView](../mfc/reference/cwinformsview-class.md)。

   在 MFC02View 中，以[CWinFormsView](../mfc/reference/cwinformsview-class.md)取代[CView](../mfc/reference/cview-class.md) ，讓程式碼看起來如下：

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   如果您想要在 MDI 應用程式中加入其他視圖，您必須針對您所建立的每個視圖呼叫[CWinApp：： AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) 。

1. 修改 MFC02View .cpp 檔案，將 IMPLEMENT_DYNCREATE 宏和訊息對應中的 CView 變更為 CWinFormsView，並以如下所示的函式取代現有的空的函式：

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

   在**方案總管**中，以滑鼠右鍵按一下 [MFC02]，然後選取 [**設定為啟始專案**]。

   在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

   在 [**調試**] 功能表上，按一下 [**啟動但不進行調試**]。

## <a name="see-also"></a>另請參閱

[將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

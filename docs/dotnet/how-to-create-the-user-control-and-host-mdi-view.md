---
title: 如何：建立使用者控制項並裝載 MDI 檢視
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 72501ba32d3b8b9a5c5fd8dd0c56f0628642b147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374460"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>如何：建立使用者控制項並裝載 MDI 檢視

以下步驟演示如何創建 .NET Framework 使用者控件,在控件類庫中創作使用者控制件(特別是 Windows 控件庫專案),然後將專案編譯為程式集。 然後,可以從使用從[CView 類](../mfc/reference/cview-class.md)和[CWinFormsView 類](../mfc/reference/cwinformsview-class.md)派生的類的 MFC 應用程式使用該控制項。

有關如何建立 Windows 表單使用者控制項和創作控制項類別的庫的資訊,請參考[如何:作者使用者控制件](/dotnet/framework/winforms/controls/how-to-author-composite-controls)。

> [!NOTE]
> 在某些情況下,Windows 表單控制項控制件(如第三方網格控件)在 MFC 應用程式中託管時可能無法可靠地運行。 建議的解決方法是在 MFC 應用程式中放置 Windows 窗體使用者控件,並將第三方網格控件放在使用者控制項中。

此過程假定您創建了名為 WindowsFormsControlLibrary1 的 Windows 窗體控件庫專案,根據[「如何:在對話框中創建使用者控件和主機](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)」中的過程。

### <a name="to-create-the-mfc-host-application"></a>建立 MFC 主機應用程式

1. 創建 MFC 應用程式專案。

   在 **「檔案**」選單上,選擇 **「新建**」,然後按下「**專案**」。 在**視覺C++** 資料夾中, 選擇**MFC 應用程式**。

   在 **「名稱」** 框`MFC02`中, 輸入並變更 **「 解決方案**」 設定**以新增到解決方案**。 按一下 [確定]  。

   在**MFC 應用程式精靈**中,接受所有預設值,然後單擊 **「完成**」。。 這將創建具有多個文檔介面的 MFC 應用程式。

1. 為通用語言運行時 (CLR) 支援配置專案。

   在**解決方案資源管理器**中,右鍵單`MFC01`擊 專案節點,並從上下文菜單中選擇 **「屬性**」。。 將顯示「**屬性頁**」 對話框。

   在 **「設定屬性**」下,選擇 **「一般**」。 在 **「項目預設值」** 部分下,將 **「通用語言運行時支援**」設置為**通用語言執行時支援 (/clr)。**

   在 **「設定屬性**」下,展開**C/C++** 並單擊**常規**節點。 將**除錯資訊格式**設定為**程式資料庫 (/Zi)。**

   單擊**代碼生成**節點。 將**開啟最小重建**設定為**否 (/Gm-)**。 還將**基本運行時檢查**設置為 **「預設**」。

   按下「**確定」** 以應用更改。

1. 在*pch.h(Visual* Studio 2017 和更早版本中的*stdafx.h)* 中,添加以下行:

    ```
    #using <System.Windows.Forms.dll>
    ```

1. 添加對 .NET 控制項的引用。

   在**解決方案資源管理員**中,右鍵按`MFC02`下專案節點並選擇「**新增**」**。** 在 **「屬性頁**」中,按一下「**添加新參考**」,選擇 WindowsFormsControlLibrary1(在 **「專案**」選項卡下),然後單擊"**確定**"。 這將以[/FU](../build/reference/fu-name-forced-hash-using-file.md)編譯器選項的形式添加引用,以便程式將編譯;它還將 WindowsFormsControlLibrary1.dll`MFC02`複製到 專案目錄中,以便程式將運行。

1. 在 stdafx.h 中,找到此行:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   在上面新增以下行:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. 修改檢視類,以便從[CWinFormsView](../mfc/reference/cwinformsview-class.md)繼承。

   在 MFC02View.h 中,將[CView](../mfc/reference/cview-class.md)替換為[CWinFormsView,](../mfc/reference/cwinformsview-class.md)以便代碼如下所示:

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   如果要向 MDI 應用程式添加其他檢視,則需要為創建的每個檢視調用[CWinApp::AddDocTemplate。](../mfc/reference/cwinapp-class.md#adddoctemplate)

1. 修改 MFC02View.cpp 檔,在IMPLEMENT_DYNCREATE宏和消息映射中將 CView 更改為 CWinFormsView,並將現有的空構造函數替換為如下所示的構造函數:

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

   在**解決方案資源管理器**中,右鍵單擊 MFC02 並選擇 **「設置為啟動專案**」。。

   在 [建置]**** 功能表上，按一下 [建置方案]****。

   在 **「調試」** 選單上,按一下 **「 不調試即可開始**」。

## <a name="see-also"></a>另請參閱

[將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

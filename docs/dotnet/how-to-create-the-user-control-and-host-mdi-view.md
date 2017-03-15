---
title: "如何：建立使用者控制項並裝載 MDI 檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++], Windows Form 控制項"
  - "Windows Form [C++], MFC 支援"
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：建立使用者控制項並裝載 MDI 檢視
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列步驟說明如何建立 .NET Framework 使用者控制項、在控制項類別程式庫中撰寫使用者控制項 \(特別是 Windows 控制項程式庫專案\)，然後將專案編譯至組件。  然後 MFC 應用程式會使用控制項，而此應用程式則是使用衍生自 [CView Class](../mfc/reference/cview-class.md)和 [CWinFormsView Class](../mfc/reference/cwinformsview-class.md)的類別。  
  
 如需如何建立 Windows Form 使用者控制項以及撰寫控制項類別程式庫的詳細資訊，請參閱 [HOW TO：撰寫使用者控制項](../Topic/How%20to:%20Author%20Composite%20Controls.md)。  
  
> [!NOTE]
>  在某些情況下，當 Windows Form 控制項 \(例如協力廠商的方格控制項\) 裝載於 MFC 應用程式中時，可能無法正常運作。  建議的解決方法是將 Windows Form 使用者控制項放置在 MFC 應用程式中，然後將協力廠商的方格控制項放置在使用者控制項中。  
  
 如 [如何：建立使用者控制項並裝載至對話方塊中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)的程序所示，此程序假設您已建立名為 WindowsFormsControlLibrary1 的 Windows Form 控制項程式庫專案。  
  
### 若要建立 MFC 主應用程式  
  
1.  建立 MFC 應用程式專案。  
  
     選取 \[**檔案**\] 功能表上的 \[**新增**\]，然後按一下 \[**專案**\]。  在 \[**Visual C\+\+**\] 資料夾中，選取 \[**MFC 應用程式**\]。  
  
     在 \[**名稱**\] 方塊中，輸入 `MFC02`，並且將 \[**方案**\] 設定變更為 \[**加入至方案**\]。  按一下 \[**確定**\]。  
  
     在 \[**MFC 應用程式精靈**\] 中，接受所有預設值，然後按一下 \[**完成**\]。  這樣便會建立具備多重文件介面 \(MDI\) 的 MFC 應用程式。  
  
2.  設定 Common Language Runtime \(CLR\) 支援的專案。  
  
     在 \[**方案總管**\] 中以滑鼠右鍵按一下 \[`MFC01`\] 方案節點，然後從內容功能表中選取 \[**屬性**\]。  \[**屬性頁**\] 對話方塊隨即出現。  
  
     在 \[**組態屬性**\] 下選取 \[**一般**\]。  在 \[**專案預設值**\] 區段底下，將 \[**Common Language Runtime 支援**\] 設定為 \[**Common Language Runtime 支援 \(\/clr\)**\]。  
  
     在 \[**組態屬性**\] 底下，展開 \[**C\/C\+\+**\]，然後按一下 \[**一般**\] 節點。  將 \[**偵錯資訊格式**\] 設定為 \[**程式資料庫 \(\/Zi\)**\]。  
  
     按一下 \[**程式碼產生**\] 節點。  將 \[**啟用最少重建**\] 設定為 \[**否 \(\/Gm\-\)**\]。  並且將 \[**基礎執行階段檢查**\] 設定為 \[**預設值**\]。  
  
     按一下 \[**確定**\] 套用變更。  
  
3.  在 stdafx.h 中，加入下列程式碼行：  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
4.  將參考加入至 .NET 控制項。  
  
     在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[`MFC02`\] 專案節點，並且選取 \[**加入**\], \[**參考**\]。  在 \[**屬性頁**\] 中，按一下 \[**加入新參考**\]，選取 \[WindowsFormsControlLibrary1\] \(在 \[**專案**\] 索引標籤下\)，然後按一下 \[**確定**\]。  這樣便會以 [\/FU](../build/reference/fu-name-forced-hash-using-file.md) 編譯器選項的形式加入參考，讓程式可以進行編譯；也會將 WindowsFormsControlLibrary1.dll 複製到 `MFC02` 專案目錄，讓程式得以執行。  
  
5.  在 stdafx.h 中尋找此行：  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     將這些行加入至那行上面：  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  修改檢視類別，使其繼承 [CWinFormsView](../mfc/reference/cwinformsview-class.md)。  
  
     在 MFC02View.h 中，以 [CWinFormsView](../mfc/reference/cwinformsview-class.md) 取代 [CView](../mfc/reference/cview-class.md)，使程式碼看起來如下所示：  
  
    ```  
    class CMFC02View : public CWinFormsView  
    {  
    };  
    ```  
  
     如果要將其他檢視加入至 MDI 應用程式，則需要針對每個建立的檢視呼叫 [CWinApp::AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md)。  
  
7.  修改 MFC02View.cpp 檔，將 IMPLEMENT\_DYNCREATE 巨集和訊息對應 \(Message Map\) 中的 CView 變更為 CWinFormsView，並且以下列顯示的建構函式 \(Constructor\) 取代現有之空的建構函式：  
  
    ```  
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)  
  
    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)   
    {  
    }  
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)  
    //leave existing body as is  
    END_MESSAGE_MAP()  
    ```  
  
8.  建置及執行專案。  
  
     在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[MFC02\]，並按一下 \[**設定為啟始專案**\]。  
  
     在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
     在 \[**偵錯**\] 功能表上，按一下 \[**啟動但不偵錯**\]。  
  
## 請參閱  
 [將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
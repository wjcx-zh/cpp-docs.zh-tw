---
title: "如何：呼叫 Windows Form 控制項的屬性和方法 | Microsoft Docs"
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
  - "呼叫方法, Windows Form 控制項"
  - "呼叫屬性"
  - "呼叫屬性, Windows Form 控制項"
  - "方法呼叫, Windows Form"
  - "Windows Form 控制項 [C++], 方法"
  - "Windows Form 控制項 [C++], 屬性"
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：呼叫 Windows Form 控制項的屬性和方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

因為 [CWinFormsView::GetControl](../Topic/CWinFormsView::GetControl.md) 傳回 <xref:System.Windows.Forms.Control?displayProperty=fullName> 的指標，而不是傳回 `WindowsControlLibrary1::UserControl1` 的指標，建議加入使用者控制項型別的成員，並在 [IView::OnInitialUpdate](../Topic/IView::OnInitialUpdate.md) 中初始化。  現在，您可以使用 `m_ViewControl` 呼叫方法和屬性。  
  
 本主題假設您先前已完成 [如何：建立使用者控制項並裝載至對話方塊中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)和 [如何：建立使用者控制項並裝載 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
### 若要建立 MFC 主應用程式  
  
1.  開啟您在 [如何：建立使用者控制項並裝載 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)建立的 MFC 應用程式。  
  
2.  將下面程式碼行加入到 MFC02View.h 中 `CMFC02View` 類別宣告的 public overrides 區段。  
  
     `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`  
  
3.  加入 OnInitialupdate 的覆寫。  
  
     顯示 \[**屬性**\] 視窗 \(F4\)。  在 \[**類別檢視**\] \(CTRL\+SHIFT\+C\) 中選取 CMFC02View 類別。  在 \[**屬性**\] 視窗中，選取覆寫的圖示。  向下捲動清單，一直到 OnInitialUpdate，  按一下下拉式清單，然後選取 \<加入\>。  在MFC02View.cpp中，確定 OnInitialUpdate 函式的主體如下所示：  
  
    ```  
    CWinFormsView::OnInitialUpdate();  
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());  
    m_ViewControl->textBox1->Text = gcnew System::String("hi");  
    ```  
  
4.  建置及執行專案。  
  
     在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
     在 \[**偵錯**\] 功能表上，按一下 \[**啟動但不偵錯**\]。  
  
     請注意，現在已經將文字方塊初始化。  
  
## 請參閱  
 [將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
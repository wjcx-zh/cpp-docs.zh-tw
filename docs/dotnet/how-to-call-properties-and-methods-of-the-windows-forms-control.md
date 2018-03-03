---
title: "如何： 呼叫屬性和方法的 Windows Form 控制項 |Microsoft 文件"
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
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: eebbc955a0b44b686986e5bd1e753ec8809a3a1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>如何：呼叫 Windows Form 控制項的屬性和方法
因為[CWinFormsView::GetControl](../mfc/reference/cwinformsview-class.md#getcontrol)將指標傳回至<xref:System.Windows.Forms.Control?displayProperty=fullName>，而非指標和`WindowsControlLibrary1::UserControl1`，建議您在加入使用者控制項類型的成員，並將它在初始化[IView::OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate). 現在您可以呼叫方法和屬性使用`m_ViewControl`。  
  
 本主題假設您之前已經完成[How to： 在對話方塊中建立使用者控制項並裝載](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)和[How to： 建立使用者控制項和主應用程式 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
### <a name="to-create-the-mfc-host-application"></a>若要建立 MFC 主應用程式  
  
1.  開啟您在建立 MFC 應用程式[How to： 建立使用者控制項和主應用程式 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)。  
  
2.  將下列行加入至的公用覆寫區段`CMFC02View`類別 MFC02View.h 中的宣告。  
  
     `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`  
  
3.  加入註冊的覆寫。  
  
     顯示**屬性**視窗 (F4)。 在**類別檢視**(CTRL + SHIFT + C)，選取 CMFC02View 類別。 在**屬性**視窗中，選取覆寫的圖示。 要註冊清單中向下 Scoll。 按一下下拉式清單並選取 \<新增 >。 在 MFC02View.cpp。 請確定 OnInitialUpdate 函式的主體，如下所示：  
  
    ```  
    CWinFormsView::OnInitialUpdate();  
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());  
    m_ViewControl->textBox1->Text = gcnew System::String("hi");  
    ```  
  
4.  建置並執行專案。  
  
     在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
     在**偵錯**功能表上，按一下 **啟動但不偵錯**。  
  
     請注意，文字方塊現在已初始化。  
  
## <a name="see-also"></a>請參閱  
 [將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
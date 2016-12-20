---
title: "如何：從原生 C++ 類別接收 Windows Form 事件 | Microsoft Docs"
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
  - "事件處理, .NET/原生 interop"
  - "事件處理, Managed/原生 interop"
  - "事件處理, 在 C++ 中接收 .NET"
  - "事件處理, C++ 中的 Windows Form"
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：從原生 C++ 類別接收 Windows Form 事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以啟用原生 C\+\+ 類別，以接收來自 Windows Form 控制項或使用 MFC 巨集對應格式的其他表單所引發 Managed 事件的回呼。  在對話方塊和檢視中的接收事件類似執行控制項的相同工作。  
  
 若要進行這項工作，您必須：  
  
-   使用 [MAKE\_DELEGATE](../Topic/MAKE_DELEGATE.md) 將 `OnClick` 事件處理常式附加至控制項。  
  
-   使用 [BEGIN\_DELEGATE\_MAP](../Topic/BEGIN_DELEGATE_MAP.md)、[END\_DELEGATE\_MAP](../Topic/END_DELEGATE_MAP.md) 和 [EVENT\_DELEGATE\_ENTRY](../Topic/EVENT_DELEGATE_ENTRY.md) 建立委派對應。  
  
 此範例會繼續進行您之前在 [如何：使用 Windows Form 執行 DDX\/DDV 資料繫結](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)中的工作。  
  
 現在，您會針對 Managed <xref:System.Windows.Forms.Control.Click> 事件，將 MFC 控制項 \(`m_MyControl`\) 與稱為 `OnClick` 的 Managed 事件處理常式委派產生關聯。  
  
### 若要附加 OnClick 事件處理常式：  
  
1.  將下列程式碼加入至 BOOL CMFC01Dlg::OnInitDialog 的實作：  
  
    ```  
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );  
    ```  
  
2.  將下列程式碼加入至 CMFC01Dlg : public CDialog 類別宣告的 public 區段。  
  
    ```  
    // delegate map  
    BEGIN_DELEGATE_MAP( CMFC01Dlg )  
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )  
    END_DELEGATE_MAP()  
  
    void OnClick( System::Object^ sender, System::EventArgs^ e );  
    ```  
  
3.  最後，將 `OnClick` 的實作加入至 CMFC01Dlg.cpp：  
  
    ```  
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)  
    {  
        AfxMessageBox(_T("Button clicked"));  
    }  
    ```  
  
## 請參閱  
 [MAKE\_DELEGATE](../Topic/MAKE_DELEGATE.md)   
 [BEGIN\_DELEGATE\_MAP](../Topic/BEGIN_DELEGATE_MAP.md)   
 [END\_DELEGATE\_MAP](../Topic/END_DELEGATE_MAP.md)   
 [EVENT\_DELEGATE\_ENTRY](../Topic/EVENT_DELEGATE_ENTRY.md)
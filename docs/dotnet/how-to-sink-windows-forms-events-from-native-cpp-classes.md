---
title: 如何： 從原生 c + + 類別接收 Windows Form 事件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2dd3778dad837ffe23d17b58b4e579844dc71f40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>如何：從原生 C++ 類別接收 Windows Form 事件
您可以啟用原生 c + + 類別，從受管理的 Windows Form 控制項或其他形式的 MFC 巨集對應格式引發的事件接收回呼。 相似執行相同工作的控制項檢視和對話方塊中的接收事件。  
  
 若要這樣做，您需要：  
  
-   附加`OnClick`事件處理常式來控制使用[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)。  
  
-   建立委派對應使用[BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)， [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)，和[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)。  
  
 這個範例會繼續在您執行的工作[How to： 使用 Windows Form 執行 DDX/DDV 資料繫](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)。  
  
 現在，您將建立關聯 MFC 控制項 (`m_MyControl`) 與 managed 的事件處理常式委派呼叫`OnClick`managed<xref:System.Windows.Forms.Control.Click>事件。  
  
### <a name="to-attach-the-onclick-event-handler"></a>若要附加 OnClick 事件處理常式：  
  
1.  將下列程式碼加入至 BOOL CMFC01Dlg::OnInitDialog 的實作：  
  
    ```  
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );  
    ```  
  
2.  將下列程式碼加入至類別 CMFC01Dlg 的宣告中的公用一節： 公用 CDialog。  
  
    ```  
    // delegate map  
    BEGIN_DELEGATE_MAP( CMFC01Dlg )  
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )  
    END_DELEGATE_MAP()  
  
    void OnClick( System::Object^ sender, System::EventArgs^ e );  
    ```  
  
3.  最後，要加入的`OnClick`CMFC01Dlg.cpp 至：  
  
    ```  
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)  
    {  
        AfxMessageBox(_T("Button clicked"));  
    }  
    ```  
  
## <a name="see-also"></a>請參閱  
 [MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)   
 [BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)   
 [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)   
 [EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)
---
title: 如何： 從原生 c + + 類別接收 Windows Forms 事件 |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9316d27637d335bc0e3a71656a5d7b9c8796ec28
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424979"
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>如何：從原生 C++ 類別接收 Windows Form 事件

您可以啟用原生 c + + 類別，以從受管理的 Windows Form 控制項或其他使用 MFC 巨集對應格式的形式引發的事件接收回撥。 檢視和對話方塊中的接收事件是類似於在控制項相同的工作。

若要這樣做，您需要：

- 附加`OnClick`控制項使用的事件處理常式[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)。

- 建立委派對應 using [BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)， [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)，並[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)。

此範例會繼續在您執行的工作[如何： 使用 Windows Form 執行 DDX/DDV 資料繫](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)。

現在，您將建立 MFC 控制項的關聯 (`m_MyControl`) 使用稱為 「 受管理的事件處理常式委派`OnClick`managed<xref:System.Windows.Forms.Control.Click>事件。

### <a name="to-attach-the-onclick-event-handler"></a>若要連結的 OnClick 事件處理常式：

1. BOOL CMFC01Dlg::OnInitDialog 的實作中加入下列程式碼：

    ```
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );
    ```

1. 將下列程式碼新增至類別 CMFC01Dlg 宣告中的 public 區段： 公用 CDialog。

    ```
    // delegate map
    BEGIN_DELEGATE_MAP( CMFC01Dlg )
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )
    END_DELEGATE_MAP()

    void OnClick( System::Object^ sender, System::EventArgs^ e );
    ```

1. 最後，新增的實作`OnClick`CMFC01Dlg.cpp 來：

    ```
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)
    {
        AfxMessageBox(_T("Button clicked"));
    }
    ```

## <a name="see-also"></a>另請參閱

[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)<br/>
[BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)<br/>
[END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)<br/>
[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)
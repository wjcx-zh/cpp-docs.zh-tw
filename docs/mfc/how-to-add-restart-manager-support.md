---
title: 如何：加入重新啟動管理員支援
ms.date: 11/04/2016
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
ms.openlocfilehash: 848cb3bb52ae13eb1b7798126becd13384fddeb6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625657"
---
# <a name="how-to-add-restart-manager-support"></a>如何：加入重新啟動管理員支援

重新開機管理員是新增至 Windows Vista 或更新版本作業系統 Visual Studio 的功能。 重新啟動管理員會在應用程式意外關閉或重新啟動時加入支援。 重新啟動管理員的行為，取決於應用程式的類型。 如果應用程式是文件編輯器，重新啟動管理員可讓應用程式自動儲存任何已開啟文件的狀態和內容，而且在意外關閉之後重新啟動應用程式。 如果應用程式不是文件編輯器，則重新啟動管理員預設會重新啟動應用程式，但不會儲存應用程式的狀態。

如果應用程式是 Unicode，則應用程式會在重新啟動之後顯示工作對話方塊。 如果是 ANSI 應用程式，則應用程式會顯示 Windows 訊息方塊。 此時，使用者可以選擇是否要還原自動儲存的文件。 如果使用者不要還原自動儲存的文件，則重新啟動管理員會捨棄暫存檔案。

> [!NOTE]
> 您可以覆寫重新啟動管理員的預設行為，以便儲存資料和重新啟動應用程式。

根據預設，當應用程式在具有 Windows Vista 或更新版本作業系統的電腦上執行時，使用中的 [專案] wizard 建立的 MFC 應用程式 Visual Studio 支援重新開機管理員。 如果您不想讓應用程式支援重新啟動管理員，可以在新的專案精靈中停用重新啟動管理員。

### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>將重新啟動管理員的支援加入現有的應用程式

1. 在 Visual Studio 中開啟現有的 MFC 應用程式。

1. 開啟主應用程式的原始程式檔。 根據預設，這是與應用程式同名的 .cpp 檔。 例如，MyProject 的主應用程式原始程式檔為 MyProject.cpp。

1. 尋找主應用程式的建構函式。 例如，專案若為 MyProject，建構函式則為 `CMyProjectApp::CMyProjectApp()`。

1. 將下面這行程式碼加入建構函式。

```
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;
```

1. 確保應用程式的 `InitInstance` 方法會呼叫其父 `InitInstance` 方法： [CWinApp::InitInstance](reference/cwinapp-class.md#initinstance) 或 `CWinAppEx::InitInstance`的功能。 `InitInstance`方法負責檢查*m_dwRestartManagerSupportFlags*參數。

1. 編譯並執行您的應用程式。

## <a name="see-also"></a>另請參閱

[CDataRecoveryHandler 類別](reference/cdatarecoveryhandler-class.md)<br/>
[CWinApp：： m_dwRestartManagerSupportFlags](reference/cwinapp-class.md#m_dwrestartmanagersupportflags)<br/>
[CWinApp 類別](reference/cwinapp-class.md)<br/>
[CWinApp：： m_nAutosaveInterval](reference/cwinapp-class.md#m_nautosaveinterval)<br/>
[CDocument：： OnDocumentEvent](reference/cdocument-class.md#ondocumentevent)

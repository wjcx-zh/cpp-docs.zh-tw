---
title: HOW TO：新增重新啟動管理員支援
ms.date: 11/04/2016
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
ms.openlocfilehash: 23f860c43c63e3153f4b87f8eaf05d61709af82f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389524"
---
# <a name="how-to-add-restart-manager-support"></a>HOW TO：新增重新啟動管理員支援

重新啟動管理員是功能加入至 Visual Studio for Windows Vista 或更新版本的作業系統。 重新啟動管理員會在應用程式意外關閉或重新啟動時加入支援。 重新啟動管理員的行為，取決於應用程式的類型。 如果應用程式是文件編輯器，重新啟動管理員可讓應用程式自動儲存任何已開啟文件的狀態和內容，而且在意外關閉之後重新啟動應用程式。 如果應用程式不是文件編輯器，則重新啟動管理員預設會重新啟動應用程式，但不會儲存應用程式的狀態。

如果應用程式是 Unicode，則應用程式會在重新啟動之後顯示工作對話方塊。 如果是 ANSI 應用程式，則應用程式會顯示 Windows 訊息方塊。 此時，使用者可以選擇是否要還原自動儲存的文件。 如果使用者不要還原自動儲存的文件，則重新啟動管理員會捨棄暫存檔案。

> [!NOTE]
>  您可以覆寫重新啟動管理員的預設行為，以便儲存資料和重新啟動應用程式。

根據預設，Visual Studio 中使用 [專案] 精靈所建立的 MFC 應用程式都支援重新啟動管理員，Windows Vista 或更新版本作業系統的電腦上執行的應用程式時。 如果您不想讓應用程式支援重新啟動管理員，可以在新的專案精靈中停用重新啟動管理員。

### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>將重新啟動管理員的支援加入現有的應用程式

1. Visual Studio 中開啟現有的 MFC 應用程式。

1. 開啟主應用程式的原始程式檔。 根據預設，這是與應用程式同名的 .cpp 檔。 例如，MyProject 的主應用程式原始程式檔為 MyProject.cpp。

1. 尋找主應用程式的建構函式。 例如，專案若為 MyProject，建構函式則為 `CMyProjectApp::CMyProjectApp()`。

1. 將下面這行程式碼加入建構函式。

```
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;
```

1. 請確定`InitInstance`應用程式的方法會呼叫其父代`InitInstance`方法：[Cwinapp:: Initinstance](../mfc/reference/cwinapp-class.md#initinstance)或`CWinAppEx::InitInstance`。 `InitInstance`方法負責檢查*m_dwRestartManagerSupportFlags*參數。

1. 編譯並執行您的應用程式。

## <a name="see-also"></a>另請參閱

[CDataRecoveryHandler 類別](../mfc/reference/cdatarecoveryhandler-class.md)<br/>
[CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)<br/>
[CWinApp 類別](../mfc/reference/cwinapp-class.md)<br/>
[CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)<br/>
[CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)

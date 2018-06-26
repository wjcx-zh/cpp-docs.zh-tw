---
title: 如何： 加入重新啟動管理員支援 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f11cc3258d577969807dd63c24c00da39652fff
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931269"
---
# <a name="how-to-add-restart-manager-support"></a>如何：加入重新啟動管理員支援

重新啟動管理員是一項功能加入至 Visual Studio Windows Vista 或更新版本的作業系統。 重新啟動管理員會在應用程式意外關閉或重新啟動時加入支援。 重新啟動管理員的行為，取決於應用程式的類型。 如果應用程式是文件編輯器，重新啟動管理員可讓應用程式自動儲存任何已開啟文件的狀態和內容，而且在意外關閉之後重新啟動應用程式。 如果應用程式不是文件編輯器，則重新啟動管理員預設會重新啟動應用程式，但不會儲存應用程式的狀態。  
  
 如果應用程式是 Unicode，則應用程式會在重新啟動之後顯示工作對話方塊。 如果是 ANSI 應用程式，則應用程式會顯示 Windows 訊息方塊。 此時，使用者可以選擇是否要還原自動儲存的文件。 如果使用者不要還原自動儲存的文件，則重新啟動管理員會捨棄暫存檔案。  
  
> [!NOTE]
>  您可以覆寫重新啟動管理員的預設行為，以便儲存資料和重新啟動應用程式。  
  
 根據預設，MFC 應用程式會建立使用中的專案精靈[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]Windows Vista 或更新版本作業系統的電腦上執行應用程式時，支援重新啟動管理員。 如果您不想讓應用程式支援重新啟動管理員，可以在新的專案精靈中停用重新啟動管理員。  
  
### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>將重新啟動管理員的支援加入現有的應用程式  
  
1.  在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]中開啟現有的 MFC 應用程式。  
  
2.  開啟主應用程式的原始程式檔。 根據預設，這是與應用程式同名的 .cpp 檔。 例如，MyProject 的主應用程式原始程式檔為 MyProject.cpp。  
  
3.  尋找主應用程式的建構函式。 例如，專案若為 MyProject，建構函式則為 `CMyProjectApp::CMyProjectApp()`。  
  
4.  將下面這行程式碼加入建構函式。  
  
 ```  
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;  
 ```  
  
5.  確保應用程式的 `InitInstance` 方法會呼叫其父 `InitInstance` 方法： [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) 或 `CWinAppEx::InitInstance`的功能。 `InitInstance`方法負責檢查*m_dwRestartManagerSupportFlags*參數。  
  
6.  編譯並執行您的應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [CDataRecoveryHandler 類別](../mfc/reference/cdatarecoveryhandler-class.md)   
 [CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)   
 [CWinApp 類別](../mfc/reference/cwinapp-class.md)   
 [CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)   
 [CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)


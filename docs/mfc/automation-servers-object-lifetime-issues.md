---
title: Automation 伺服程式： 物件存留期問題 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e27812c20a64f5472c29a66298bcdec30bf4ef2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341796"
---
# <a name="automation-servers-object-lifetime-issues"></a>Automation 伺服程式：物件存留期問題
當 Automation 用戶端建立或啟用 OLE 項目時，伺服器會傳遞該物件的指標給用戶端。 在用戶端建立透過呼叫 OLE 函式物件的參考[iunknown:: Addref](http://msdn.microsoft.com/library/windows/desktop/ms691379)。 這個參考是作用中直到用戶端呼叫[Iunknown](http://msdn.microsoft.com/library/windows/desktop/ms682317)。 (以 MFC 程式庫的 OLE 類別撰寫的用戶端應用程式不需要建立這些呼叫；架構也是如此)。這個 OLE 系統和伺服器本身可能會建立對物件的參考。 只要物件的外部參考仍然有效，伺服器就不應終結物件。  
  
 架構會維護的任何伺服器物件衍生自參考數目內部計數[CCmdTarget](../mfc/reference/ccmdtarget-class.md)。 當 Automation 用戶端或其他實體加入或釋放對物件的參考時，便會更新這個計數。  
  
 當參考計數變成 0 時，架構會呼叫虛擬函式[ccmdtarget:: Onfinalrelease](../mfc/reference/ccmdtarget-class.md#onfinalrelease)。 此函式的預設實作會呼叫**刪除**運算子來刪除此物件。  
  
 當外部用戶端擁有對應用程式物件的參考時，MFC 程式庫會提供額外的功能以控制應用程式行為。 除了維護對每個物件的參考計數之外，伺服器還會維護使用中物件的全域計數。 全域函式[AfxOleLockApp](../mfc/reference/application-control.md#afxolelockapp)和[AfxOleUnlockApp](../mfc/reference/application-control.md#afxoleunlockapp)更新應用程式的使用中物件計數。 如果這個計數不為零，則當使用者從系統功能表選擇 [關閉] 或從 [檔案] 功能表選擇 [結束] 時，不會結束應用程式。 相反地，應用程式的主視窗會被隱藏 (但不會被終結)，直到所有暫止的用戶端要求已經完成。 通常，`AfxOleLockApp` 和 `AfxOleUnlockApp` 會分別由支援 Automation 之類別的建構函式和解構函式呼叫。  
  
 當用戶端仍然擁有對物件的參考時，某些情況下會強制終止伺服器。 例如，伺服器所依存的資源可能變為無法使用，造成伺服器遇到錯誤。 使用者也可以關閉包含具有參考之其他應用程式物件的伺服器文件。  
  
 在 Windows SDK 中，請參閱`IUnknown::AddRef`和`IUnknown::Release`。  
  
## <a name="see-also"></a>另請參閱  
 [Automation 伺服程式](../mfc/automation-servers.md)   
 [AfxOleCanExitApp](../mfc/reference/application-control.md#afxolecanexitapp)


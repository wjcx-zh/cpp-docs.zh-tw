---
title: "TN071: MFC IOleCommandTarget 實作 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IOleCommandTarget
dev_langs: C++
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 43f97774036c42fa0f681a65e0a335f944daf09c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071：MFC IOleCommandTarget 實作
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 `IOleCommandTarget`介面可讓物件和其容器來分派彼此的命令。 比方說，物件的工具列可以包含命令的按鈕例如**列印**，**預覽列印**，**儲存**， `New`，和**縮放**. 如果這類物件已內嵌在容器，支援`IOleCommandTarget`，物件無法啟用其按鈕和轉送時使用者按下加以處理之容器的命令。 如果容器想要列印本身的內嵌的物件，它無法進行此要求傳送命令，以透過`IOleCommandTarget`內嵌物件的介面。  
  
 `IOleCommandTarget`是一個自動化類似的介面，因為它正由用戶端叫用伺服器上的方法。 不過，使用`IOleCommandTarget`儲存透過 Automation 介面進行呼叫，因為程式設計人員不需要使用通常高度耗費資源的額外負荷`Invoke`方法`IDispatch`。  
  
 在 MFC 中，`IOleCommandTarget`作用中的文件伺服程式會使用介面允許主動式文件容器來分派至伺服器的命令。 主動式文件伺服器類別， `CDocObjectServerItem`，會使用 MFC 介面對應 (請參閱[TN038: MFC/OLE IUnknown 實作](../mfc/tn038-mfc-ole-iunknown-implementation.md)) 來實作`IOleCommandTarget`介面。  
  
 `IOleCommandTarget`也實作於**COleFrameHook**類別。 **COleFrameHook**實作就地框架視窗功能未記載之的 MFC 類別編輯容器。 **COleFrameHook**也會使用 MFC 介面對應實作`IOleCommandTarget`介面。 **COleFrameHook**的實作`IOleCommandTarget`會轉送 OLE 命令給`COleDocObjectItem`-衍生主動式文件容器。 這可讓任何 MFC 使用中的文件容器，從包含主動式文件伺服器接收訊息。  
  
## <a name="mfc-ole-command-maps"></a>MFC OLE 命令對應  
 MFC 程式開發人員可以利用`IOleCommandTarget`使用 MFC OLE 命令對應。 OLE 命令對應就像訊息對應，因為它們可以用來將 OLE 命令對應至包含命令對應的類別成員函式。 若要這麼做，加上巨集來指定 OLE 指令群組，您想要處理的命令、 OLE 命令和命令 ID 的命令對應[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)收到 OLE 命令時要傳送的訊息。 MFC 也提供許多預先定義巨集標準 OLE 命令。 取得一份標準 OLE 原本設計的命令會使用與 Microsoft Office 應用程式，請參閱定義於 docobj.h OLECMDID 列舉型別。  
  
 包含命令對應的 OLE 的 MFC 應用程式所收到的 OLE 命令時，MFC 就會嘗試尋找 OLE 命令對應的應用程式中要求的命令的命令識別碼和命令群組。 如果找到相符項目， **WM_COMMAND**訊息分派至包含所要求的命令 ID 的命令對應的應用程式。 (請參閱描述`ON_OLECMD`下方。)如此一來，OLE 分派至應用程式的命令會變成**WM_COMMAND** mfc 的訊息。 **WM_COMMAND**透過使用 MFC 的標準應用程式的訊息對應會接著路由傳送訊息[命令路由](../mfc/command-routing.md)架構。  
  
 不同於訊息對應，MFC OLE 命令對應不會受到 ClassWizard。 MFC 開發人員必須將 OLE 命令對應支援和 OLE 命令對應項目以手動方式。 OLE 命令對應可以加入至 MFC 現用文件伺服程式中的任何類別中**WM_COMMAND**訊息路由的鏈結，在使用中文件是就地啟用作用中的容器中的時間。 這些類別包括應用程式的類別衍生自[CWinApp](../mfc/reference/cwinapp-class.md)， [CView](../mfc/reference/cview-class.md)， [CDocument](../mfc/reference/cdocument-class.md)，和[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)。 在使用中文件容器中，OLE 命令對應只會新增至[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)-衍生的類別。 此外，在主動式文件容器**WM_COMMAND**只能將訊息分派至的訊息對應中`COleDocObjectItem`-衍生的類別。  
  
## <a name="ole-command-map-macros"></a>OLE 命令對應巨集  
 您可以使用下列巨集將命令對應功能加入至類別：  
  
```  
 
DECLARE_OLECMD_MAP ()  
 
```  
  
 這個巨集則是放在類別宣告 （通常是在標頭檔） 包含的命令對應的類別。  
  
```  
 
BEGIN_OLECMD_MAP(
theClass  ,   baseClass)  
 
```  
  
 `theClass`  
 包含命令對應的類別名稱。  
  
 `baseClass`  
 包含命令對應之類別的基底類別的名稱。  
  
 這個巨集標記命令對應的開頭。 包含命令對應的類別的實作檔中使用這個巨集。  
  
```  
 
END_OLECMD_MAP()  
 
```  
  
 這個巨集標示命令對應的結尾。 包含命令對應的類別的實作檔中使用這個巨集。 這個巨集都必須依照**BEGIN_OLECMD_MAP**巨集。  
  
```  
 
ON_OLECMD(
pguid  ,   
olecmdid  ,
    id)  
 
```  
  
 `pguid`  
 OLE 命令的命令群組 GUID 的指標。 這個參數是**NULL**標準 OLE 命令群組。  
  
 *olecmdid*  
 OLE 所要叫用命令的命令識別碼。  
  
 `id`  
 識別碼**WM_COMMAND**訊息傳送到叫用此 OLE 命令時包含命令對應的應用程式。  
  
 使用`ON_OLECMD`您想要處理的命令對應，將 ole 項目中的巨集命令。 當收到 OLE 命令時，將轉換為指定**WM_COMMAND**訊息，並經由使用標準的 MFC 命令路由架構的應用程式的訊息對應。  
  
## <a name="example"></a>範例  
 下列範例示範如何將 OLE 命令處理功能加入至使用 MFC 的文件伺服器來處理[OLECMDID_PRINT](http://msdn.microsoft.com/library/windows/desktop/ms691264) OLE 命令。 這個範例假設您使用 AppWizard 產生 MFC 應用程式是使用中文件的伺服器。  
  
1.  在您`CView`-衍生類別的標頭檔案中加入`DECLARE_OLECMD_MAP`巨集，以在類別宣告。  
  
    > [!NOTE]
    >  使用`CView`-衍生類別，因為它是在使用中文件伺服器中的類別的其中一個**WM_COMMAND**訊息路由的鏈結。  
  
 ```  
    class CMyServerView : public CView  
 {  
    protected: // create from serialization only  
    CMyServerView();
DECLARE_DYNCREATE(CMyServerView)  
    DECLARE_OLECMD_MAP() 
 . . .  
 };  
 ```  
  
2.  中的實作檔`CView`-衍生的類別，新增`BEGIN_OLECMD_MAP`和`END_OLECMD_MAP`巨集：  
  
 ```  
    BEGIN_OLECMD_MAP(CMyServerView, CView)  
 
    END_OLECMD_MAP() 
 ```  
  
3.  若要處理的標準 OLE 列印命令，新增[ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd)巨集，以指定標準列印命令的 OLE 命令 ID 的命令對應和**ID_FILE_PRINT**如**WM_COMMAND**識別碼。 **ID_FILE_PRINT**是 AppWizard 產生 MFC 應用程式所使用的列印命令識別碼的標準：  
  
 ```  
    BEGIN_OLECMD_MAP(CMyServerView,
    CView)  
    ON_OLECMD(NULL,
    OLECMDID_PRINT,
    ID_FILE_PRINT) 
    END_OLECMD_MAP() 
 ```  
  
 請注意，其中一個標準 OLE 命令巨集，定義於 afxdocob.h，無法用於取代`ON_OLECMD`巨集因為**OLECMDID_PRINT**是標準 OLE 命令識別碼。 `ON_OLECMD_PRINT`巨集將會完成與相同的工作`ON_OLECMD`如上所示的巨集。  
  
 當容器應用程式將此伺服器傳送**OLECMDID_PRINT**命令的伺服器透過`IOleCommandTarget`介面，MFC 列印命令處理常式將會叫用在伺服器中，導致列印應用程式伺服器。 主動式文件容器的程式碼叫用在上述步驟中新增的列印命令看起來可能像這樣：  
  
```  
void CContainerCntrItem::DoOleCmd()  
{  
    IOleCommandTarget *pCmd = NULL;  
    HRESULT hr = E_FAIL;  
    OLECMD ocm={OLECMDID_PRINT, 0};  
 
    hr = m_lpObject->QueryInterface(IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if(FAILED(hr)) 
    return; 
 
    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if(SUCCEEDED(hr)&& (ocm.cmdf& OLECMDF_ENABLED))  
 { *//Command is available and enabled so call it  
    COleVariant vIn;  
    COleVariant vOut;  
    hr = pCmd->Exec(NULL, OLECMDID_PRINT,  
    OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);

    ASSERT(SUCCEEDED(hr));

 }  
    pCmd->Release();

} 
```  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)


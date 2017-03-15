---
title: "TN071：MFC IOleCommandTarget 實作 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IOleCommandTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IOleCommandTarget 介面"
  - "TN071"
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN071：MFC IOleCommandTarget 實作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 `IOleCommandTarget` 介面啟用物件及它們的容器，來分派命令。  例如，物件的工具列可能包含命令的按鈕 \(例如 \[**列印**\]、\[**預覽列印**\]、\[**儲存**\]、\[`New`\] 和 \[**縮放**\]。  如果這類物件內嵌在支援 `IOleCommandTarget` 的容器內，當使用者按一下它們時，物件可以啟用它的按鈕並轉送命令至容器以繼續處理。  如果容器要內嵌物件列印自己，可以透過內嵌物件的 `IOleCommandTarget` 介面傳送命令來達到這個要求。  
  
 `IOleCommandTarget` 是一個類似 Automation 的介面，因為它是在伺服器上提供用戶端叫用方法。  不過，因為程式設計人員無需使用耗費資源的 `IDispatch` 的 `Invoke` 方法，使用 `IOleCommandTarget` 可以節省透過 Automation 介面呼叫的負荷。  
  
 在 MFC 中，主動式文件伺服程式使用 `IOleCommandTarget` 介面來允許主動式文件容器分派命令至伺服器。  主動式文件伺服程式類別 `CDocObjectServerItem` 會使用 MFC 對應 \(請參閱 [TN038: MFC\/OLE IUnknown 實作](../mfc/tn038-mfc-ole-iunknown-implementation.md)\) 來實作 `IOleCommandTarget` 介面。  
  
 `IOleCommandTarget` 也實作在 **COleFrameHook** 類別中。  **COleFrameHook** 是一個未記載的 MFC 類別，實作就地編輯容器的框架視窗功能。  **COleFrameHook** 也使用 MFC 介面對應來實作 `IOleCommandTarget` 介面。  **COleFrameHook** 的 `IOleCommandTarget` 實作會傳送 OLE 命令給 `COleDocObjectItem` 衍生的主動式文件容器。  這可讓任何 MFC 主動式文件容器接收來自包含主動式文件伺服程式的訊息。  
  
## MFC OLE 命令對應  
 使用 MFC OLE 命令對應， MFC 開發人員可以利用 `IOleCommandTarget`。  OLE 命令對應與訊息對應類似，因為它們可以用來將 OLE 命令對應到包含命令對應的類別的成員函式。  若要執行這項工作，將巨集放在命令對應以指定您要處理的 OLE 命令組、OLE 命令和當接收到 OLE 命令時要傳送 [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) 訊息的命令 ID。  MFC 也為標準 OLE 命令提供多個預先定義巨集。  如需最初設計為與 Microsoft Office 應用程式一起使用的標準 OLE 命令的清單，請參閱 OLECMDID 列舉，定義在 docobj.h 中。  
  
 當 OLE 命令由包含 OLE 命令對應的 MFC 應用程式接收時， MFC 會嘗試找到命令 ID 和應用程式的 OLE 命令對應之要求命令的命令群組。  如果找到符合的項目， **WM\_COMMAND** 訊息會被分派至包含具有要求命令之 ID 的命令對應的應用程式。\(請參閱下面 `ON_OLECMD` 的說明\)。如此一來，分派給應用程式的 OLE 命令會由 MFC 變成 **WM\_COMMAND** 訊息。  **WM\_COMMAND** 訊息接著會使用 MFC 標準 [命令路由](../mfc/command-routing.md) 結構傳遞至應用程式的訊息對應。  
  
 不同於訊息對應， MFC OLE 命令對應不為 ClassWizard 支援。  MFC 程式開發人員必須手動加入 OLE 命令對應支援和 OLE 命令對應項目。  當現用文件是在容器就地使用中時，OLE 命令對應可被加入至 **WM\_COMMAND** 訊息路由鏈結的任何類別的 MFC 主動式文件伺服程式。  這些類別包括衍生自 [CWinApp](../mfc/reference/cwinapp-class.md)、[CView](../mfc/reference/cview-class.md)、[CDocument](../mfc/reference/cdocument-class.md) 和 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) 的應用程式的類別。  在主動式文件容器中， OLE 命令對應只能加入至 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md) 衍生的類別。  此外，在主動式文件容器中，**WM\_COMMAND** 訊息只會被分派至 `COleDocObjectItem` 衍生的類別中的訊息對應。  
  
## OLE 命令對應巨集  
 使用下列巨集將命令對應功能加入至類別：  
  
```  
  
DECLARE_OLECMD_MAP ()  
  
```  
  
 這個巨集在包含命令對應的類別的類別宣告 \(通常是在標頭檔\) 中。  
  
```  
  
BEGIN_OLECMD_MAP(  
theClass  
,   
baseClass  
)  
  
```  
  
 `theClass`  
 包含命令對應的類別名稱。  
  
 `baseClass`  
 包含命令對應的類別之基底類別名稱。  
  
 這個巨集標記命令對應的開頭。  為包含命令對應的類別在實作檔中使用這個巨集。  
  
```  
  
END_OLECMD_MAP()  
  
```  
  
 這個巨集標記命令對應的結尾。  為包含命令對應的類別在實作檔中使用這個巨集。  這個巨集必須一律遵循 **BEGIN\_OLECMD\_MAP** 巨集。  
  
```  
  
ON_OLECMD(  
pguid  
,   
olecmdid  
,   
id  
)  
  
```  
  
 `pguid`  
 對 OLE 命令群組之 GUID 的指標。  標準 OLE 命令群組的這個參數是 **NULL** 。  
  
 *olecmdid*  
 要叫用的命令的 OLE 命令 ID。  
  
 `id`  
 當 OLE 命令被叫用時，要傳送給包含命令對應的應用程式之 **WM\_COMMAND** 訊息的 ID。  
  
 在命令對應使用 `ON_OLECMD` 巨集加入您要處理的 OLE 命令的項目。  當接收到 OLE 命令時，它們會使用標準 MFC 命令傳送結構，轉換為指定的 **WM\_COMMAND** 訊息並透過應用程式的訊息對應路由傳送。  
  
## 範例  
 下列範例示範如何將 OLE 命令處理功能加入至 MFC 主動式文件伺服程式，以處理 [OLECMDID\_PRINT](http://msdn.microsoft.com/library/windows/desktop/ms691264) OLE 命令。  此範例會假設您使用 AppWizard 來產生是主動式文件伺服程式的 MFC 應用程式。  
  
1.  在您的 `CView` 衍生類別的標頭檔，加入 `DECLARE_OLECMD_MAP` 巨集至類別宣告。  
  
    > [!NOTE]
    >  請使用 `CView` 衍生類別，因為它是一個在 **WM\_COMMAND** 訊息路由鏈結的主動式文件伺服程式的其中一個類別。  
  
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
  
2.  在 `CView` 衍生類別的實作檔中，加入 `BEGIN_OLECMD_MAP` 和 `END_OLECMD_MAP` 巨集：  
  
    ```  
    BEGIN_OLECMD_MAP(CMyServerView, CView)  
  
    END_OLECMD_MAP()  
    ```  
  
3.  若要處理標準 OLE 列印命令，請為標準列印命令加入 [ON\_OLECMD](../Topic/ON_OLECMD.md) 巨集至指定的 OLE 命令 ID，以及為 **WM\_COMMAND** ID 加入 **ID\_FILE\_PRINT**。  **ID\_FILE\_PRINT** 是 AppWizard 產生的 MFC 應用程式使用的標準列印命令 ID：  
  
    ```  
    BEGIN_OLECMD_MAP(CMyServerView, CView)  
       ON_OLECMD(NULL,OLECMDID_PRINT,ID_FILE_PRINT)  
    END_OLECMD_MAP()  
    ```  
  
 因為 **OLECMDID\_PRINT** 是標準 OLE 命令 ID，請注意定義在 afxdocob.h 的一個標準 OLE 命令巨集，可能用來取代 `ON_OLECMD` 巨集。  `ON_OLECMD_PRINT` 巨集將與 `ON_OLECMD` 巨集上述相同的工作。  
  
 當容器應用程式透過伺服器的 `IOleCommandTarget` 介面傳送 **OLECMDID\_PRINT** 命令給伺服器時，MFC 列印命令處理常式會在伺服器內被叫用，使伺服器列印應用程式。  在上述步驟中，用來叫用列印命令的主動式文件容器而加入的程式碼看起來可能如下：  
  
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
   if(SUCCEEDED(hr) && (ocm.cmdf & OLECMDF_ENABLED))  
   {  
      //Command is available and enabled so call it  
      COleVariant vIn;  
      COleVariant vOut;  
      hr = pCmd->Exec(NULL, OLECMDID_PRINT,  
 OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);  
      ASSERT(SUCCEEDED(hr));  
   }  
   pCmd->Release();  
}  
```  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)
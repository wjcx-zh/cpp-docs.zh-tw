---
title: "TN041：MFC/OLE1 移轉到 MFC/OLE 2 | Microsoft Docs"
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
  - "vc.mfc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "將 OLE1 轉換為 OLE2"
  - "將 OLE1 移轉至 OLE2"
  - "移轉 [C++], OLE1 to OLE2"
  - "OLE1 [C++]"
  - "OLE2 [C++]"
  - "將 OLE1 移植至 OLE2"
  - "TN041"
  - "升級 Visual C++ 應用程式, OLE1 to OLE2"
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN041：MFC/OLE1 移轉到 MFC/OLE 2
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
## 與移轉相關的一般問題。  
 其中一個在 MFC 2.5 的 2 類別 \(和以上\) 的 OLE 的設計目標是保留放在適當位置的許多相同結構在 OLE 1.0 支援的 MFC 2.0。  因此，許多MFC 2.0 中的相同 OLE 類別仍存在於這個版本的 MFC中 \(`COleDocument`、 `COleServerDoc`、 `COleClientItem`， `COleServerItem`\)。  此外，許多這些類別中的 API 完全相同。  不過，OLE 2 與 OLE 1.0 大幅不同，因此您可以預期特定詳細資料已變更。  如果您熟悉 MFC 2.0 ' s OLE1 支援，那麼您使用 MFC's 2.0 支援將非常自在。  
  
 如果您使用現有的 MFC\/OLE1 應用程式並將 OLE 2 功能給它，您應先閱讀這個注意事項。  這個注意事項包括當移植 OLE1 功能到 MFC\/OLE 2 時您可能遇到的一些常見問題，然後討論移植在 MFC 中的兩個應用程式 2.0 ：MFC OLE 範例 [OCLIENT](../top/visual-cpp-samples.md) 和 [HIERSVR](../top/visual-cpp-samples.md) 發現的問題。  
  
## MFC 文件\/檢視架構是很重要的  
 如果您的應用程式不使用 MFC 的文件\/檢視架構，且您要將 OLE 2 支援加入至您的應用程式，現在就是移至文件\/檢視的時候了。  一旦您的應用程式使用 MFC 內建結構與元件，許多 MFC 的 OLE 2 類別的優點將實現。  
  
 不使用 MFC 結構實作一個伺服器或容器是可行的，不過並不建議。  
  
## 使用 MFC 實作代替您  
 MFC 「可能會實作」類別，例如 `CToolBar`、 `CStatusBar`，及 `CScrollView` 具有 OLE 2 支援的內建特殊情況程式碼。  因此，如果您在應用程式中使用這些類別將受益於工作放置到使它們 OLE 明確。  同樣地，可能為「捲軸其中」類別在此處為這些目的，但是並不建議。  如果您需要實作類似的功能， MFC 原始程式碼為涉及某些 OLE 的出色點絕佳的參考 \(特別是就地啟用方面\)。  
  
## 檢查 MFC 範例程式碼  
 包含 OLE 功能的 MFC 範例。  每一個這些應用程式會從不同的角度實作 OLE：  
  
-   [HIERSVR](../top/visual-cpp-samples.md) 表示主要做為伺服器應用程式。  在 MFC 2.0 中做為 MFC\/OLE1 應用程式且移植至移植至 MFC\/OLE 2 然後延伸了會實作許多 OLE 功能適用於 OLE 2。  
  
-   [OCLIENT](../top/visual-cpp-samples.md) 這是獨立的容器應用程式，會示範許多從容器位置的 OLE 功能。  從 MFC 2.0 也移植，然後加以擴充支援許多進階 OLE 功能，例如自訂剪貼簿格式並連結至內嵌項目。  
  
-   [DRAWCLI](../top/visual-cpp-samples.md) 應用程式實作 OLE 容器支援很像 OCLIENT，不過，它是在現有的物件導向繪圖程式架構中使用。  顯示您要實作 OLE 容器支援並與您現有的應用程式整合。  
  
-   [SUPERPAD](../top/visual-cpp-samples.md) 這個應用程式，以及為細微的獨立應用程式，也是 OLE 伺服器。  它所實作的伺服器支援相當極簡的。  特別值得注意的是如何使用 OLE 剪貼簿服務資料複製到剪貼簿，不過，使用內建功能視窗「編輯」控制項實作剪貼簿貼上功能。  這顯示傳統 Windows 應用程式開發介面使用方式以及整合新的 OLE API 有趣的混合使用。  
  
 如需範例應用程式的詳細資訊，請參閱「MFC 範例說明」。  
  
## 案例研究：從 MFC 2.0 的 OCLIENT  
 如先前所述，[OCLIENT](../top/visual-cpp-samples.md) 在 MFC 2.0 中並已使用 MFC\/OLE1 的 OLE。  這個應用程式一開始轉換使用 MFC\/OLE 2 類別的步驟如下。  在初始連接埠達到較佳說明 MFC\/OLE 類別後，許多功能加入。  這些功能不會涵蓋這裡；需這些進階功能的詳細資訊請參閱這個範例如。  
  
> [!NOTE]
>  編譯器錯誤及以 Visual C\+\+ 2.0 創建的逐步程序。  特定的錯誤訊息和位置可能已經搭配 Visual C\+\+ 4.0 變更，不過，概念性資訊維持有效。  
  
## 啟動並運作  
 移植 OCLIENT 範例到 MFC\/OLE 使用的方法一開始會建置並修正明顯會發生的編譯器錯誤。  如果您採用 MFC 2.0 的 OCLIENT 範例並編譯它在 MFC 中這個版本中，您會發現未解決大部分的錯誤。  錯誤會依照其出現的順序如下。  
  
## 編譯並更正錯誤  
  
```  
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters  
```  
  
 第一個錯誤涉及 `COleClientItem::Draw`。  在 MFC\/OLE1 它比 MFC\/OLE 版本採用了更多參數。  額外參數通常不需要且通常是 null \(如本範例中\)。  當繪製的 CDC 是中繼檔 DC時，MFC 的這個版本會自動判斷 lpWBounds 的值。  此外，因為此種架構會建立一個從「屬性 DC」傳遞的 pDC，pFormatDC 不再是必須的。  因此修正這個問題，請移除兩個額外空參數至繪製呼叫。  
  
```  
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier  
\oclient\mainview.cpp(273) : error C2057: expected constant expression  
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '  
```  
  
 上述的錯誤由在 MFC\/OLE1 中所有的 **COleClientItem::CreateXXXX** 函式需要一個唯一的名字傳遞來表示項目所造成。  這是基礎 OLE 應用程式開發介面的要求。  這在 MFC\/OLE 2 中不是必要的，因為 OLE 2 不使用 DDE 做為基礎的通訊機制 \(名稱 DDE 互動\)。  若要解決這個問題，您可以移除 **CreateNewName** 函式以及所有指向它的參考。  藉由將游標放在呼叫上並按 F1，尋找什麼是每個 MFC\/OLE 函式在這個版本所期望的是簡單的。  
  
 相當不同的另一個區域是 OLE 2 剪貼簿處理。  使用 OLE1，您使用了與剪貼簿互動的 Windows 剪貼簿 API 。  搭配 OLE 2 以不同的機制完成。  MFC\/OLE1 API 假設在複製 `COleClientItem` 物件至剪貼簿前，剪貼簿是開啟的。  這不是必要的且將讓所有 MFC\/OLE 剪貼簿作業失敗。  當您編輯程式碼移除 **CreateNewName** 的相依性時，您也應該移除開啟和關閉 Windows 剪貼簿的程式碼。  
  
```  
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier  
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function  
\oclient\mainview.cpp(344) : error C2057: expected constant expression  
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'  
```  
  
 由 **CMainView::OnInsertObject** 處理常式所造成的這些錯誤。  處理「插入新物件」命令是事件變更相當多的另一個區域。  在這種情況下，與 AppWizard 提供之原始實作簡易合併成新的 OLE 容器應用程式是最容易的。  實際上，這是可移植至其他應用程式的技術。  在 MFC\/OLE1 中，您可以呼叫 **AfxOleInsertDialog** 函式顯示「插入物件」對話方塊。  在這個版本，您建構 **COleInsertObject** 對話物件並且呼叫 `DoModal`。  此外，新的 OLE 項目搭配 **CLSID** 建立而不是類別名稱字串。  最終結果應該看起來像這樣  
  
```  
COleInsertDialog dlg;  
if (dlg.DoModal() != IDOK)  
    return;  
  
BeginWaitCursor();  
  
CRectItem* pItem = NULL;  
TRY  
{  
    // First create the C++ object  
    pItem = GetDocument()->CreateItem();  
    ASSERT_VALID(pItem);  
  
    // Initialize the item from the dialog data.  
    if (!dlg.CreateItem(pItem))  
        AfxThrowMemoryException();  
           // any exception will do  
    ASSERT_VALID(pItem);  
  
    // run the object if appropriate  
    if (dlg.GetSelectionType() ==   
            COleInsertDialog::createNewItem)  
        pItem->DoVerb(OLEIVERB_SHOW, this);  
  
    // update right away  
    pItem->UpdateLink();  
    pItem->UpdateItemRectFromServer();  
  
    // set selection to newly inserted item  
    SetSelection(pItem);  
    pItem->Invalidate();  
}  
CATCH (CException, e)  
{    
    // clean up item  
    if (pItem != NULL)  
        GetDocument()->DeleteItem(pItem);  
  
    AfxMessageBox(IDP_FAILED_TO_CREATE);  
}  
END_CATCH  
  
EndWaitCursor();  
```  
  
> [!NOTE]
>  為您的應用程式插入新物件可能不同\):  
  
 包含 \<afxodlgs.h\> 也是必要的，包含 **COleInsertObject** 對話方塊類別的宣告以及 MFC 所提供的其他標準對話方塊。  
  
```  
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier  
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters  
```  
  
 這些錯誤是由某一 OLE1 常數在 OLE 2 中已變更的事實所造成，即使在概念方面它們相同。  在這種情況下 **OLEVERB\_PRIMARY** 變更為 `OLEIVERB_PRIMARY`。  在 OLE1 和 OLE2，當使用者連按兩下項目時，主要動詞通常由容器執行。  
  
 此外， `DoVerb` 現在接受額外參數—對檢視 \(`CView`的指標\*\)。  這個參數只用來實作「編輯的視覺」\(或就地啟用\)。  現在您設定 null 參數，因為您目前不實作這個功能。  
  
 若要確定，架構不會嘗試以就地啟動，您應該覆寫 `COleClientItem::CanActivate` 如下：  
  
```  
BOOL CRectItem::CanActivate()  
{  
    return FALSE;  
}  
  
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier  
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function  
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier  
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function  
```  
  
 在 MFC\/OLE1， **COleClientItem::GetBounds** 和 **SetBounds** 是用來質詢和管理項目的範圍 \( **left** 和 **top** 成員永遠為零\)。  在 MFC\/OLE 2 這由 `COleClientItem::GetExtent` 和 `SetExtent`更直接支援，涉及 **SIZE** 或 `CSize` 。  
  
 您的新 SetItemRectToServer 的程式碼和 UpdateItemRectFromServer 呼叫如下所示：  
  
```  
BOOL CRectItem::UpdateItemRectFromServer()  
{  
   ASSERT(m_bTrackServerSize);  
   CSize size;  
   if (!GetExtent(&size))  
      return FALSE;    // blank  
  
   // map from HIMETRIC to screen coordinates  
   {  
      CClientDC screenDC(NULL);  
      screenDC.SetMapMode(MM_HIMETRIC);  
      screenDC.LPtoDP(&size);  
   }  
   // just set the item size  
   if (m_rect.Size() != size)  
   {  
      // invalidate the old size/position  
      Invalidate();  
      m_rect.right = m_rect.left + size.cx;  
      m_rect.bottom = m_rect.top + size.cy;  
      // as well as the new size/position  
      Invalidate();  
   }  
   return TRUE;  
}  
  
BOOL CRectItem::SetItemRectToServer()  
{  
   // set the official bounds for the embedded item  
   CSize size = m_rect.Size();  
   {  
      CClientDC screenDC(NULL);  
      screenDC.SetMapMode(MM_HIMETRIC);  
      screenDC.DPtoLP(&size);  
   }  
   TRY  
   {  
      SetExtent(size);  // may do a wait  
   }  
   CATCH(CException, e)  
   {  
      return FALSE;  // links will not allow SetBounds  
   }  
   END_CATCH  
   return TRUE;  
}  
  
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'  
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier  
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function  
```  
  
 在 MFC\/OLE1 從容器同步處理 API 呼叫至伺服器被*模擬*，因為 OLE1 在許多情況下原本就是繼承自非同步。  檢查是否有未完成的非同步呼叫過程中需要在處理使用者的命令。  MFC\/OLE1 為如此做提供 **COleClientItem::InWaitForRelease** 函式。  在 MFC\/OLE 2 這不是必要的，因此您可以同時移除 OnCommand 中 CMainFrame 的覆寫。  
  
 此時 OCLIENT 將編譯和連結。  
  
## 其他必要的變更  
 不過有一些不做會防止執行 OCLIENT 的事。  現在最好解決這些問題而非之後。  
  
 首先，初始化 OLE 程式庫是必要的。  這是由從 `InitInstance` 呼叫 **AfxOleInit** 完成：  
  
```  
if (!AfxOleInit())  
{  
  AfxMessageBox("Failed to initialize OLE libraries");  
  return FALSE;  
}  
```  
  
 它也是很好的檢查參數清單變更的虛擬函式。  一個這類函式是 `COleClientItem::OnChange`，以覆寫每個 MFC\/OLE 容器應用程式。  藉由查看線上說明，您會看到一個額外的「DWORD dwParam」已加入。  新的 CRectItem::OnChange 如下所示：  
  
```  
void   
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)  
{  
  if (m_bTrackServerSize &&  
        !UpdateItemRectFromServer())  
  {  
    // Blank object  
    if (wNotification == OLE_CLOSED)  
    {  
      // no data received for the object - destroy it  
      ASSERT(!IsVisible());  
      GetDocument()->DeleteItem(this);  
      return;   // no update (item is gone now)  
    }  
  }  
  if (wNotification != OLE_CLOSED)  
      Dirty();  
  Invalidate();  // any change will cause a redraw  
}  
```  
  
 在 MFC\/OLE1 中，容器應用程式衍生自 **COleClientDoc** 的文件類別。  在 MFC\/OLE 2中， `COleDocument` 取消並取代了這個類別 \(這個新的組織可以輕鬆建立容器\/伺服器應用程式\)。  具有 `#define` 對應 **COleClientDoc** 至 `COleDocument` 來簡化 MFC\/OLE1 應用程式到 MFC\/OLE 2 的移植，例如 OCLIENT。  由 **COleClientDoc** 提供的`COleDocument` 未提供的其中一項功能是標準命令訊息對應項目。  如此一來，讓也使用 `COleDocument` \(間接\)的伺服器應用程式，不會載入其負荷這些命令處理常式，除非它們是容器\/伺服器應用程式。  您還需要將下列項目加入至CMainDoc 訊息對應：  
  
```  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)  
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)  
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)  
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)  
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)  
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)  
```  
  
 所有這些命令的實作在 `COleDocument`中，這是文件的基底類別。  
  
 此時， OCLIENT 是一個功能 OLE 容器應用程式。  可以插入任何型別項目 \(OLE1 或 OLE 2\)。  Since the necessary code to enable in\-place activation is not implemented, items are edited in a separate window much like with OLE1.  下節將討論必要變更啟用就地編輯 \(有時稱為「編輯的視覺」\)。  
  
## 加入「視覺化編輯」  
 其中一個 OLE 有趣的功能是就地編輯啟動 \(或「視覺化編輯」\)。  這項功能可讓伺服器應用程式接收容器的使用者介面 \(UI\) 的區段，為使用者提供了更完善的編輯介面。  若要實作就地啟動到 OCLIENT，某些特殊資源需要加入，以及一些額外的程式碼。  AppWizard 通常提供這些資源和程式碼—實際上，許多此程式碼直接從新 AppWizard 應用程式搭配「容器」支援被借用了。  
  
 首先，當有就地啟動項目時，加入會使用的功能表資源是必要的。  您可以複製 IDR\_OCLITYPE 資源和移除所有除了檔案及 Windows 快顯之外，來在 Visual C\+\+ 建立這個額外的功能表資源。  兩個分隔線插入在檔案和 Windows 快顯之間來表示群組的分隔 \(應該看到類似：檔案&#124;&#124;視窗\)。  如需這些分隔符號的意義及伺服器和容器功能表如何合併的詳細資訊，請參閱*OLE 2 類別* 中的「功能表和資源：功能表合併」。  
  
 一旦您將這些功能表建立，您必須告知架構。  這是透過呼叫文件範本的 `CDocTemplate::SetContainerInfo` 完成，然後再將它加入至您的 InitInstance 之前的文件範本清單。  註冊文件樣板建立新的程式碼如下所示：  
  
```  
CDocTemplate* pTemplate = new CMultiDocTemplate(  
    IDR_OLECLITYPE,  
    RUNTIME_CLASS(CMainDoc),  
    RUNTIME_CLASS(CMDIChildWnd),    // standard MDI child frame  
    RUNTIME_CLASS(CMainView));  
pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);  
AddDocTemplate(pTemplate);  
```  
  
 IDR\_OLECLITYPE\_INPLACE 資源是 Visual C\+\+ 建立的特殊就地資源。  
  
 若要啟用就地啟動，在 `CView` 的某些作業 \(CMainView\) 衍生類別以及 `COleClientItem` 衍生類別 \(CRectItem\) 進行變更。  AppWizard 提供這些覆寫，而且大部分的實作會直接來自預設 AppWizard 應用程式。  
  
 在第一個步驟中這個通訊埠，透過覆寫 `COleClientItem::CanActivate`完全停用就地啟用。  應該取消這個覆寫允許就地啟動。  此外，NULL 則傳遞至 `DoVerb` 的所有呼叫 \(有兩個\)，因為對就地啟動來說，提供檢視才是必要的。  完整實作就地啟動，傳入 `DoVerb` 呼叫的正確檢視是必要的。  這些呼叫的其中一個在 **CMainView::OnInsertObject** 中：  
  
```  
pItem->DoVerb(OLEIVERB_SHOW, this);  
```  
  
 另一個在 **CMainView::OnLButtonDblClk** 中：  
  
```  
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);  
```  
  
 覆寫 `COleClientItem::OnGetItemPosition` 是必要的。  當項目就地啟動時，這個會告知伺服器將其視窗相對於容器的視窗。  對於 OCLIENT，實作起來都非常簡單：  
  
```  
void CRectItem::OnGetItemPosition(CRect& rPosition)  
{  
    rPosition = m_rect;  
}  
```  
  
 大部分伺服器也實作所謂的「就地調整」。當使用者編輯項目時，這可讓伺服器視窗調整大小和移動。  容器必須參與這個動作，因為移動或調整視窗的大小通常會影響在容器文件中的位置和大小。  OCLIENT 的實作同步處理新的位置和大小的 m\_rect 維護的矩形內部。  
  
```  
BOOL CRectItem::OnChangeItemPosition(const CRect& rectPos)  
{  
    ASSERT_VALID(this);  
  
    if (!COleClientItem::OnChangeItemPosition(rectPos))  
        return FALSE;  
  
    Invalidate();  
    m_rect = rectPos;  
    Invalidate();  
    GetDocument()->SetModifiedFlag();  
  
    return TRUE;  
}  
```  
  
 此時，會讓足夠的程式碼讓項目就地啟動和處理調整大小和移動項目，當它啟用中時，不過，程式碼不會允許使用者結束編輯工作階段。  雖然有些伺服器會處理 Esc 鍵提供這項功能，建議容器提供兩種停用項目：\(1\) 藉由按一下項目以外的項目以及 \(2\) 藉由按 Esc 鍵。  
  
 對於 Esc 鍵，用對應 VK\_ESCAPE 鍵至命令的 Visual C\+\+ 加入一個快速鍵，ID\_CANCEL\_EDIT 加入資源。  這個命令的處理常式如下：  
  
```  
// The following command handler provides the standard  
// keyboard user interface to cancel an in-place  
// editing session.void CMainView::OnCancelEdit()  
{  
    // Close any in-place active item on this view.  
    COleClientItem* pActiveItem =   
        GetDocument()->GetInPlaceActiveItem(this);  
    if (pActiveItem != NULL)  
        pActiveItem->Close();  
    ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);  
}  
```  
  
 若要處理使用者在專案外部按一下的情況，加入下列程式碼至 **CMainView::SetSelection** 的開頭：  
  
```  
if (pNewSel != m_pSelection || pNewSel == NULL)  
{  
    COleClientItem* pActiveItem =   
        GetDocument()->GetInPlaceActiveItem(this);  
    if (pActiveItem != NULL && pActiveItem != pNewSel)  
        pActiveItem->Close();  
}  
  
```  
  
 當項目是就地啟動時，它應該具有焦點。  若要判斷此為您處理 OnSetFocus 的情況，當您檢視接收焦點時，讓焦點永遠傳輸至現用項目：  
  
```  
// Special handling of OnSetFocus and OnSize are required   
// when an object is being edited in-place.  
void CMainView::OnSetFocus(CWnd* pOldWnd)  
{  
    COleClientItem* pActiveItem =   
        GetDocument()->GetInPlaceActiveItem(this);  
    if (pActiveItem != NULL &&  
    pActiveItem->GetItemState() == COleClientItem::activeUIState)  
    {  
        // need to set focus to this item if it is same view  
        CWnd* pWnd = pActiveItem->GetInPlaceWindow();  
        if (pWnd != NULL)  
        {  
            pWnd->SetFocus();  // don't call the base class  
            return;  
        }  
    }  
  
    CView::OnSetFocus(pOldWnd);  
}  
```  
  
 當檢視調整大小時，您需要通知現用項目裁剪方框已變更。  若要做到這點，您要提供 `OnSize`的處理常式：  
  
```  
void CMainView::OnSize(UINT nType, int cx, int cy)  
{  
    CView::OnSize(nType, cx, cy);  
    COleClientItem* pActiveItem =   
        GetDocument()->GetInPlaceActiveItem(this);  
    if (pActiveItem != NULL)  
        pActiveItem->SetItemRects();  
}  
```  
  
## 案例研究：MFC 2.0 的 HIERSVR  
 [HIERSVR](../top/visual-cpp-samples.md) 在 MFC 2.0 也包含並已使用 MFC\/OLE1 實作 OLE。  這個附註簡要說明這個應用程式一開始轉換使用 MFC\/OLE 2 類別的步驟。  在初始連接埠達到較佳說明 MFC\/OLE 2 類別後，許多功能加入。  這些功能不會涵蓋這裡；需這些進階功能的詳細資訊請參閱這個範例。  
  
> [!NOTE]
>  編譯器錯誤及以 Visual C\+\+ 2.0 創建的逐步程序。  特定的錯誤訊息和位置可能已經搭配 Visual C\+\+ 4.0 變更，不過，概念性資訊維持有效。  
  
## 啟動並運作  
 移植 HIERSVR 範例到 MFC\/OLE 使用的方法一開始會建置並修正明顯會發生的編譯器錯誤。  如果您接受從 MFC 2.0 的 HIERSVR 範例並編譯它在 MFC 中這個版本中，您會發現未解析的許多錯誤 \(雖然有更多與 OCLIENT 範例\)。  錯誤會依照其通常出現的順序如下。  
  
## 編譯並更正錯誤  
  
```  
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'  
```  
  
 這第一個錯誤指出 `InitInstance` 函式中完整問題的伺服器。  對於 OLE 伺服器所需的初始化可能是您必須對 MFC\/OLE1 應用程式取得它執行的其中一個最大的變更。  要做最好的做法是查看 AppWizard 為 OLE 伺服器建立和修改您的程式碼屬性。  這邊要記住的幾點：  
  
 藉由呼叫 **AfxOleInit** 初始化 OLE 程式庫是必要的。  
  
 在文件樣板物件上呼叫 SetServerInfo 設定您無法搭配 `CDocTemplate` 建構子設定的伺服器資源處理常式及執行階段類別資訊。  
  
 如果 \/Embedding 位於命令列，不要顯示主視窗應用程式。  
  
 您將需要文件的 **GUID** 。  這就是資料型別 \(128 位元\) 唯一識別項。  AppWizard 會為您建立一個—如此，如果您使用這個技術會描述在這裡複製新 AppWizard 產生的伺服器應用程式的新程式碼，您可以從該應用程式的 GUID「竊取」。  否則，您可以在 Bin 目錄中使用 GUIDGEN.EXE 公用程式。  
  
 藉由呼叫 `COleTemplateServer::ConnectTemplate` 「連線」您的 `COleTemplateServer` 物件和文件範本是必要的。  
  
 當應用程式獨立執行時，請更新系統登錄。  如此一來，如果使用者移動您的應用程式的 .EXE，從新位置執行它將更新 Windows 系統註冊資料庫指向新位置。  
  
 在套用所有這些以 AppWizard 為 `InitInstance` 所建立為基礎的變更之後，HIERSVR 的 `InitInstance` \(及相關的 GUID\) 應該看起來如下：:  
  
```  
// this is the GUID for HIERSVR documents  
static const GUID BASED_CODE clsid =  
    { 0xA0A16360L, 0xC19B, 0x101A, { 0x8C, 0xE5, 0x00, 0xDD, 0x01, 0x11, 0x3F, 0x12 } };  
  
/////////////////////////////////////////////////////////////////////////////  
// COLEServerApp initialization  
  
BOOL COLEServerApp::InitInstance()  
{  
    // OLE 2 initialization  
    if (!AfxOleInit())  
    {  
        AfxMessageBox("Initialization of the OLE failed!");  
        return FALSE;  
    }  
  
    // Standard initialization  
    LoadStdProfileSettings(); // Load standard INI file options   
  
    // Register document templates  
    CDocTemplate* pDocTemplate;  
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,  
        RUNTIME_CLASS(CServerDoc),     
        RUNTIME_CLASS(CMDIChildWnd),  
        RUNTIME_CLASS(CServerView));  
    pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);  
    AddDocTemplate(pDocTemplate);  
  
    // create main MDI Frame window  
    CMainFrame* pMainFrame = new CMainFrame;  
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))  
        return FALSE;  
    m_pMainWnd = pMainFrame;  
  
    SetDialogBkColor();   // gray look  
  
    // enable file manager drag/drop and DDE Execute open  
    m_pMainWnd->DragAcceptFiles();  
    EnableShellOpen();  
  
    m_server.ConnectTemplate(clsid, pDocTemplate, FALSE);  
    COleTemplateServer::RegisterAll();  
  
    // try to launch as an OLE server  
    if (RunEmbedded())  
    {  
        // "short-circuit" initialization -- run as server!  
        return TRUE;  
    }  
    m_server.UpdateRegistry();  
    RegisterShellFileTypes();  
  
    // not run as OLE server, so show the main window  
    if (m_lpCmdLine[0] == '\0')  
    {  
        // create a new (empty) document  
        OnFileNew();  
    }  
    else  
    {  
        // open an existing document  
        OpenDocumentFile(m_lpCmdLine);  
    }  
  
    pMainFrame->ShowWindow(m_nCmdShow);  
    pMainFrame->UpdateWindow();  
  
    return TRUE;  
}  
```  
  
 您會發現上述程式碼參考新的資源 ID， IDR\_HIERSVRTYPE\_SRVR\_EMB。  這是使用的功能表資源，並在另一個容器中內嵌的文件進行編輯。  在 MFC\/OLE1 特有的編輯內嵌項目正在執行中修改功能表項目。  使用完全不同的功能表結構，在編輯內嵌項目而不是編輯檔案架構資料可讓您更輕鬆地為這兩個模式提供不同的使用者介面。  因為您將看到，使用完全不同的功能表資源，並且可就地編輯時的內嵌物件。  
  
 若要建立這個資源，載入資源指令碼到 Visual C\+\+ 並複製現有的 IDR\_HIERSVRTYPE 功能表資源。  將新資源重新命名為 IDR\_HIERSVRTYPE\_SRVR\_EMB \(這是 AppWizard 用途\) 相同的命名慣例。  下變更「儲存檔案」為「檔案更新」；給它命令 ID **ID\_FILE\_UPDATE**。  也變更「儲存檔案」為「儲存檔案並複製為」；給它命令 ID **ID\_FILE\_SAVE\_COPY\_AS**。  這個架構提供這兩個命令的實作。  
  
```  
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations  
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers  
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'  
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'  
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers  
```  
  
 因為它參考到 **OLESTATUS** 型別，有一些錯誤造成 `OnSetData`覆寫。  **OLESTATUS** 是一種 OLE1 傳回的錯誤。  在 OLE 2 中，這個變更為 `HRESULT`，雖然 MFC 通常轉換 `HRESULT` 成包含錯誤的 `COleException` 。  在這種特定情形下， `OnSetData` 覆寫不再是必要的，因此，若要進行的最簡單的方法就是將它移除。  
  
```  
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters  
```  
  
 `COleServerItem` 建構函式接受額外的「BOOL」為參數。  這個旗標會判斷記憶體管理如何在 `COleServerItem` 物件完成。  將它設定為 true，架構處理這些物件記憶體管理—當不再需要時刪除。  HIERSVR 使用 **CServerItem** \(衍生自 `COleServerItem`\) 物件做為其原生資料的一部分，因此，會將這個旗標設定為 false。  這讓 HIERSVR 刪除功能表項目時判斷。  
  
```  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class  
```  
  
 因為這些錯誤暗示，未在 CServerItem 覆寫的一些「純虛擬函式」。  這很可能是由 OnDraw 的參數清單已變更的事實所造成。  若要更正這個錯誤，請變更 **CServerItem::OnDraw** 如下 \(以及在 svritem.h 宣告\)：  
  
```  
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)  
{  
    // request from OLE to draw node  
    pDC->SetMapMode(MM_TEXT); // always in pixels  
    return DoDraw(pDC, CPoint(0,0), FALSE);  
}  
```  
  
 新的參數是「rSize」。  這可讓您填入繪製的大小，如果方便。  這個大小必須在 **HIMETRIC**。  在這種情況下，填入這個值不方便，因此，架構會呼叫 `OnGetExtent` 來擷取範圍。  如需成功運行，您必須實作 `OnGetExtent`:  
  
```  
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)  
{  
    if (dwDrawAspect != DVASPECT_CONTENT)  
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);  
  
    rSize = CalcNodeSize();  
    return TRUE;  
}  
  
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier  
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type  
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,int )__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'  
```  
  
 在 CServerItem::CalcNodeSize 函式項目大小在 **m\_rectBounds**轉換成 **HIMETRIC** 和儲存。  `COleServerItem` 未記載的 '**m\_rectBounds**' 成員不存在 \(由 `m_sizeExtent`部分取代，但是在 OLE 2 成員比 **m\_rectBounds** 在 OLE1 有稍微不同的使用方式\)。  除了設定 **HIMETRIC** 大小加入至這個成員變數中，您會將它傳回。  這個傳回值用於 `OnGetExtent`，先前實作。  
  
```  
CSize CServerItem::CalcNodeSize()  
{  
    CClientDC dcScreen(NULL);  
  
    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,  
      m_strDescription.GetLength());  
    m_sizeNode += CSize(CX_INSET * 2, CY_INSET * 2);  
  
    // set suggested HIMETRIC size  
    CSize size(m_sizeNode.cx, m_sizeNode.cy);  
    dcScreen.SetMapMode(MM_HIMETRIC);  
    dcScreen.DPtoLP(&size);  
    return size;  
}  
```  
  
 CServerItem 也覆寫 **COleServerItem::OnGetTextData**。  這個函式在 MFC\/OLE 已經過時且會由不同的機制取代。  MFC OLE 範例 [HIERSVR](../top/visual-cpp-samples.md) 的 MFC 3.0 版會覆寫 `COleServerItem::OnRenderFileData` 實作這項功能。  這項功能對這個基礎通訊埠不重要，因此，您可以取消 OnGetTextData 覆寫。  
  
 在未處理的 svritem.cpp 有許多錯誤。  它們不是真正的錯誤—是先前的錯誤導致的錯誤。  
  
```  
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters  
```  
  
 `COleServerItem::CopyToClipboard` 不再支援「bIncludeNative」旗標。  原生資料 \(伺服器項目寫出資料序列化函式\) 永遠複製，因此，移除第一個參數。  此外，當發生錯誤而不是傳回 false時，`CopyToClipboard` 會擲回例外狀況。  變更 CServerView::OnEditCopy 的程式碼如下所示：  
  
```  
void CServerView::OnEditCopy()  
{  
    if (m_pSelectedNode == NULL)  
        AfxThrowNotSupportedException();  
  
    TRY  
    {  
        m_pSelectedNode->CopyToClipboard(TRUE);  
    }  
    CATCH_ALL(e)  
    {  
        AfxMessageBox("Copy to clipboard failed");  
    }  
    END_CATCH_ALL     
}  
```  
  
 雖然起因於 HIERSVR 的 MFC 2.0 版的編譯的錯誤較 OCLIENT 的相同版本多，實際上只有少量變更。  
  
 此時 HIERSVR 將編譯及連結並當做 OLE 伺服器，不過，不用就地編輯功能，該功能接下來會實作。  
  
## 加入「視覺化編輯」  
 若要加入「編輯的視覺」\(或就地啟動\) 至這個伺服器應用程式，您只必須負則一些事件：  
  
-   當項目是就地啟動時，您需要特殊功能表資源使用。  
  
-   這個應用程式有工具列，因此，您必須有具有一個標準工具列的子集來符合從伺服器可取得的功能表命令\(符合上述的功能表資源\)。  
  
-   您需要一個衍生自提供就地使用者介面的  `COleIPFrameWnd` 的新類別 \(很像 CMainFrame，衍生自 `CMDIFrameWnd`，提供 MDI 使用者介面\)。  
  
-   您需要告知這些特殊資源和類別的框架。  
  
 功能表資源可輕鬆建立。  執行 Visual C\+\+，複製功能表資源 IDR\_HIERSVRTYPE 至呼叫 IDR\_HIERSVRTYPE\_SRVR\_IP 的功能表資源。  修改功能表，以便只有編輯和說明功能表快顯在視窗左側。  將兩個分隔符號加入至編輯和說明功能表之間 \(應該看到類似：編輯&#124;&#124;說明\)。  如需這些分隔符號的意義及伺服器和容器功能表如何合併的詳細資訊，請參閱*OLE 2 類別* 中的「功能表和資源：功能表合併」。  
  
 子集工具列的點陣圖可以從「server」索引標籤已選取的新的 AppWizard 產生的應用程式複製一個來輕鬆建立。  這個點陣圖可以匯入到 Visual C\+\+。  請確定給點陣圖一個 IDR\_HIERSVRTYPE\_SRVR\_IP 的 ID。  
  
 衍生自 `COleIPFrameWnd` 的類別可以從一個 AppWizard 產生的應用程式搭配伺服器支援複製。  複製兩個檔案，IPFRAME.CPP 和 IPFRAME.H 並加入至專案。  請確定 `LoadBitmap` 呼叫參考 IDR\_HIERSVRTYPE\_SRVR\_IP，在先前步驟中建立的點陣圖。  
  
 既然所有新資源和類別被建立，加入必要的程式碼以便架構知道這些\(和知道這個應用程式現在支援就地編輯\)。  這會藉由某些參數加入至 `InitInstance` 函式的`SetServerInfo` 呼叫而完成：  
  
```  
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,  
    IDR_HIERSVRTYPE_SRVR_IP, RUNTIME_CLASS(CInPlaceFrame));  
```  
  
 它現在已準備好要就地，也支援就地啟動的任何容器。  但是，仍然有延遲在程式碼中的較小錯誤。  HIERSVR 支援內容功能表，顯示使用者按下滑鼠右鍵。  當 HIERSVR 完全開啟時，這個功能表運作，但是當就地編輯內嵌則無法運作。  原因可以修正向下到在 CServerView::OnRButtonDown 這個程式碼：  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x, point.y, AfxGetApp()->m_pMainWnd);  
```  
  
 請注意對 **AfxGetApp\(\)\-\>m\_pMainWnd**的參考。  當伺服器是就地啟動時，它有主視窗，然後 m\_pMainWnd 設定，不過它通常是不可見的。  此外，這個視窗參考應用程式的 *主視窗* ，顯示的 MDI 框架視窗目前的伺服器是完全獨立開啟或執行。  它不是指使用中框架視窗中，該視窗在就地啟用時衍生自 `COleIPFrameWnd`。  取得正確使用中視窗，即使就地編輯， MFC 這個版本會加入新的函式 `AfxGetMainWnd`。  通常，您應該使用此函式來取代 **AfxGetApp\(\)\-\>m\_pMainWnd**。  這個程式碼需要變更如下：  
  
```  
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,  
    point.x, point.y, AfxGetMainWnd());  
```  
  
 您現在有一個 OLE 伺服器為功能就地啟用最低限度地啟用。  但仍有許多功能可用於在 MFC\/OLE1 中無法使用的 MFC\/OLE 2。  針對您想要實作之功能的詳細概念請參閱 HIERSVR 範例。  某些 HIERSVR 實作的功能如下所列：  
  
-   縮放，為 true WYSISYG 相對容器的行為。  
  
-   拖放和自訂的剪貼簿格式。  
  
-   容器視窗做為選取範圍變更時移動。  
  
 在 MFC 3.0 的 HIERSVR 範例為其伺服器項目也會使用一個稍微不同的設計。  這有助於節省記憶體而讓您的連結更有彈性。  HIERSVR 2.0 版本在樹狀 *is\-a* `COleServerItem`的每一個節點。  `COleServerItem` 會為這些節點比起必要的傳送更多額外負荷，不過， `COleServerItem` 對於每個作用中連結是必要的。  至於大部分，在任何指定時間有少數作用中連結。  要將這個變得更有效率，在這個版本的 MFC HIERSVR 從 `COleServerItem`分隔節點。  它有 CServerNode 和一個 **CServerItem** 類別。  **CServerItem** \(衍生自 `COleServerItem`\) 視需要建立。  一旦使用該特定連結的容器 \(或容器\) 停止的那個特定節點， CServerItem 物件與 CServerNode 刪除。  這個設計更有效率且更有彈性。  其彈性進入，在處理多重選取連結時。  HIERSVR 支援多重選取的這兩個版本皆不是，但加入\(並支援連結該選取\)搭配 HIERSVR 的 MFC 3.0 版本，因為 兩者皆不是 HIERSVR 支援多重選取，這兩個版本，而不會更容易加入 \(和對這類選取的支援連結\) 與 HIERSVR MFC 3.0 版，因為 `COleServerItem`與原生資料分割。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)
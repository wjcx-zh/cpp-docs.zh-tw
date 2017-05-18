---
title: "COleDocument 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDocument
- AFXOLE/COleDocument
- AFXOLE/COleDocument::COleDocument
- AFXOLE/COleDocument::AddItem
- AFXOLE/COleDocument::ApplyPrintDevice
- AFXOLE/COleDocument::EnableCompoundFile
- AFXOLE/COleDocument::GetInPlaceActiveItem
- AFXOLE/COleDocument::GetNextClientItem
- AFXOLE/COleDocument::GetNextItem
- AFXOLE/COleDocument::GetNextServerItem
- AFXOLE/COleDocument::GetPrimarySelectedItem
- AFXOLE/COleDocument::GetStartPosition
- AFXOLE/COleDocument::HasBlankItems
- AFXOLE/COleDocument::OnShowViews
- AFXOLE/COleDocument::RemoveItem
- AFXOLE/COleDocument::UpdateModifiedFlag
- AFXOLE/COleDocument::OnEditChangeIcon
- AFXOLE/COleDocument::OnEditConvert
- AFXOLE/COleDocument::OnEditLinks
- AFXOLE/COleDocument::OnFileSendMail
- AFXOLE/COleDocument::OnUpdateEditChangeIcon
- AFXOLE/COleDocument::OnUpdateEditLinksMenu
- AFXOLE/COleDocument::OnUpdateObjectVerbMenu
- AFXOLE/COleDocument::OnUpdatePasteLinkMenu
- AFXOLE/COleDocument::OnUpdatePasteMenu
dev_langs:
- C++
helpviewer_keywords:
- COleDocument class
- OLE documents, base class
- OLE containers, client items
- visual editing, OLE document base class
- OLE documents
- documents, OLE
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 73bd1bc5c2c93e180b42a79cf23ab98360887c31
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="coledocument-class"></a>COleDocument 類別
支援視覺化編輯之 OLE 文件的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDocument : public CDocument  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDocument::COleDocument](#coledocument)|建構 `COleDocument` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDocument::AddItem](#additem)|將項目加入至文件所維護的項目清單。|  
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|設定列印目標裝置的文件中的所有用戶端項目。|  
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|會使用 OLE 結構化儲存體檔案格式儲存的文件。|  
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|傳回目前就地啟動 OLE 項目。|  
|[COleDocument::GetNextClientItem](#getnextclientitem)|取得逐一查看下一個用戶端項目。|  
|[COleDocument::GetNextItem](#getnextitem)|取得逐一查看下一個文件項目。|  
|[COleDocument::GetNextServerItem](#getnextserveritem)|取得逐一查看下一個伺服器項目。|  
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|傳回文件中的主要選取的 OLE 項目。|  
|[COleDocument::GetStartPosition](#getstartposition)|取得要開始反覆項目之初始位置。|  
|[COleDocument::HasBlankItems](#hasblankitems)|檢查文件中的空白項目。|  
|[COleDocument::OnShowViews](#onshowviews)|當呼叫文件成為可見或不可見。|  
|[COleDocument::RemoveItem](#removeitem)|文件所維護的項目清單中移除的項目。|  
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|將文件標記為已修改，如果任何包含的 OLE 項目已經被修改。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|處理中的 [變更圖示] 功能表命令的事件。|  
|[COleDocument::OnEditConvert](#oneditconvert)|處理內嵌或連結的物件可從一個類型轉換為另一個。|  
|[COleDocument::OnEditLinks](#oneditlinks)|處理事件，在 [編輯] 功能表上的 [連結] 命令。|  
|[COleDocument::OnFileSendMail](#onfilesendmail)|附加的文件傳送郵件訊息。|  
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|若要更新命令 UI 的 [編輯/變更圖示] 功能表選項架構呼叫。|  
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|若要更新命令 UI 的 [編輯/連結] 功能表選項架構呼叫。|  
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|若要編輯的更新命令 UI 架構呼叫 / *ObjectName*功能表選項，並從編輯存取 [動詞] 子功能表 / *ObjectName*。|  
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|若要更新命令 UI 的 [選擇性貼上] 功能表選項架構呼叫。|  
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|若要更新命令 UI 的貼上 功能表選項架構呼叫。|  
  
## <a name="remarks"></a>備註  
 `COleDocument`衍生自**CDocument**，可讓您使用 Mfc 程式庫所提供的文件/檢視架構的 OLE 應用程式。  
  
 `COleDocument`將文件當做一系列[CDocItem](../../mfc/reference/cdocitem-class.md)物件來處理 OLE 項目。 容器和伺服器應用程式需要這類的架構，因為其文件必須要能夠包含 OLE 項目。 [COleServerItem](../../mfc/reference/coleserveritem-class.md)和[COleClientItem](../../mfc/reference/coleclientitem-class.md)類別都衍生自`CDocItem`，管理應用程式與 OLE 項目之間的互動。  
  
 如果您正在撰寫一個簡單的容器應用程式，衍生您的文件類別從`COleDocument`。 如果您正在撰寫一個容器應用程式，支援連結至其文件所包含內嵌的項目，衍生您的文件類別從[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)。 如果您正在撰寫伺服器應用程式或組合容器/伺服器，衍生您的文件類別從[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)。 `COleLinkingDoc`和`COleServerDoc`衍生自`COleDocument`，因此這些類別會繼承中所提供的所有服務`COleDocument`和**CDocument**。  
  
 若要使用`COleDocument`、 衍生的類別和新增功能，以便管理應用程式的非 OLE 資料，以及內嵌或連結項目。 如果您定義`CDocItem`-衍生的類別來儲存應用程式的原生資料，您可以使用所定義的預設實作`COleDocument`儲存 OLE 和非 OLE 資料。 您也可以設計自己的資料結構來儲存非 OLE 資料分開 OLE 項目。 如需詳細資訊，請參閱文章[容器︰ 複合檔案](../../mfc/containers-compound-files.md)...  
  
 **CDocument**支援傳送郵件透過文件是否有郵件支援 (MAPI)。 `COleDocument`已更新[OnFileSendMail](#onfilesendmail)正確處理複合文件。 如需詳細資訊，請參閱文章[MAPI](../../mfc/mapi.md)和[MFC 的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)...  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `COleDocument`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="additem"></a>COleDocument::AddItem  
 呼叫此函式可將項目加入至文件。  
  
```  
virtual void AddItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 要加入文件項目的指標。  
  
### <a name="remarks"></a>備註  
 您不需要明確呼叫此函式，呼叫此方法時`COleClientItem`或`COleServerItem`接受指向文件的建構函式。  
  
##  <a name="applyprintdevice"></a>COleDocument::ApplyPrintDevice  
 呼叫此函式來變更所有內嵌的列印目標裝置[COleClientItem](../../mfc/reference/coleclientitem-class.md)您的應用程式在容器文件中的項目。  
  
```  
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);  
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```  
  
### <a name="parameters"></a>參數  
 `ptd`  
 指標**DVTARGETDEVICE**資料結構，其中包含新的列印目標裝置的相關資訊。 可以是**NULL**。  
  
 `ppd`  
 指標**PRINTDLG**資料結構，其中包含新的列印目標裝置的相關資訊。 可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式來更新列印目標裝置的所有項目，但不會重新整理簡報快取項目的。 若要更新簡報快取的項目，呼叫[COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)。  
  
 此函式的引數包含 OLE 用來識別目標裝置的資訊。 [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)結構包含 Windows 用來初始化一般的 [列印] 對話方塊的資訊。 使用者關閉對話方塊之後，Windows 會傳回這個結構中的使用者選取的相關資訊。 `m_pd`成員[CPrintDialog](../../mfc/reference/cprintdialog-class.md)物件是**PRINTDLG**結構。  
  
 如需詳細資訊，請參閱[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需詳細資訊，請參閱[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="coledocument"></a>COleDocument::COleDocument  
 建構 `COleDocument` 物件。  
  
```  
COleDocument();
```  
  
##  <a name="enablecompoundfile"></a>COleDocument::EnableCompoundFile  
 如果您想要儲存使用複合檔案格式的文件，請呼叫此函式。  
  
```  
void EnableCompoundFile(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bEnable`  
 指定是否啟用或停用支援複合檔案。  
  
### <a name="remarks"></a>備註  
 這也稱為結構化儲存體。 一般都會呼叫此函式的建構函式從您`COleDocument`-衍生的類別。 如需複合文件的詳細資訊，請參閱文章[容器︰ 複合檔案](../../mfc/containers-compound-files.md)...  
  
 如果您不會呼叫此成員函式，文件會儲存在 nonstructured （「 一般 」） 的檔案格式。  
  
 複合檔案支援為啟用或停用文件之後，文件的存留期間不應該變更此設定。  
  
##  <a name="getinplaceactiveitem"></a>COleDocument::GetInPlaceActiveItem  
 呼叫此函式可取得 OLE 項目目前已啟動，包含所識別的檢視和框架視窗中就地`pWnd`。  
  
```  
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 會顯示在容器文件視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 單一的就地使用中 OLE 項目的指標。**NULL**如果有任何 OLE 項目目前是處於 「 就地使用中 」 狀態。  
  
##  <a name="getnextclientitem"></a>COleDocument::GetNextClientItem  
 呼叫此函式重複存取每個文件中的用戶端項目。  
  
```  
COleClientItem* GetNextClientItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 參考**位置**設定值由先前呼叫`GetNextClientItem`; 預設值由`GetStartPosition`成員函式。  
  
### <a name="return-value"></a>傳回值  
 下一步，文件中的用戶端項目的指標或**NULL**如果沒有更多的用戶端項目。  
  
### <a name="remarks"></a>備註  
 在每次呼叫時的值之後`pos`設定文件，這可能會或可能不是用戶端項目中的下一個項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&1;](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]  
  
##  <a name="getnextitem"></a>COleDocument::GetNextItem  
 呼叫此函式重複存取每個文件中的項目。  
  
```  
virtual CDocItem* GetNextItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 參考**位置**設定值由先前呼叫`GetNextItem`; 預設值由`GetStartPosition`成員函式。  
  
### <a name="return-value"></a>傳回值  
 指定位置處的文件項目指標。  
  
### <a name="remarks"></a>備註  
 在每次呼叫時的值之後`pos`設為**位置**文件中的下一個項目值。 如果擷取的項目是在文件中的新值的最後一個項目`pos`是**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer #&2;](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]  
  
##  <a name="getnextserveritem"></a>COleDocument::GetNextServerItem  
 呼叫此函式重複存取每個文件中的伺服器項目。  
  
```  
COleServerItem* GetNextServerItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 參考**位置**設定值由先前呼叫`GetNextServerItem`; 預設值由`GetStartPosition`成員函式。  
  
### <a name="return-value"></a>傳回值  
 下一步，文件中的伺服器項目的指標或**NULL**如果沒有更多的伺服器項目。  
  
### <a name="remarks"></a>備註  
 在每次呼叫時的值之後`pos`設定文件，這可能會或可能不是伺服器項目中的下一個項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleServer #&2;](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]  
  
##  <a name="getprimaryselecteditem"></a>COleDocument::GetPrimarySelectedItem  
 若要擷取在指定的檢視中目前選取的 OLE 項目架構呼叫。  
  
```  
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```  
  
### <a name="parameters"></a>參數  
 `pView`  
 顯示文件的使用中檢視物件的指標。  
  
### <a name="return-value"></a>傳回值  
 指向單一的所選的 OLE 項目。**NULL**如果未選取任何 OLE 項目或多個已選取。  
  
### <a name="remarks"></a>備註  
 預設實作搜尋清單包含的 OLE 項目選取單一項目，並傳回的指標。 如果沒有選取的項目，或是否有多個選取的項目，則此函數會傳回**NULL**。 您必須覆寫`CView::IsSelected`中您要使用此函式的檢視類別的成員函式。 如果您有自己的方法，儲存所含的 OLE 項目，請覆寫這個函式。  
  
##  <a name="getstartposition"></a>COleDocument::GetStartPosition  
 呼叫此函式可取得文件中的第一個項目的位置。  
  
```  
virtual POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，可用來逐一查看文件的項目︰**NULL**如果文件不有任何項目。  
  
### <a name="remarks"></a>備註  
 傳回的值傳遞`GetNextItem`， `GetNextClientItem`，或`GetNextServerItem`。  
  
##  <a name="hasblankitems"></a>COleDocument::HasBlankItems  
 呼叫此函式可判斷文件是否包含任何空白項目。  
  
```  
BOOL HasBlankItems() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零的文件包含的任何空白項目。否則為 0。  
  
### <a name="remarks"></a>備註  
 空白項目是其矩形是空的。  
  
##  <a name="oneditchangeicon"></a>COleDocument::OnEditChangeIcon  
 顯示 OLE 的 變更圖示 對話方塊中，並會變更目前所選的 OLE 項目代表使用者選取對話方塊中之圖示的圖示。  
  
```  
afx_msg void OnEditChangeIcon();
```  
  
### <a name="remarks"></a>備註  
 `OnEditChangeIcon`會建立和啟動`COleChangeIconDialog`變更圖示 對話方塊。  
  
##  <a name="oneditconvert"></a>COleDocument::OnEditConvert  
 OLE 轉換 對話方塊會顯示與轉換或啟動根據使用者選取項目 對話方塊中目前選取的 OLE 項目。  
  
```  
afx_msg void OnEditConvert();
```  
  
### <a name="remarks"></a>備註  
 `OnEditConvert`會建立和啟動`COleConvertDialog`轉換 對話方塊。  
  
 轉換的範例將 Microsoft Word 文件轉換成 WordPad 文件。  
  
##  <a name="oneditlinks"></a>COleDocument::OnEditLinks  
 顯示 OLE 編輯/連結 對話方塊。  
  
```  
afx_msg void OnEditLinks();
```  
  
### <a name="remarks"></a>備註  
 `OnEditLinks`會建立和啟動`COleLinksDialog`連結 對話方塊，可讓使用者變更連結的物件。  
  
##  <a name="onfilesendmail"></a>COleDocument::OnFileSendMail  
 傳送訊息透過內建的郵件主機 （如果有的話） 與文件作為附件。  
  
```  
afx_msg void OnFileSendMail();
```  
  
### <a name="remarks"></a>備註  
 `OnFileSendMail`呼叫`OnSaveDocument`序列化 （儲存） 到暫存檔案，然後透過電子郵件會傳送未命名和修改過的文件。 如果未修改文件，不被必要的暫存檔;原始會傳送。 `OnFileSendMail`載入 MAPI32。如果它已經尚未載入的 DLL。  
  
 不同的實作於`OnFileSendMail`的**CDocument**，此函式會正確處理複合檔案。  
  
 如需詳細資訊，請參閱[MAPI 主題](../../mfc/mapi.md)和[MFC 的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)文章...  
  
##  <a name="onshowviews"></a>COleDocument::OnShowViews  
 架構會呼叫此函式後文件的可見性狀態變更。  
  
```  
virtual void OnShowViews(BOOL bVisible);
```  
  
### <a name="parameters"></a>參數  
 `bVisible`  
 表示文件是否已成為可見或不可見。  
  
### <a name="remarks"></a>備註  
 此函式的預設版本，就沒有作用。 如果您的應用程式必須執行任何特殊處理文件的可見性變更時，則請它覆寫。  
  
##  <a name="onupdateeditchangeicon"></a>COleDocument::OnUpdateEditChangeIcon  
 若要更新 [編輯] 功能表上的 [變更圖示] 命令，架構呼叫。  
  
```  
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 `pCmdUI`  
 指標`CCmdUI`結構，表示產生更新命令的功能表。 更新處理常式呼叫**啟用**成員函式`CCmdUI`結構透過`pCmdUI`來更新使用者介面。  
  
### <a name="remarks"></a>備註  
 `OnUpdateEditChangeIcon`更新命令的使用者介面，根據有效的圖示存在於文件。 覆寫此函式可變更的行為。  
  
##  <a name="onupdateeditlinksmenu"></a>COleDocument::OnUpdateEditLinksMenu  
 更新 [編輯] 功能表上的 [連結] 命令，架構呼叫。  
  
```  
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 `pCmdUI`  
 指標`CCmdUI`結構，表示產生更新命令的功能表。 更新處理常式呼叫**啟用**成員函式`CCmdUI`結構透過`pCmdUI`來更新使用者介面。  
  
### <a name="remarks"></a>備註  
 開始在文件中第一個 OLE 項目`OnUpdateEditLinksMenu`存取每個項目時，測試是否項目連結，以及，如果它是連結，可讓 [連結] 命令。 覆寫此函式可變更的行為。  
  
##  <a name="onupdateobjectverbmenu"></a>COleDocument::OnUpdateObjectVerbMenu  
 更新架構呼叫*ObjectName*命令 [編輯] 功能表和 [動詞] 子功能表存取*ObjectName*命令，其中*ObjectName*文件中內嵌 OLE 物件的名稱。  
  
```  
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 `pCmdUI`  
 指標`CCmdUI`結構，表示產生更新命令的功能表。 更新處理常式呼叫**啟用**成員函式`CCmdUI`結構透過`pCmdUI`來更新使用者介面。  
  
### <a name="remarks"></a>備註  
 `OnUpdateObjectVerbMenu`更新*ObjectName*根據有效的物件是否有文件中的命令的使用者介面。 如果物件存在， *ObjectName*已啟用 [編輯] 功能表上的命令。 選取此功能表命令時，會顯示 [動詞] 子功能表。 [動詞] 子功能表包含物件，例如編輯、 屬性及其他可用的所有動詞命令。 覆寫此函式可變更的行為。  
  
##  <a name="onupdatepastelinkmenu"></a>COleDocument::OnUpdatePasteLinkMenu  
 若要判斷是否可以從剪貼簿貼上連結的 OLE 項目架構呼叫。  
  
```  
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 `pCmdUI`  
 指標`CCmdUI`結構，表示產生更新命令的功能表。 更新處理常式呼叫**啟用**成員函式`CCmdUI`結構透過`pCmdUI`來更新使用者介面。  
  
### <a name="remarks"></a>備註  
 啟用或停用項目是否可以貼到文件或未根據選擇性貼上的功能表命令。  
  
##  <a name="onupdatepastemenu"></a>COleDocument::OnUpdatePasteMenu  
 若要判斷內嵌的 OLE 項目是否可以從剪貼簿貼上架構呼叫。  
  
```  
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 `pCmdUI`  
 指標`CCmdUI`結構，表示產生更新命令的功能表。 更新處理常式呼叫**啟用**成員函式`CCmdUI`結構透過`pCmdUI`來更新使用者介面。  
  
### <a name="remarks"></a>備註  
 貼上 功能表命令和按鈕啟用或停用項目是否可以貼到文件或未根據。  
  
##  <a name="removeitem"></a>COleDocument::RemoveItem  
 呼叫此函式來移除文件中的項目。  
  
```  
virtual void RemoveItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 要移除文件項目的指標。  
  
### <a name="remarks"></a>備註  
 您通常不需要明確地呼叫此函式。它會呼叫解構函式`COleClientItem`和`COleServerItem`。  
  
##  <a name="updatemodifiedflag"></a>COleDocument::UpdateModifiedFlag  
 呼叫此函式可將文件標記為已修改，如果任何包含的 OLE 項目已經被修改。  
  
```  
virtual void UpdateModifiedFlag();
```  
  
### <a name="remarks"></a>備註  
 這讓提示使用者在關閉之前，儲存文件，即使文件中的原生資料未修改架構。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例容器](../../visual-cpp-samples.md)   
 [MFC 範例 MFCBIND](../../visual-cpp-samples.md)   
 [CDocument 類別](../../mfc/reference/cdocument-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)





---
title: COleDocument 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- COleDocument [MFC], COleDocument
- COleDocument [MFC], AddItem
- COleDocument [MFC], ApplyPrintDevice
- COleDocument [MFC], EnableCompoundFile
- COleDocument [MFC], GetInPlaceActiveItem
- COleDocument [MFC], GetNextClientItem
- COleDocument [MFC], GetNextItem
- COleDocument [MFC], GetNextServerItem
- COleDocument [MFC], GetPrimarySelectedItem
- COleDocument [MFC], GetStartPosition
- COleDocument [MFC], HasBlankItems
- COleDocument [MFC], OnShowViews
- COleDocument [MFC], RemoveItem
- COleDocument [MFC], UpdateModifiedFlag
- COleDocument [MFC], OnEditChangeIcon
- COleDocument [MFC], OnEditConvert
- COleDocument [MFC], OnEditLinks
- COleDocument [MFC], OnFileSendMail
- COleDocument [MFC], OnUpdateEditChangeIcon
- COleDocument [MFC], OnUpdateEditLinksMenu
- COleDocument [MFC], OnUpdateObjectVerbMenu
- COleDocument [MFC], OnUpdatePasteLinkMenu
- COleDocument [MFC], OnUpdatePasteMenu
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f492e7fc3e29c74caba7303179b72c5dacad72e
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040684"
---
# <a name="coledocument-class"></a>COleDocument 類別
支援視覺化編輯之 OLE 文件的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDocument : public CDocument  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDocument::COleDocument](#coledocument)|建構 `COleDocument` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDocument::AddItem](#additem)|將項目加入至文件所維護的項目清單。|  
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|設定文件中的列印目標裝置的所有用戶端項目。|  
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|會使用 OLE 結構化儲存體的檔案格式儲存的文件。|  
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|傳回目前就地啟用作用中的 OLE 項目。|  
|[COleDocument::GetNextClientItem](#getnextclientitem)|取得逐一查看下一個用戶端項目。|  
|[COleDocument::GetNextItem](#getnextitem)|取得逐一查看下一個文件項目。|  
|[COleDocument::GetNextServerItem](#getnextserveritem)|取得逐一查看下一個伺服器項目。|  
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|文件中傳回主要選取的 OLE 項目。|  
|[COleDocument::GetStartPosition](#getstartposition)|取得要開始反覆項目之初始位置。|  
|[COleDocument::HasBlankItems](#hasblankitems)|檢查文件中的空白項目。|  
|[COleDocument::OnShowViews](#onshowviews)|當呼叫文件會變成可見或不可見。|  
|[COleDocument::RemoveItem](#removeitem)|文件所維護的項目清單中移除的項目。|  
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|將文件標示為已修改若任何包含的 OLE 項目已修改。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|處理中的 [變更圖示] 功能表命令的事件。|  
|[COleDocument::OnEditConvert](#oneditconvert)|處理內嵌或連結的物件可從一個類型轉換到另一個。|  
|[COleDocument::OnEditLinks](#oneditlinks)|處理事件，在 [編輯] 功能表中的 [連結] 命令。|  
|[COleDocument::OnFileSendMail](#onfilesendmail)|傳送郵件訊息與附加的文件。|  
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|由架構呼叫以更新命令 UI 的 [編輯/變更圖示] 功能表選項。|  
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|由架構呼叫以更新命令 UI 的 編輯/連結功能表選項。|  
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|由架構呼叫以更新命令 UI 的 編輯 / *ObjectName*功能表選項，並從編輯存取 動詞 子功能表 / *ObjectName*。|  
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|由架構呼叫以更新命令 UI 的 選擇性貼上的功能表選項。|  
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|由架構呼叫以更新命令 UI 的 [貼上] 功能表選項。|  
  
## <a name="remarks"></a>備註  
 `COleDocument` 衍生自`CDocument`，可讓您使用 Microsoft Foundation 類別庫所提供的文件/檢視架構的 OLE 應用程式。  
  
 `COleDocument` 將文件做為集合[CDocItem](../../mfc/reference/cdocitem-class.md)物件來處理 OLE 項目。 容器和伺服器應用程式需要這類架構，因為其文件中必須要能夠包含 OLE 項目。 [COleServerItem](../../mfc/reference/coleserveritem-class.md)和[COleClientItem](../../mfc/reference/coleclientitem-class.md)類別都衍生自`CDocItem`，管理應用程式和 OLE 項目之間的互動。  
  
 如果您要撰寫簡單的容器應用程式，衍生您的文件的類別從`COleDocument`。 如果您正在撰寫一個容器應用程式，支援將連結至其文件所包含內嵌的項目，衍生您的文件的類別從[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)。 如果您要撰寫伺服器應用程式或組合容器/伺服器，衍生您的文件的類別從[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)。 `COleLinkingDoc` 和`COleServerDoc`衍生自`COleDocument`，因此這些類別會繼承中可用的所有服務`COleDocument`和`CDocument`。  
  
 若要使用`COleDocument`衍生的類別，將功能加入至管理應用程式的非 OLE 資料，以及內嵌或連結項目。 如果您定義`CDocItem`-衍生的類別來儲存應用程式的原生資料，您可以使用所定義的預設實作`COleDocument`儲存 OLE 和非 OLE 資料。 您也可以設計自己的資料結構來儲存非 OLE 資料分開 OLE 項目。 如需詳細資訊，請參閱文章[容器： 複合檔案](../../mfc/containers-compound-files.md)...  
  
 `CDocument` 如果郵件支援 (MAPI) 存在於傳送郵件透過文件的支援。 `COleDocument` 已更新[OnFileSendMail](#onfilesendmail)複合文件來正確地處理。 如需詳細資訊，請參閱文章[MAPI](../../mfc/mapi.md)和[MFC 中的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)...  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `COleDocument`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="additem"></a>  COleDocument::AddItem  
 呼叫此函式可將項目加入至文件。  
  
```  
virtual void AddItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>參數  
 *pItem*  
 要加入的文件項目指標。  
  
### <a name="remarks"></a>備註  
 您不需要呼叫此方法時，明確地呼叫這個函式`COleClientItem`或`COleServerItem`建構函式可接受的文件的指標。  
  
##  <a name="applyprintdevice"></a>  COleDocument::ApplyPrintDevice  
 呼叫此函式可變更所有內嵌的列印目標裝置[COleClientItem](../../mfc/reference/coleclientitem-class.md)您的應用程式容器文件中的項目。  
  
```  
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);  
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```  
  
### <a name="parameters"></a>參數  
 *ptd*  
 指標**DVTARGETDEVICE**資料結構，其中包含新的列印目標裝置的相關資訊。 可以是**NULL**。  
  
 *ppd*  
 指標**PRINTDLG**資料結構，其中包含新的列印目標裝置的相關資訊。 可以是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 此函式會更新列印目標裝置的所有項目，但是不會重新整理簡報快取中的這些項目。 若要更新簡報快取中的項目，呼叫[COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)。  
  
 此函式的引數包含 OLE 用來識別目標裝置的資訊。 [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)結構包含 Windows 用來初始化一般的 [列印] 對話方塊的資訊。 使用者關閉對話方塊之後，Windows 會傳回這個結構中的相關使用者的選取項目資訊。 `m_pd`隸屬[CPrintDialog](../../mfc/reference/cprintdialog-class.md)物件是**PRINTDLG**結構。  
  
 如需詳細資訊，請參閱[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) Windows SDK 中的結構。  
  
 如需詳細資訊，請參閱[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) Windows SDK 中的結構。  
  
##  <a name="coledocument"></a>  COleDocument::COleDocument  
 建構 `COleDocument` 物件。  
  
```  
COleDocument();
```  
  
##  <a name="enablecompoundfile"></a>  COleDocument::EnableCompoundFile  
 如果您想要儲存使用複合檔案格式的文件，請呼叫此函式。  
  
```  
void EnableCompoundFile(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bEnable*  
 指定是否啟用或停用複合檔案支援。  
  
### <a name="remarks"></a>備註  
 這也稱為結構化儲存體。 通常呼叫此函式的建構函式從您`COleDocument`-衍生的類別。 如需複合文件的詳細資訊，請參閱文章[容器： 複合檔案](../../mfc/containers-compound-files.md)...  
  
 如果您不會呼叫此成員函式，文件會儲存在 nonstructured （「 一般 」） 檔案格式。  
  
 複合檔案支援為啟用或停用文件之後，文件的存留期間不應該變更設定。  
  
##  <a name="getinplaceactiveitem"></a>  COleDocument::GetInPlaceActiveItem  
 呼叫此函式可取得 OLE 項目目前啟動包含所識別的檢視和框架視窗中就地*pWnd*。  
  
```  
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 *pWnd*  
 顯示容器文件視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 單一、 就地使用中 OLE 項目的指標。**NULL**如果沒有 OLE 項目目前處於 「 就地啟用作用中 」 狀態。  
  
##  <a name="getnextclientitem"></a>  COleDocument::GetNextClientItem  
 呼叫此函式重複可存取每個文件中的用戶端項目。  
  
```  
COleClientItem* GetNextClientItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>參數  
 *pos*  
 參考**位置**設定值由先前呼叫`GetNextClientItem`; 起始值由`GetStartPosition`成員函式。  
  
### <a name="return-value"></a>傳回值  
 下一步，文件中的用戶端項目的指標或**NULL**如果沒有更多的用戶端項目。  
  
### <a name="remarks"></a>備註  
 每次呼叫時，值之後*pos*設定文件，其中可能會或可能不是用戶端項目中的下一個項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]  
  
##  <a name="getnextitem"></a>  COleDocument::GetNextItem  
 呼叫此函式重複可存取每個文件中的項目。  
  
```  
virtual CDocItem* GetNextItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>參數  
 *pos*  
 參考**位置**設定值由先前呼叫`GetNextItem`; 起始值由`GetStartPosition`成員函式。  
  
### <a name="return-value"></a>傳回值  
 指定位置處的文件項目指標。  
  
### <a name="remarks"></a>備註  
 每次呼叫時，值之後*pos*設**位置**文件中的下一個項目值。 如果擷取的項目是在文件中的新值的最後一個項目*pos*是**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]  
  
##  <a name="getnextserveritem"></a>  COleDocument::GetNextServerItem  
 呼叫此函式重複可存取每個文件中的伺服器項目。  
  
```  
COleServerItem* GetNextServerItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>參數  
 *pos*  
 參考**位置**設定值由先前呼叫`GetNextServerItem`; 起始值由`GetStartPosition`成員函式。  
  
### <a name="return-value"></a>傳回值  
 下一步，文件中的伺服器項目的指標或**NULL**如果沒有更多的伺服器項目。  
  
### <a name="remarks"></a>備註  
 每次呼叫時，值之後*pos*設定文件，其中可能會或可能不是伺服器項目中的下一個項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]  
  
##  <a name="getprimaryselecteditem"></a>  COleDocument::GetPrimarySelectedItem  
 由架構呼叫以擷取目前選取的 OLE 項目中指定的檢視。  
  
```  
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```  
  
### <a name="parameters"></a>參數  
 *pView*  
 顯示文件的作用中的檢視物件的指標。  
  
### <a name="return-value"></a>傳回值  
 指向單一、 選取 OLE 項目。**NULL**如果不選取任何 OLE 項目或多個已選取其中。  
  
### <a name="remarks"></a>備註  
 預設實作搜尋清單包含的 OLE 項目的單一選取項目，並傳回的指標。 如果沒有選取的項目，或是否有多個選取的項目，則此函數會傳回**NULL**。 您必須覆寫`CView::IsSelected`中您要使用此函式的檢視類別成員函式。 如果您有自己的方法，儲存所含的 OLE 項目，請覆寫這個函式。  
  
##  <a name="getstartposition"></a>  COleDocument::GetStartPosition  
 呼叫此函式，以取得文件中的第一個項目的位置。  
  
```  
virtual POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，可用來逐一查看文件的項目。**NULL**如果文件不有任何項目。  
  
### <a name="remarks"></a>備註  
 傳回的值傳遞`GetNextItem`， `GetNextClientItem`，或`GetNextServerItem`。  
  
##  <a name="hasblankitems"></a>  COleDocument::HasBlankItems  
 呼叫此函式可判斷文件是否包含任何空白項目。  
  
```  
BOOL HasBlankItems() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果文件包含的任何空白的項目，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 空白項目是其矩形是空的。  
  
##  <a name="oneditchangeicon"></a>  COleDocument::OnEditChangeIcon  
 顯示 OLE 的 變更圖示 對話方塊，並變更目前所選的 OLE 項目代表使用者 對話方塊中選取之圖示的圖示。  
  
```  
afx_msg void OnEditChangeIcon();
```  
  
### <a name="remarks"></a>備註  
 `OnEditChangeIcon` 建立並啟動`COleChangeIconDialog`變更圖示 對話方塊。  
  
##  <a name="oneditconvert"></a>  COleDocument::OnEditConvert  
 OLE 轉換 對話方塊會顯示和轉換或啟動目前所選的 OLE 項目，根據在對話方塊中的使用者選項。  
  
```  
afx_msg void OnEditConvert();
```  
  
### <a name="remarks"></a>備註  
 `OnEditConvert` 建立並啟動`COleConvertDialog`轉換 對話方塊。  
  
 轉換的範例將 Microsoft Word 文件轉換成 WordPad 文件。  
  
##  <a name="oneditlinks"></a>  COleDocument::OnEditLinks  
 顯示 OLE 編輯/連結 對話方塊。  
  
```  
afx_msg void OnEditLinks();
```  
  
### <a name="remarks"></a>備註  
 `OnEditLinks` 建立並啟動`COleLinksDialog`連結 對話方塊，可讓使用者變更連結的物件。  
  
##  <a name="onfilesendmail"></a>  COleDocument::OnFileSendMail  
 傳送訊息透過內建的郵件主機 （如果有的話） 與文件做為附件。  
  
```  
afx_msg void OnFileSendMail();
```  
  
### <a name="remarks"></a>備註  
 `OnFileSendMail` 呼叫`OnSaveDocument`（儲存） 未命名和已修改的暫存檔案，然後透過電子郵件傳送文件序列化。 如果未修改文件，則不會需要的暫存檔案;原始會傳送。 `OnFileSendMail` 載入 MAPI32。如果它已經尚未載入的 DLL。  
  
 不同於的實作`OnFileSendMail`如`CDocument`，此函式會正確處理複合檔案。  
  
 如需詳細資訊，請參閱[MAPI 主題](../../mfc/mapi.md)和[MFC 中的 MAPI 支援](../../mfc/mapi-support-in-mfc.md)文件...  
  
##  <a name="onshowviews"></a>  COleDocument::OnShowViews  
 架構會呼叫此函式之後文件的可見性狀態變更。  
  
```  
virtual void OnShowViews(BOOL bVisible);
```  
  
### <a name="parameters"></a>參數  
 *bVisible*  
 指出是否在文件變得可見或不可見。  
  
### <a name="remarks"></a>備註  
 此函式的預設版本沒有任何作用。 覆寫它，如果您的應用程式必須執行任何特殊處理文件的可見性變更時。  
  
##  <a name="onupdateeditchangeicon"></a>  COleDocument::OnUpdateEditChangeIcon  
 由架構呼叫以更新 編輯 功能表上的 變更圖示命令。  
  
```  
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 *pCmdUI*  
 指標`CCmdUI`結構，表示產生更新命令的功能表。 更新處理常式呼叫`Enable`成員函式`CCmdUI`結構透過*pCmdUI*更新使用者介面。  
  
### <a name="remarks"></a>備註  
 `OnUpdateEditChangeIcon` 更新命令的使用者介面，根據有效的圖示有文件中。 覆寫此函式可變更的行為。  
  
##  <a name="onupdateeditlinksmenu"></a>  COleDocument::OnUpdateEditLinksMenu  
 由架構呼叫以更新 [編輯] 功能表中的 [連結] 命令。  
  
```  
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 *pCmdUI*  
 指標`CCmdUI`結構，表示產生更新命令的功能表。 更新處理常式呼叫`Enable`成員函式`CCmdUI`結構透過*pCmdUI*更新使用者介面。  
  
### <a name="remarks"></a>備註  
 從開始，文件中第一個 OLE 項目`OnUpdateEditLinksMenu`存取每個項目、 測試是否項目為連結，和，如果它是連結，可讓連結命令。 覆寫此函式可變更的行為。  
  
##  <a name="onupdateobjectverbmenu"></a>  COleDocument::OnUpdateObjectVerbMenu  
 由架構呼叫以更新*ObjectName*命令 [編輯] 功能表和 [指令動詞] 子功能表從存取*ObjectName*命令，其中*ObjectName*的名稱OLE 物件內嵌在文件。  
  
```  
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 *pCmdUI*  
 指標`CCmdUI`結構，表示產生更新命令的功能表。 更新處理常式呼叫`Enable`成員函式`CCmdUI`結構透過*pCmdUI*更新使用者介面。  
  
### <a name="remarks"></a>備註  
 `OnUpdateObjectVerbMenu` 更新*ObjectName*根據有效的物件是否有文件中的命令的使用者介面。 如果物件存在， *ObjectName*已啟用 [編輯] 功能表的命令。 選取此功能表命令時，會顯示指令動詞 子功能表。 [指令動詞] 子功能表包含物件，例如編輯、 屬性，以及其他可用的所有動詞命令。 覆寫此函式可變更的行為。  
  
##  <a name="onupdatepastelinkmenu"></a>  COleDocument::OnUpdatePasteLinkMenu  
 由架構呼叫以判斷是否可以從剪貼簿貼上連結的 OLE 項目。  
  
```  
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 *pCmdUI*  
 指標`CCmdUI`結構，表示產生更新命令的功能表。 更新處理常式呼叫`Enable`成員函式`CCmdUI`結構透過*pCmdUI*更新使用者介面。  
  
### <a name="remarks"></a>備註  
 啟用或停用項目是否可以貼到文件或未根據選擇性貼上的功能表命令。  
  
##  <a name="onupdatepastemenu"></a>  COleDocument::OnUpdatePasteMenu  
 由架構呼叫以判斷內嵌的 OLE 項目是否可以從剪貼簿貼上。  
  
```  
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 *pCmdUI*  
 指標`CCmdUI`結構，表示產生更新命令的功能表。 更新處理常式呼叫`Enable`成員函式`CCmdUI`結構透過*pCmdUI*更新使用者介面。  
  
### <a name="remarks"></a>備註  
 貼上 功能表命令和按鈕啟用或停用項目是否可以貼到文件或未根據。  
  
##  <a name="removeitem"></a>  COleDocument::RemoveItem  
 呼叫此函式可在文件中移除的項目。  
  
```  
virtual void RemoveItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>參數  
 *pItem*  
 要移除文件項目指標。  
  
### <a name="remarks"></a>備註  
 您通常不需要明確地呼叫這個函式。解構函式呼叫`COleClientItem`和`COleServerItem`。  
  
##  <a name="updatemodifiedflag"></a>  COleDocument::UpdateModifiedFlag  
 呼叫此函式可將文件標示為已修改若任何包含的 OLE 項目已修改。  
  
```  
virtual void UpdateModifiedFlag();
```  
  
### <a name="remarks"></a>備註  
 這可讓架構，以提示使用者在關閉之前，儲存文件，即使未修改文件中的原生資料。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例容器](../../visual-cpp-samples.md)   
 [MFC 範例 MFCBIND](../../visual-cpp-samples.md)   
 [CDocument 類別](../../mfc/reference/cdocument-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




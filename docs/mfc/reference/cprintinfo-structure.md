---
title: "CPrintInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrintInfo
dev_langs:
- C++
helpviewer_keywords:
- CPrintInfo structure
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
caps.latest.revision: 21
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ffa72acc58e0ac1a387e67e6542abcd466be9640
ms.lasthandoff: 02/24/2017

---
# <a name="cprintinfo-structure"></a>CPrintInfo 結構
儲存列印或是預覽列印工作的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CPrintInfo  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPrintInfo::GetFromPage](#getfrompage)|傳回第一個正在列印的頁面數目。|  
|[CPrintInfo::GetMaxPage](#getmaxpage)|傳回文件的最後一頁的數目。|  
|[CPrintInfo::GetMinPage](#getminpage)|傳回文件的第一頁的數目。|  
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|傳回先前的 DocObject 項目正在列印中結合 DocObject 列印工作的第一頁的頁面數目。|  
|[CPrintInfo::GetToPage](#gettopage)|傳回最後一個正在列印的頁面數目。|  
|[CPrintInfo::SetMaxPage](#setmaxpage)|設定文件的最後一頁的數目。|  
|[CPrintInfo::SetMinPage](#setminpage)|設定文件的第一頁的數目。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|包含旗標，指出架構是否應該繼續列印迴圈。|  
|[CPrintInfo::m_bDirect](#m_bdirect)|包含旗標，指出是否在列印文件直接 （不顯示 [列印] 對話方塊中）。|  
|[CPrintInfo::m_bDocObject](#m_bdocobject)|包含旗標，指出是否要列印的文件 DocObject。|  
|[CPrintInfo::m_bPreview](#m_bpreview)|包含旗標，指出是否要預覽文件。|  
|[CPrintInfo::m_dwFlags](#m_dwflags)|指定 DocObject 列印作業。|  
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|包含使用者建立的結構的指標。|  
|[CPrintInfo::m_nCurPage](#m_ncurpage)|識別目前正在列印的頁面數目。|  
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|指定目前的列印工作的作業系統所指派的工作數目|  
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|識別在預覽視窗，顯示的頁數1 或 2。|  
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|結合 DocObject 列印工作中指定的特定 DocObject 第一頁的位移。|  
|[CPrintInfo::m_pPD](#m_ppd)|包含一個指向`CPrintDialog`用於 [列印] 對話方塊中的物件。|  
|[CPrintInfo::m_rectDraw](#m_rectdraw)|指定定義目前的可用頁面區域的矩形。|  
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|包含頁碼顯示格式字串。|  
  
## <a name="remarks"></a>備註  
 `CPrintInfo`是一種結構，而且也沒有基底類別。  
  
 此架構會建立物件的`CPrintInfo`每次列印或預覽列印 命令會選擇並命令完成後將其終結。  
  
 `CPrintInfo`包含列印工作，例如要列印的頁面範圍、 整個和目前的列印工作，例如目前列印的頁面狀態的相關資訊。 部分資訊會儲存在相關聯[CPrintDialog](../../mfc/reference/cprintdialog-class.md)物件; 此物件包含 [列印] 對話方塊中的使用者所輸入的值。  
  
 A`CPrintInfo`物件架構與您的檢視類別之間傳遞列印程序期間，用來交換兩者之間的資訊。 例如，架構就會通知檢視類別，來指派值給列印文件的哪一頁`m_nCurPage`成員`CPrintInfo`; 類別擷取值，並會執行指定的頁面的實際列印的檢視。  
  
 另一個範例是以文件的長度不知道列印前的情況。 在此情況下，檢視類別測試文件結尾的每個列印頁面的時間。 當到達結束時，檢視類別設定`m_bContinuePrinting`成員`CPrintInfo`至**FALSE**; 這會通知架構，以便停止列印迴圈。  
  
 `CPrintInfo`成員函式會使用`CView`列在 「 另請參閱。 」 如需 Mfc 程式庫所提供的列印架構的詳細資訊，請參閱[框架視窗](../../mfc/frame-windows.md)和[文件/檢視架構](../../mfc/document-view-architecture.md)與文件[列印](../../mfc/printing.md)和[列印︰ 多重頁面文件](../../mfc/multipage-documents.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CPrintInfo`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxext.h  
  
##  <a name="a-namegetfrompagea--cprintinfogetfrompage"></a><a name="getfrompage"></a>CPrintInfo::GetFromPage  
 呼叫此函式以擷取要列印的第一頁的數目。  
  
```  
UINT GetFromPage() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 要列印的第一頁數目。  
  
### <a name="remarks"></a>備註  
 這是使用者在 [列印] 對話方塊中指定的值，而且會儲存在`CPrintDialog`所參考物件`m_pPD`成員。 如果使用者未指定值，預設為文件的第一頁。  
  
##  <a name="a-namegetmaxpagea--cprintinfogetmaxpage"></a><a name="getmaxpage"></a>CPrintInfo::GetMaxPage  
 呼叫此函式可擷取文件的最後一頁的數目。  
  
```  
UINT GetMaxPage() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 文件的最後一頁數目。  
  
### <a name="remarks"></a>備註  
 這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。  
  
##  <a name="a-namegetminpagea--cprintinfogetminpage"></a><a name="getminpage"></a>CPrintInfo::GetMinPage  
 呼叫此函式可擷取文件的第一頁的數目。  
  
```  
UINT GetMinPage() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 文件的第一頁數目。  
  
### <a name="remarks"></a>備註  
 這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。  
  
##  <a name="a-namegetoffsetpagea--cprintinfogetoffsetpage"></a><a name="getoffsetpage"></a>CPrintInfo::GetOffsetPage  
 呼叫此函式可擷取位移，從 DocObject 用戶端列印多個 DocObject 項目時。  
  
```  
UINT GetOffsetPage() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 先前的 DocObject 項目正在列印中結合 DocObject 列印工作的第一頁的頁數。  
  
### <a name="remarks"></a>備註  
 這個值由參考**m_nOffsetPage**成員。 您的文件的第一頁編號**m_nOffsetPage**值 + 1 時列印成 DocObject 與其他使用中的文件。 **M_nOffsetPage**是有效的成員才**m_bDocObject**值是**TRUE**。  
  
##  <a name="a-namegettopagea--cprintinfogettopage"></a><a name="gettopage"></a>CPrintInfo::GetToPage  
 呼叫此函式以擷取要列印的最後一頁的數目。  
  
```  
UINT GetToPage() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 要列印的最後一頁數目。  
  
### <a name="remarks"></a>備註  
 這是使用者在 [列印] 對話方塊中指定的值，而且會儲存在`CPrintDialog`所參考物件`m_pPD`成員。 如果使用者未指定值，預設為文件的最後一頁。  
  
##  <a name="a-namembcontinueprintinga--cprintinfombcontinueprinting"></a><a name="m_bcontinueprinting"></a>CPrintInfo::m_bContinuePrinting  
 包含旗標，指出架構是否應該繼續列印迴圈。  
  
### <a name="remarks"></a>備註  
 如果您要列印時分頁，您可以將這個成員設定**FALSE**在覆寫`CView::OnPrepareDC`一旦達到文件結尾。 您不需要修改此變數，如果您已指定在開始列印工作使用的文件的長度`SetMaxPage`成員函式。 `m_bContinuePrinting`成員是類型的公用變數**BOOL**。  
  
##  <a name="a-namembdirecta--cprintinfombdirect"></a><a name="m_bdirect"></a>CPrintInfo::m_bDirect  
 架構會將這個成員設定為**TRUE**如果 [列印] 對話方塊中將被略過直接列印。**FALSE**否則。  
  
### <a name="remarks"></a>備註  
 [列印] 對話方塊通常略過列印從 shell 或完成列印時使用的命令 ID **ID_FILE_PRINT_DIRECT**。  
  
 您通常不會變更這個成員，但如果您變更，變更之前呼叫[CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting)在覆寫[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)。  
  
##  <a name="a-namembdocobjecta--cprintinfombdocobject"></a><a name="m_bdocobject"></a>CPrintInfo::m_bDocObject  
 包含旗標，指出是否要列印的文件 DocObject。  
  
### <a name="remarks"></a>備註  
 資料成員`m_dwFlags`和**m_nOffsetPage**不正確的除非此旗標是**TRUE**。  
  
##  <a name="a-namembpreviewa--cprintinfombpreview"></a><a name="m_bpreview"></a>CPrintInfo::m_bPreview  
 包含旗標，指出是否要預覽文件。  
  
### <a name="remarks"></a>備註  
 這是由架構取決於哪些執行命令的使用者設定。 [列印] 對話方塊中，不會顯示預覽列印工作。 **M_bPreview**成員是類型的公用變數**BOOL**。  
  
##  <a name="a-namemdwflagsa--cprintinfomdwflags"></a><a name="m_dwflags"></a>CPrintInfo::m_dwFlags  
 包含指定 DocObject 列印作業的旗標的組合。  
  
### <a name="remarks"></a>備註  
 有效的只有當資料成員**m_bDocObject**是**TRUE**。  
  
 旗標可以是一或多個下列值︰  
  
- **PRINTFLAG_MAYBOTHERUSER**  
  
- **PRINTFLAG_PROMPTUSER**  
  
- **PRINTFLAG_USERMAYCHANGEPRINTER**  
  
- **PRINTFLAG_RECOMPOSETODEVICE**  
  
- **PRINTFLAG_DONTACTUALLYPRINT**  
  
- **PRINTFLAG_FORCEPROPERTIES**  
  
- **PRINTFLAG_PRINTTOFILE**  
  
##  <a name="a-namemlpuserdataa--cprintinfomlpuserdata"></a><a name="m_lpuserdata"></a>CPrintInfo::m_lpUserData  
 包含使用者建立的結構的指標。  
  
### <a name="remarks"></a>備註  
 您可以使用此儲存不想將儲存在您的檢視類別的特定列印的資料。 **M_lpUserData**成員是類型的公用變數**LPVOID**。  
  
##  <a name="a-namemncurpagea--cprintinfomncurpage"></a><a name="m_ncurpage"></a>CPrintInfo::m_nCurPage  
 包含目前的頁面數目。  
  
### <a name="remarks"></a>備註  
 這個架構會呼叫`CView::OnPrepareDC`和`CView::OnPrint`一次每一頁的文件中，指定不同的值，這個成員的每次; 其值介於所傳回的值`GetFromPage`所傳回的`GetToPage`。 使用這個成員的覆寫在`CView::OnPrepareDC`和`CView::OnPrint`列印文件指定的頁面。  
  
 第一次叫用預覽模式時，架構會讀取這個成員來決定一開始應該先預覽文件的哪一頁的值。 您可以設定的值，這個成員的覆寫中`CView::OnPreparePrinting`輸入預覽模式時，維護使用者的文件中的目前位置。 `m_nCurPage`成員是類型的公用變數**UINT**。  
  
##  <a name="a-namemnjobnumbera--cprintinfomnjobnumber"></a><a name="m_njobnumber"></a>CPrintInfo::m_nJobNumber  
 指出目前的列印工作的作業系統所指派的工作數目。  
  
### <a name="remarks"></a>備註  
 這個值可能是**SP_ERROR**如果還沒有列印工作 (也就是如果`CPrintInfo`物件新建構，而且尚未使用列印)，或正在啟動工作時發生錯誤。  
  
##  <a name="a-namemnnumpreviewpagesa--cprintinfomnnumpreviewpages"></a><a name="m_nnumpreviewpages"></a>CPrintInfo::m_nNumPreviewPages  
 包含的頁數，顯示在預覽模式。它可以是 1 或 2。  
  
### <a name="remarks"></a>備註  
 **M_nNumPreviewPages**成員是類型的公用變數**UINT**。  
  
##  <a name="a-namemnoffsetpagea--cprintinfomnoffsetpage"></a><a name="m_noffsetpage"></a>CPrintInfo::m_nOffsetPage  
 包含在結合的 DocObject 列印工作之前特定 DocObject 的第一頁的頁數。  
  
##  <a name="a-namemppda--cprintinfomppd"></a><a name="m_ppd"></a>CPrintInfo::m_pPD  
 包含一個指向`CPrintDialog`物件用來顯示列印工作的 [列印] 對話方塊。  
  
### <a name="remarks"></a>備註  
 `m_pPD`成員是宣告為指標的公用變數`CPrintDialog`。  
  
##  <a name="a-namemrectdrawa--cprintinfomrectdraw"></a><a name="m_rectdraw"></a>CPrintInfo::m_rectDraw  
 指定頁面的可用繪圖區域的邏輯座標。  
  
### <a name="remarks"></a>備註  
 您可以在覆寫，請參閱此`CView::OnPrint`。 您可以使用這個成員來追蹤您列印頁首、 頁尾等等之後，仍可以使用哪個區域。 **M_rectDraw**成員是類型的公用變數`CRect`。  
  
##  <a name="a-namemstrpagedesca--cprintinfomstrpagedesc"></a><a name="m_strpagedesc"></a>CPrintInfo::m_strPageDesc  
 包含格式字串，用來顯示頁碼，在預覽列印中;這個字串包含兩個子字串，另一個用於單一頁面上，一個用於雙頁面顯示每個以 '\n' 字元結尾。  
  
### <a name="remarks"></a>備註  
 架構會使用 「 頁面 %u\npages%u-%u\n"做為預設值。 如果您想要以不同格式的頁面數字，指定格式字串中的覆寫`CView::OnPreparePrinting`。 **M_strPageDesc**成員是類型的公用變數`CString`。  
  
##  <a name="a-namesetmaxpagea--cprintinfosetmaxpage"></a><a name="setmaxpage"></a>CPrintInfo::SetMaxPage  
 呼叫此函式可指定文件的最後一頁的數目。  
  
```  
void SetMaxPage(UINT nMaxPage);
```  
  
### <a name="parameters"></a>參數  
 *nMaxPage*  
 文件的最後一頁的數目。  
  
### <a name="remarks"></a>備註  
 這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。 如果文件的長度為已知在列印之前，呼叫此函式的覆寫從`CView::OnPreparePrinting`。 如果文件的長度取決於使用者在 [列印] 對話方塊中指定的設定，會呼叫此函式的覆寫從`CView::OnBeginPrinting`。 如果不知道文件的長度，會在列印之前，使用`m_bContinuePrinting`來控制列印迴圈的成員。  
  
### <a name="example"></a>範例  
  請參閱範例[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)。  
  
##  <a name="a-namesetminpagea--cprintinfosetminpage"></a><a name="setminpage"></a>CPrintInfo::SetMinPage  
 呼叫此函式可指定文件的第一頁的數目。  
  
```  
void SetMinPage(UINT nMinPage);
```  
  
### <a name="parameters"></a>參數  
 *nMinPage*  
 文件的第一頁的數目。  
  
### <a name="remarks"></a>備註  
 頁碼通常從 1 開始。 這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 DIBLOOK](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)   
 [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)   
 [CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)   
 [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)   
 [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)   
 [CView::OnPrint](../../mfc/reference/cview-class.md#onprint)





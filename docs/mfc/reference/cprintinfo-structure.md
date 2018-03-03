---
title: "CPrintInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrintInfo
dev_langs:
- C++
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4943554e67d43b6dc1652a984a0e758af9d6951b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cprintinfo-structure"></a>CPrintInfo 結構
儲存列印或預覽列印工作的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CPrintInfo  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPrintInfo::GetFromPage](#getfrompage)|傳回第一個正在列印的頁面數目。|  
|[CPrintInfo::GetMaxPage](#getmaxpage)|傳回文件的最後一頁的數目。|  
|[CPrintInfo::GetMinPage](#getminpage)|傳回文件的第一頁的數目。|  
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|傳回結合 DocObject 列印工作中列印 DocObject 項目的第一個頁面的上一個頁面數目。|  
|[CPrintInfo::GetToPage](#gettopage)|傳回要列印的最後一頁的數目。|  
|[CPrintInfo::SetMaxPage](#setmaxpage)|設定文件的最後一頁的數目。|  
|[CPrintInfo::SetMinPage](#setminpage)|設定文件的第一頁的數目。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|包含表示架構是否應該繼續列印迴圈的旗標。|  
|[CPrintInfo::m_bDirect](#m_bdirect)|包含旗標，指出是否要列印文件直接 （不顯示 [列印] 對話方塊）。|  
|[CPrintInfo::m_bDocObject](#m_bdocobject)|包含旗標，指出是否要列印的文件 DocObject。|  
|[CPrintInfo::m_bPreview](#m_bpreview)|包含旗標，指出是否要預覽文件。|  
|[CPrintInfo::m_dwFlags](#m_dwflags)|指定 DocObject 列印作業。|  
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|包含使用者所建立的結構的指標。|  
|[CPrintInfo::m_nCurPage](#m_ncurpage)|識別目前列印的頁面數目。|  
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|指定目前的列印工作的作業系統所指派的作業數目|  
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|識別顯示在 [預覽] 視窗中; 中的頁面數目1 或 2。|  
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|結合 DocObject 列印工作中指定特定 DocObject 第一頁的位移。|  
|[CPrintInfo::m_pPD](#m_ppd)|包含的指標`CPrintDialog`物件，用於 [列印] 對話方塊。|  
|[CPrintInfo::m_rectDraw](#m_rectdraw)|指定定義目前的可用頁面區域的矩形。|  
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|包含頁碼顯示格式字串。|  
  
## <a name="remarks"></a>備註  
 `CPrintInfo`是一種結構，而且沒有基底類別。  
  
 Framework 建立的物件`CPrintInfo`每次列印或預覽列印 命令會選擇在命令完成後將其終結。  
  
 `CPrintInfo`包含列印工作，例如為要列印的頁面範圍、 整個和列印工作，例如目前列印頁面的目前狀態的相關資訊。 有些資訊會儲存在相關聯[CPrintDialog](../../mfc/reference/cprintdialog-class.md)物件; 此物件包含使用者在 [列印] 對話方塊中輸入的值。  
  
 A`CPrintInfo`物件架構與您的檢視類別之間傳遞列印程序期間，用來交換兩者之間的資訊。 例如，架構會通知檢視類別的文件列印指派值給哪一頁`m_nCurPage`隸屬`CPrintInfo`; 檢視類別，擷取值，並執行指定的頁面的實際列印。  
  
 另一個範例是所在文件的長度不知道會在列印之前的情況。 在此情況下，檢視類別測試文件結尾的每個列印頁面的時間。 當到達結束時，檢視類別設定`m_bContinuePrinting`隸屬`CPrintInfo`至**FALSE**; 這會通知架構，以停止列印迴圈。  
  
 `CPrintInfo`成員函式由`CView`列在 「 另請參閱。 」 如需 Microsoft Foundation 類別庫所提供的列印架構的詳細資訊，請參閱[框架視窗](../../mfc/frame-windows.md)和[文件/檢視架構](../../mfc/document-view-architecture.md)以及文件[列印](../../mfc/printing.md)和[列印： 多頁文件](../../mfc/multipage-documents.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CPrintInfo`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxext.h  
  
##  <a name="getfrompage"></a>CPrintInfo::GetFromPage  
 呼叫此函式可擷取要列印的第一頁的數目。  
  
```  
UINT GetFromPage() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 若要列印的第一頁數目。  
  
### <a name="remarks"></a>備註  
 這是使用者在 [列印] 對話方塊中所指定的值，而且它會儲存在`CPrintDialog`所參考物件`m_pPD`成員。 如果使用者沒有指定值，則預設為文件的第一頁。  
  
##  <a name="getmaxpage"></a>CPrintInfo::GetMaxPage  
 呼叫此函式可擷取文件的最後一頁的數目。  
  
```  
UINT GetMaxPage() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 文件的最後一頁數目。  
  
### <a name="remarks"></a>備註  
 這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。  
  
##  <a name="getminpage"></a>CPrintInfo::GetMinPage  
 呼叫此函式可擷取文件的第一頁的數目。  
  
```  
UINT GetMinPage() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 文件的第一頁數目。  
  
### <a name="remarks"></a>備註  
 這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。  
  
##  <a name="getoffsetpage"></a>CPrintInfo::GetOffsetPage  
 呼叫此函式可擷取位移列印 DocObject 用戶端從多個 DocObject 項目時。  
  
```  
UINT GetOffsetPage() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 上述結合 DocObject 列印工作中列印 DocObject 項目的第一頁的頁數。  
  
### <a name="remarks"></a>備註  
 這個值由參考**m_nOffsetPage**成員。 您的文件的第一頁編號**m_nOffsetPage**值 + 1 時列印成 DocObject 與其他使用中的文件。 **M_nOffsetPage**成員無效，只有當**m_bDocObject**值是**TRUE**。  
  
##  <a name="gettopage"></a>CPrintInfo::GetToPage  
 呼叫此函式可擷取要列印的最後一頁的數目。  
  
```  
UINT GetToPage() const;

 
```  
  
### <a name="return-value"></a>傳回值  
 若要列印的最後一頁數目。  
  
### <a name="remarks"></a>備註  
 這是使用者在 [列印] 對話方塊中所指定的值，而且它會儲存在`CPrintDialog`所參考物件`m_pPD`成員。 如果使用者沒有指定值，則預設為文件的最後一頁。  
  
##  <a name="m_bcontinueprinting"></a>CPrintInfo::m_bContinuePrinting  
 包含表示架構是否應該繼續列印迴圈的旗標。  
  
### <a name="remarks"></a>備註  
 如果您要列印時分頁，您可以設定此成員為**FALSE**的覆寫中`CView::OnPrepareDC`一旦達到文件結尾。 您沒有修改此變數，如果您已經指定的列印工作使用的開始處的文件長度`SetMaxPage`成員函式。 `m_bContinuePrinting`成員是類型的公用變數**BOOL**。  
  
##  <a name="m_bdirect"></a>CPrintInfo::m_bDirect  
 架構會將這個成員設定為**TRUE**如果直接列印; 將略過 [列印] 對話方塊**FALSE**否則。  
  
### <a name="remarks"></a>備註  
 當您列印從殼層或完成列印時列印 對話方塊通常略過使用的命令 ID **ID_FILE_PRINT_DIRECT**。  
  
 您通常不會變更這個成員，但如果您變更它，將它變更之前呼叫[CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting)的覆寫中[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)。  
  
##  <a name="m_bdocobject"></a>CPrintInfo::m_bDocObject  
 包含旗標，指出是否要列印的文件 DocObject。  
  
### <a name="remarks"></a>備註  
 資料成員`m_dwFlags`和**m_nOffsetPage**是無效的除非此旗標是**TRUE**。  
  
##  <a name="m_bpreview"></a>CPrintInfo::m_bPreview  
 包含旗標，指出是否要預覽文件。  
  
### <a name="remarks"></a>備註  
 這個設定是依據執行命令的使用者架構。 預覽列印工作不會顯示 [列印] 對話方塊。 **M_bPreview**成員是類型的公用變數**BOOL**。  
  
##  <a name="m_dwflags"></a>CPrintInfo::m_dwFlags  
 包含指定 DocObject 列印作業的旗標的組合。  
  
### <a name="remarks"></a>備註  
 只有才有效資料成員**m_bDocObject**是**TRUE**。  
  
 旗標可以是下列一或多個下列值：  
  
- **PRINTFLAG_MAYBOTHERUSER**  
  
- **PRINTFLAG_PROMPTUSER**  
  
- **PRINTFLAG_USERMAYCHANGEPRINTER**  
  
- **PRINTFLAG_RECOMPOSETODEVICE**  
  
- **PRINTFLAG_DONTACTUALLYPRINT**  
  
- **PRINTFLAG_FORCEPROPERTIES**  
  
- **PRINTFLAG_PRINTTOFILE**  
  
##  <a name="m_lpuserdata"></a>CPrintInfo::m_lpUserData  
 包含使用者所建立的結構的指標。  
  
### <a name="remarks"></a>備註  
 這個函數可用來儲存不想儲存您的檢視類別中的列印特定資料。 **M_lpUserData**成員是類型的公用變數**LPVOID**。  
  
##  <a name="m_ncurpage"></a>CPrintInfo::m_nCurPage  
 包含目前的頁面數目。  
  
### <a name="remarks"></a>備註  
 這個架構會呼叫`CView::OnPrepareDC`和`CView::OnPrint`一次每一頁的文件中，指定不同的值，這個成員的每次; 其值的範圍所傳回的值從`GetFromPage`所傳回的`GetToPage`。 使用這個成員的覆寫中`CView::OnPrepareDC`和`CView::OnPrint`列印文件指定的頁面。  
  
 第一次叫用預覽模式時，framework 就會讀取此成員以決定一開始應該先預覽文件的哪一頁的值。 您可以設定的值，這個成員的覆寫中`CView::OnPreparePrinting`輸入預覽模式時，維護使用者的文件中的目前位置。 `m_nCurPage`成員是類型的公用變數**UINT**。  
  
##  <a name="m_njobnumber"></a>CPrintInfo::m_nJobNumber  
 指出目前的列印工作的作業系統所指派的作業數目。  
  
### <a name="remarks"></a>備註  
 這個值可能是**SP_ERROR**如果還沒有列印工作 (亦即，如果`CPrintInfo`新建構物件，以及尚未使用列印)，或如果正在啟動工作時發生錯誤。  
  
##  <a name="m_nnumpreviewpages"></a>CPrintInfo::m_nNumPreviewPages  
 包含在預覽模式; 顯示的頁數它可以是 1 或 2。  
  
### <a name="remarks"></a>備註  
 **M_nNumPreviewPages**成員是類型的公用變數**UINT**。  
  
##  <a name="m_noffsetpage"></a>CPrintInfo::m_nOffsetPage  
 包含在結合 DocObject 列印工作之前特定 DocObject 的第一頁的頁數。  
  
##  <a name="m_ppd"></a>CPrintInfo::m_pPD  
 包含的指標`CPrintDialog`物件用來顯示列印工作的 [列印] 對話方塊。  
  
### <a name="remarks"></a>備註  
 `m_pPD`成員是公用的變數宣告為指標`CPrintDialog`。  
  
##  <a name="m_rectdraw"></a>CPrintInfo::m_rectDraw  
 指定的邏輯座標的可用頁面的繪圖區域。  
  
### <a name="remarks"></a>備註  
 您可能要參考中的覆寫這`CView::OnPrint`。 您可以使用這個成員來追蹤頁首、 頁尾等等，在列印之後，仍可以使用哪一個區域。 **M_rectDraw**成員是類型的公用變數`CRect`。  
  
##  <a name="m_strpagedesc"></a>CPrintInfo::m_strPageDesc  
 包含用來列印的頁碼顯示在預覽列印中; 的格式字串這個字串包含這兩個子字串，一個用於單一頁面顯示，另一個適用於雙頁面顯示每個以 '\n' 字元為結尾。  
  
### <a name="remarks"></a>備註  
 架構會使用 「 頁面 %u\npages%u-%u\n"做為預設值。 如果您想要以不同格式列印的頁碼，指定格式字串中的覆寫`CView::OnPreparePrinting`。 **M_strPageDesc**成員是類型的公用變數`CString`。  
  
##  <a name="setmaxpage"></a>CPrintInfo::SetMaxPage  
 呼叫此函式可指定文件的最後一頁的數目。  
  
```  
void SetMaxPage(UINT nMaxPage);
```  
  
### <a name="parameters"></a>參數  
 *nMaxPage*  
 文件的最後一頁的數目。  
  
### <a name="remarks"></a>備註  
 這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。 如果文件的長度為已知，在列印之前，呼叫此函式的覆寫從`CView::OnPreparePrinting`。 如果文件長度取決於設定指定使用者在 [列印] 對話方塊中，呼叫此函式的覆寫從`CView::OnBeginPrinting`。 如果文件的長度不知道會在列印之前，使用`m_bContinuePrinting`控制列印迴圈的成員。  
  
### <a name="example"></a>範例  
  請參閱範例的[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)。  
  
##  <a name="setminpage"></a>CPrintInfo::SetMinPage  
 呼叫此函式可指定文件的第一頁的數目。  
  
```  
void SetMinPage(UINT nMinPage);
```  
  
### <a name="parameters"></a>參數  
 *nMinPage*  
 文件的第一頁的數目。  
  
### <a name="remarks"></a>備註  
 頁碼通常 1 開始。 這個值會儲存在`CPrintDialog`所參考物件`m_pPD`成員。  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例 DIBLOOK](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)   
 [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)   
 [CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)   
 [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)   
 [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)   
 [CView::OnPrint](../../mfc/reference/cview-class.md#onprint)




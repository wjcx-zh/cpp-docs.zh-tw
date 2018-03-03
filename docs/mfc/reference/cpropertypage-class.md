---
title: "CPropertyPage 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPropertyPage
- AFXDLGS/CPropertyPage
- AFXDLGS/CPropertyPage::CPropertyPage
- AFXDLGS/CPropertyPage::CancelToClose
- AFXDLGS/CPropertyPage::Construct
- AFXDLGS/CPropertyPage::GetPSP
- AFXDLGS/CPropertyPage::OnApply
- AFXDLGS/CPropertyPage::OnCancel
- AFXDLGS/CPropertyPage::OnKillActive
- AFXDLGS/CPropertyPage::OnOK
- AFXDLGS/CPropertyPage::OnQueryCancel
- AFXDLGS/CPropertyPage::OnReset
- AFXDLGS/CPropertyPage::OnSetActive
- AFXDLGS/CPropertyPage::OnWizardBack
- AFXDLGS/CPropertyPage::OnWizardFinish
- AFXDLGS/CPropertyPage::OnWizardNext
- AFXDLGS/CPropertyPage::QuerySiblings
- AFXDLGS/CPropertyPage::SetModified
- AFXDLGS/CPropertyPage::m_psp
dev_langs:
- C++
helpviewer_keywords:
- CPropertyPage [MFC], CPropertyPage
- CPropertyPage [MFC], CancelToClose
- CPropertyPage [MFC], Construct
- CPropertyPage [MFC], GetPSP
- CPropertyPage [MFC], OnApply
- CPropertyPage [MFC], OnCancel
- CPropertyPage [MFC], OnKillActive
- CPropertyPage [MFC], OnOK
- CPropertyPage [MFC], OnQueryCancel
- CPropertyPage [MFC], OnReset
- CPropertyPage [MFC], OnSetActive
- CPropertyPage [MFC], OnWizardBack
- CPropertyPage [MFC], OnWizardFinish
- CPropertyPage [MFC], OnWizardNext
- CPropertyPage [MFC], QuerySiblings
- CPropertyPage [MFC], SetModified
- CPropertyPage [MFC], m_psp
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c42a0ba40797312a2108a288fecdea55c6873f3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cpropertypage-class"></a>CPropertyPage 類別
表示屬性工作表的個別頁面，也稱為索引標籤對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CPropertyPage : public CDialog  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CPropertyPage::CPropertyPage](#cpropertypage)|建構 `CPropertyPage` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPropertyPage::CancelToClose](#canceltoclose)|變更為 關閉，確定 按鈕，並停用取消 5d; 按鈕之後發生無法復原變更的強制回應屬性工作表頁。|  
|[CPropertyPage::Construct](#construct)|建構 `CPropertyPage` 物件。 使用`Construct`如果您想要在執行階段，指定您的參數，或如果您使用的陣列。|  
|[CPropertyPage::GetPSP](#getpsp)|擷取 Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)結構與相關聯`CPropertyPage`物件。|  
|[CPropertyPage::OnApply](#onapply)|按一下 [立即套用] 按鈕時由架構呼叫。|  
|[CPropertyPage::OnCancel](#oncancel)|按一下 [取消] 按鈕時由架構呼叫。|  
|[Cpropertypage:: Onkillactive](#onkillactive)|當目前的頁面已不再使用中的頁面時，由架構呼叫。 此執行資料驗證。|  
|[CPropertyPage::OnOK](#onok)|按一下 確定，立即套用 或 關閉 按鈕時由架構呼叫。|  
|[CPropertyPage::OnQueryCancel](#onquerycancel)|按一下 [取消] 按鈕時，並取消動作發生之前由架構呼叫。|  
|[CPropertyPage::OnReset](#onreset)|按一下 [取消] 按鈕時由架構呼叫。|  
|[Cpropertypage:: Onsetactive](#onsetactive)|頁面進行作用中的頁面時，由架構呼叫。|  
|[CPropertyPage::OnWizardBack](#onwizardback)|當使用精靈類型的屬性工作表，按一下 [上一頁] 按鈕時由架構呼叫。|  
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|當使用精靈類型的屬性工作表，按一下 [完成] 按鈕時由架構呼叫。|  
|[CPropertyPage::OnWizardNext](#onwizardnext)|當使用精靈類型的屬性工作表，按一下 [下一步] 按鈕時由架構呼叫。|  
|[CPropertyPage::QuerySiblings](#querysiblings)|轉寄訊息到屬性工作表的每一頁。|  
|[Cpropertypage:: Setmodified](#setmodified)|呼叫以啟用或停用立即套用 按鈕。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CPropertyPage::m_psp](#m_psp)|Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)結構。 提供基本的屬性頁參數的存取權。|  
  
## <a name="remarks"></a>備註  
 因為標準的對話方塊，以衍生類別，以從`CPropertyPage`屬性工作表中每一頁。 若要使用`CPropertyPage`-衍生的物件第一次建立[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)物件，然後再建立屬性工作表中的每個頁面的物件。 呼叫[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)每個工作表，在頁面上，然後呼叫以顯示屬性工作表[cpropertysheet:: Setwizardmode](../../mfc/reference/cpropertysheet-class.md#domodal)強制回應屬性工作表，或[CPropertySheet::建立](../../mfc/reference/cpropertysheet-class.md#create)非強制回應屬性工作表。  
  
 您可以建立一種稱為精靈，其中包含屬性工作表使用一連串的步驟的作業，例如設定裝置，或建立新聞稿引導使用者的屬性頁 索引標籤對話方塊。 精靈類型索引標籤對話方塊，在屬性頁沒有索引標籤上，而且只有一個屬性頁面會顯示一次。 另外，您不需要 確定 和 立即套用 按鈕，精靈類型索引標籤對話方塊具有 上一頁 按鈕下, 一個 或 完成 5d; 按鈕和 取消 按鈕。  
  
 如需有關如何建立屬性工作表為精靈的詳細資訊，請參閱[cpropertysheet:: Domodal](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。 如需有關使用`CPropertyPage`物件，請參閱文章[屬性工作表和屬性頁](../../mfc/property-sheets-and-property-pages-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CPropertyPage`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdlgs.h  
  
##  <a name="canceltoclose"></a>CPropertyPage::CancelToClose  
 無法復原的變更建立強制回應屬性工作表頁面中的資料之後，請呼叫此函式。  
  
```  
void CancelToClose();
```  
  
### <a name="remarks"></a>備註  
 此函式會將 確定 按鈕變更為 關閉並停用 取消 按鈕。 此變更的警示的變更是永久的修改使用者無法取消。  
  
 `CancelToClose`成員函式不做任何動作在非強制回應屬性工作表中，因為預設的非強制回應屬性工作表沒有 [取消] 按鈕。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPropertyPage::QuerySiblings](#querysiblings)。  
  
##  <a name="construct"></a>CPropertyPage::Construct  
 呼叫此成員函式來建構`CPropertyPage`物件。  
  
```  
void Construct(
    UINT nIDTemplate,  
    UINT nIDCaption = 0);

 
void Construct(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption = 0);

 
void Construct(
    UINT nIDTemplate,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0);

 
void Construct(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0);
```  
  
### <a name="parameters"></a>參數  
 `nIDTemplate`  
 使用此頁面的範本識別碼。  
  
 `nIDCaption`  
 要放置在此頁面的索引標籤名稱的識別碼。 如果為 0，名稱將會取自此頁面的對話方塊範本。  
  
 `lpszTemplateName`  
 包含的範本資源名稱的以 null 結尾字串。  
  
 `nIDHeaderTitle`  
 要放置在屬性頁標頭的標題位置名稱的識別碼。 預設為 0。  
  
 `nIDHeaderSubTitle`  
 要放置在屬性頁標頭的子標題位置名稱的識別碼。 預設為 0。  
  
### <a name="remarks"></a>備註  
 所有下列條件都符合之後，會顯示物件：  
  
-   頁面已加入至屬性工作表使用[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)。  
  
-   屬性工作表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[建立](../../mfc/reference/cpropertysheet-class.md#create)在呼叫函式。  
  
-   使用者選取了 （以索引標籤式） 此頁面。  
  
 呼叫**建構**如果其中一個其他類別建構函式被呼叫。 `Construct`成員函式是有彈性，因為您可以將參數的陳述式保留空白，然後在您的程式碼中指定多個參數和建構在任何時間點。  
  
 您必須使用`Construct`當您使用的陣列，且您必須呼叫**建構**陣列的每個成員，以便將資料成員會指派適當的值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]  
  
##  <a name="cpropertypage"></a>CPropertyPage::CPropertyPage  
 建構 `CPropertyPage` 物件。  
  
```  
CPropertyPage();

 
explicit CPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
explicit CPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
CPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));

 
CPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption,  
    UINT nIDHeaderTitle,  
    UINT nIDHeaderSubTitle = 0,  
    DWORD dwSize = sizeof(PROPSHEETPAGE));
```  
  
### <a name="parameters"></a>參數  
 `nIDTemplate`  
 使用此頁面的範本識別碼。  
  
 `nIDCaption`  
 要放置在此頁面的索引標籤名稱的識別碼。 如果為 0，名稱將會取自此頁面的對話方塊範本。  
  
 `dwSize`  
 `lpszTemplateName`  
 指向字串，包含此頁面範本的名稱。 不能**NULL**。  
  
 `nIDHeaderTitle`  
 要放置在屬性頁標頭的標題位置名稱的識別碼。  
  
 `nIDHeaderSubTitle`  
 要放置在屬性頁標頭的子標題位置名稱的識別碼。  
  
### <a name="remarks"></a>備註  
 所有下列條件都符合之後，會顯示物件：  
  
-   頁面已加入至屬性工作表使用[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)。  
  
-   屬性工作表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[建立](../../mfc/reference/cpropertysheet-class.md#create)在呼叫函式。  
  
-   使用者選取了 （以索引標籤式） 此頁面。  
  
 如果您有多個參數 （例如，如果您使用的陣列） 時，使用[CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct)而不是`CPropertyPage`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]  
  
##  <a name="getpsp"></a>CPropertyPage::GetPSP  
 擷取 Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)結構與相關聯`CPropertyPage`物件。  
  
```  
const PROPSHEETPAGE& GetPSP() const;  
  
PROPSHEETPAGE& GetPSP();
```  
  
### <a name="return-value"></a>傳回值  
 若要參考**PROPSHEETPAGE**結構。  
  
##  <a name="m_psp"></a>CPropertyPage::m_psp  
 `m_psp`是一種結構的成員儲存的特性[PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548)。  
  
```  
PROPSHEETPAGE m_psp;  
```  
  
### <a name="remarks"></a>備註  
 您可以使用此結構來建構後即初始化屬性頁面的外觀。  
  
 如需有關此結構，包括其成員的清單，請參閱**PROPSHEETPAGE** Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]  
  
##  <a name="onapply"></a>CPropertyPage::OnApply  
 此成員函式是由架構呼叫，當使用者選擇 [確定] 或 [立即套用] 按鈕。  
  
```  
virtual BOOL OnApply();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果所做的變更已被接受。否則便是 0。  
  
### <a name="remarks"></a>備註  
 當架構會呼叫此函式時，接受屬性工作表中的所有屬性頁上所做的變更時，屬性工作表會保留焦點，和`OnApply`傳回**TRUE** （值 1）。 之前`OnApply`可以呼叫由架構中，您必須先呼叫[SetModified](#setmodified)並將其參數設定為**TRUE**。 只要使用者在屬性頁上進行變更，這會啟動 [立即套用] 按鈕。  
  
 覆寫此成員函式，來指定當使用者按一下 [立即套用] 按鈕，您的程式會採用的動作。 函式覆寫時，應傳回**TRUE**接受變更並**FALSE**以防止變更生效。  
  
 預設實作`OnApply`呼叫`OnOK`。  
  
 如需傳送使用者屬性工作表中按立即套用或 [確定] 按鈕時的通知訊息的詳細資訊，請參閱[PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552) Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPropertyPage::OnOK](#onok)。  
  
##  <a name="oncancel"></a>CPropertyPage::OnCancel  
 選取 [取消] 按鈕時，此成員函式是由架構呼叫。  
  
```  
virtual void OnCancel();
```  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，執行 [取消] 按鈕。 預設值變換正負號所做的任何變更。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]  
  
##  <a name="onkillactive"></a>Cpropertypage:: Onkillactive  
 當頁面不再使用中的頁面時，此成員函式是由架構呼叫。  
  
```  
virtual BOOL OnKillActive();
```  
  
### <a name="return-value"></a>傳回值  
 如果資料已成功更新，則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，以執行特殊的資料驗證工作。  
  
 此成員函式的預設實作會將設定控制項的屬性頁複製到成員變數的屬性頁。 如果資料未成功更新對話方塊資料驗證 (DDV) 錯誤，因此，頁面會保留焦點。  
  
 此成員函式會成功傳回之後，架構會呼叫在頁面的[OnOK](#onok)函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]  
  
##  <a name="onok"></a>CPropertyPage::OnOK  
 由架構呼叫此成員函式，是當使用者選擇 [確定] 或 [立即套用] 按鈕，這個架構會呼叫之後立即[OnKillActive](#onkillactive)。  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>備註  
 當使用者選擇 [確定] 或 [立即套用] 按鈕時，架構會接收[PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552)在內容頁上的通知。 若要呼叫`OnOK`如果您呼叫不會進行[CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton)因為 [屬性] 頁面不會在此情況下傳送通知。  
  
 覆寫此成員函式，來實作特有目前使用中頁面的其他行為，當使用者關閉整個屬性工作表。  
  
 此成員函式的預設實作會將標示為 「 清除 」 以反映在已更新的資料頁面`OnKillActive`函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]  
  
##  <a name="onquerycancel"></a>CPropertyPage::OnQueryCancel  
 當使用者按一下 [取消] 按鈕，而且之前取消動作發生時，此成員函式是由架構呼叫。  
  
```  
virtual BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>傳回值  
 傳回**FALSE**來避免取消作業或為 TRUE，則允許使用它。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，以指定當使用者按一下 [取消] 按鈕時，程式會採用的動作。  
  
 預設實作`OnQueryCancel`傳回**TRUE**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]  
  
##  <a name="onreset"></a>CPropertyPage::OnReset  
 此成員函式是由架構呼叫，當使用者選擇 [取消] 按鈕。  
  
```  
virtual void OnReset();
```  
  
### <a name="remarks"></a>備註  
 當架構會呼叫此函式時，捨棄所有的屬性頁使用者先前選擇 [立即套用] 按鈕所做的變更，和屬性工作表會保留焦點。  
  
 覆寫此成員函式，來指定程式取得，當使用者按一下 [取消] 按鈕的動作。  
  
 預設實作`OnReset`不做任何動作。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPropertyPage::OnCancel](#oncancel)。  
  
##  <a name="onsetactive"></a>Cpropertypage:: Onsetactive  
 此成員函式是由架構呼叫，當頁面由使用者選擇，並會變成使用中的頁面。  
  
```  
virtual BOOL OnSetActive();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果頁面已成功設定作用中。否則便是 0。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，來啟動頁面時執行工作。 覆寫此成員函式通常會更新資料成員，以允許其以新資料更新頁面控制項之後呼叫的預設版本。  
  
 預設實作會建立於 [頁面] 視窗如果不是先前建立，而且可讓使用中的頁面。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext)。  
  
##  <a name="onwizardback"></a>CPropertyPage::OnWizardBack  
 當使用者按一下精靈中的 [上一頁] 按鈕時，此成員函式是由架構呼叫。  
  
```  
virtual LRESULT OnWizardBack();
```  
  
### <a name="return-value"></a>傳回值  
 0 到自動前進到下一個頁面。若要防止頁面變更為-1。 若要跳至下一個以外的頁面，請傳回要顯示對話方塊的識別項。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，來指定當使用者按下 [上一頁] 按鈕時，必須採取某些動作。  
  
 如需有關如何讓精靈類型的屬性工作表的詳細資訊，請參閱[cpropertysheet:: Domodal](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]  
  
##  <a name="onwizardfinish"></a>CPropertyPage::OnWizardFinish  
 當使用者按一下 [完成] 按鈕，在精靈中時，此成員函式是由架構呼叫。  
  
```  
virtual BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果在精靈完成時，系統會終結屬性工作表否則為零。  
  
### <a name="remarks"></a>備註  
 當使用者按一下**完成**按鈕在精靈中，架構會呼叫此函式; 當`OnWizardFinish`傳回**TRUE** （非零值），屬性工作表也將被銷毀可以 （但實際上並不是終結）。 呼叫`DestroyWindow`終結屬性工作表。 請勿呼叫`DestroyWindow`從`OnWizardFinish`; 這樣做會導致堆積損毀或其他錯誤。  
  
 您可以覆寫此成員函式，來指定當使用者按下 [完成] 按鈕時，必須採取某些動作。 在覆寫這個函式，傳回**FALSE**被終結時，防止屬性工作表。  
  
 如需當使用者按下精靈屬性工作表中的 [完成] 按鈕時傳送通知訊息的詳細資訊，請參閱[PSN_WIZFINISH](http://msdn.microsoft.com/library/windows/desktop/bb774571) Windows SDK 中。  
  
 如需有關如何讓精靈類型的屬性工作表的詳細資訊，請參閱[cpropertysheet:: Domodal](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]  
  
##  <a name="onwizardnext"></a>CPropertyPage::OnWizardNext  
 當使用者按一下 [下一步] 按鈕在精靈中，此成員函式是由架構呼叫。  
  
```  
virtual LRESULT OnWizardNext();
```  
  
### <a name="return-value"></a>傳回值  
 0 到自動前進到下一個頁面。若要防止頁面變更為-1。 若要跳至下一個以外的頁面，請傳回要顯示對話方塊的識別項。  
  
### <a name="remarks"></a>備註  
 覆寫此成員函式，來指定當使用者按 下一步按鈕時，必須採取某些動作。  
  
 如需有關如何讓精靈類型的屬性工作表的詳細資訊，請參閱[cpropertysheet:: Domodal](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]  
  
##  <a name="querysiblings"></a>CPropertyPage::QuerySiblings  
 呼叫此成員函式轉送至屬性工作表中的每個頁面的訊息。  
  
```  
LRESULT QuerySiblings(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 `wParam`  
 指定訊息相關的其他資訊。  
  
 `lParam`  
 指定訊息相關的其他資訊  
  
### <a name="return-value"></a>傳回值  
 為非零，傳回的值從屬性工作表或 0 中的網頁的所有頁面 0 的值。  
  
### <a name="remarks"></a>備註  
 如果頁面傳回則為非零值，屬性工作表不會傳送訊息到後續的頁面。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]  
  
##  <a name="setmodified"></a>Cpropertypage:: Setmodified  
 呼叫此成員函式可啟用或停用 [立即套用] 按鈕，根據屬性頁中的設定是否應該套用到適當的外部物件。  
  
```  
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bChanged`  
 **TRUE**表示屬性頁設定，已修改這些交易套用; 最後一次**FALSE** ，表示屬性頁設定已套用，或應予忽略。  
  
### <a name="remarks"></a>備註  
 架構會持續的追蹤頁面的 「 有所變更 」，也就是，您所呼叫的屬性頁**SetModified (TRUE)**。 立即套用 按鈕將一律會啟用，如果您呼叫**SetModified (TRUE)**的其中一個頁面。 當您呼叫時立即套用 按鈕將會停用**SetModified (FALSE)**的其中一個頁面，但如果沒有任何其他網頁 「 有所變更 」。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例 CMNCTRL1](../../visual-cpp-samples.md)   
 [MFC 範例 CMNCTRL2](../../visual-cpp-samples.md)   
 [MFC 範例 PROPDLG](../../visual-cpp-samples.md)   
 [MFC 範例 SNAPVW](../../visual-cpp-samples.md)   
 [CDialog 類別](../../mfc/reference/cdialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md)   
 [CDialog 類別](../../mfc/reference/cdialog-class.md)

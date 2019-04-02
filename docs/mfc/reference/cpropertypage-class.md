---
title: CPropertyPage 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: 9d4100037c5a6cd2eeef1a50fb2d5a46b2cb6505
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772719"
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
|[CPropertyPage::CancelToClose](#canceltoclose)|變更為 [關閉]，[確定] 按鈕，並停用 [取消] 按鈕，強制回應屬性工作表的頁面中有無法復原的變更之後。|
|[CPropertyPage::Construct](#construct)|建構 `CPropertyPage` 物件。 使用`Construct`如果您想要在執行階段，指定您的參數，或如果您使用的陣列。|
|[CPropertyPage::GetPSP](#getpsp)|擷取 Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2)相關聯的結構`CPropertyPage`物件。|
|[CPropertyPage::OnApply](#onapply)|按一下 [立即套用] 按鈕時由架構呼叫。|
|[CPropertyPage::OnCancel](#oncancel)|按一下 [取消] 按鈕時由架構呼叫。|
|[CPropertyPage::OnKillActive](#onkillactive)|當目前的頁面已不再使用中的頁面時，由架構呼叫。 執行資料驗證。|
|[CPropertyPage::OnOK](#onok)|按一下 確定，立即套用 或 關閉 按鈕時由架構呼叫。|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|按一下 [取消] 按鈕時，並取消動作發生之前由架構呼叫。|
|[CPropertyPage::OnReset](#onreset)|按一下 [取消] 按鈕時由架構呼叫。|
|[CPropertyPage::OnSetActive](#onsetactive)|頁面進行作用中的頁面時，由架構呼叫。|
|[CPropertyPage::OnWizardBack](#onwizardback)|當使用精靈類型的屬性工作表，按一下 [上一頁] 按鈕時由架構呼叫。|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|當使用精靈類型的屬性工作表，按一下 [完成] 按鈕時由架構呼叫。|
|[CPropertyPage::OnWizardNext](#onwizardnext)|當使用精靈類型的屬性工作表，按一下 [下一步] 按鈕時由架構呼叫。|
|[CPropertyPage::QuerySiblings](#querysiblings)|轉寄訊息到每一頁的屬性工作表。|
|[CPropertyPage::SetModified](#setmodified)|呼叫以啟用或停用立即套用 按鈕。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2)結構。 提供基本的屬性頁參數的存取權。|

## <a name="remarks"></a>備註

與標準的對話方塊，您衍生的類別如`CPropertyPage`為您的屬性工作表中的每個頁面。 若要使用`CPropertyPage`-衍生的物件，第一次建立[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)物件，然後再建立屬性工作表中的每個頁面的物件。 呼叫[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)每個工作表，在頁面上，並呼叫，以顯示屬性工作表[cpropertysheet:: Setwizardmode](../../mfc/reference/cpropertysheet-class.md#domodal)強制回應屬性工作表，或[CPropertySheet::建立](../../mfc/reference/cpropertysheet-class.md#create)非強制回應屬性工作表。

您可以建立一種稱為精靈，可引導使用者逐步完成的作業，例如設定裝置，或建立的電子報的屬性頁的序列包含屬性工作表的索引標籤對話方塊。 在精靈輸入 索引標籤對話方塊中，屬性頁沒有索引標籤上，而且只有一個屬性頁面會顯示一次。 此外，不再需要 確定 和 立即套用 按鈕，而精靈類型索引標籤對話方塊具有 上一頁 按鈕、 下一步 或 完成 按鈕和 取消 按鈕。

如需有關如何建立屬性工作表為精靈的詳細資訊，請參閱 < [cpropertysheet:: Domodal](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。 如需有關使用`CPropertyPage`物件，請參閱文章[屬性工作表和屬性頁](../../mfc/property-sheets-and-property-pages-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>需求

**標頭：** afxdlgs.h

##  <a name="canceltoclose"></a>  CPropertyPage::CancelToClose

無法復原的變更已對的強制回應屬性工作表頁中的資料之後，請呼叫此函式。

```
void CancelToClose();
```

### <a name="remarks"></a>備註

此函式會將 確定 按鈕變更為 關閉並停用 取消 按鈕。 這項變更無法取消變更是永久的修改使用者的警示。

`CancelToClose`成員函式不在非強制回應屬性工作表中，執行任何動作，因為預設的非強制回應屬性工作表沒有 [取消] 按鈕。

### <a name="example"></a>範例

  範例，請參閱[CPropertyPage::QuerySiblings](#querysiblings)。

##  <a name="construct"></a>  CPropertyPage::Construct

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

*nIDTemplate*<br/>
此頁面所用的範本識別碼。

*nIDCaption*<br/>
要放在這個頁面的索引標籤名稱的識別碼。 如果為 0，名稱會取自對話方塊範本，此頁面。

*lpszTemplateName*<br/>
包含範本資源的名稱以 null 結束的字串。

*nIDHeaderTitle*<br/>
要放在標題位置，在屬性頁面標頭名稱的識別碼。 根據預設，0。

*nIDHeaderSubTitle*<br/>
要放在子標題的位置，在屬性頁面標頭名稱的識別碼。 根據預設，0。

### <a name="remarks"></a>備註

所有下列條件都符合之後，會顯示物件：

- 頁面已加入至屬性工作表[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)。

- 屬性工作表[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或是[建立](../../mfc/reference/cpropertysheet-class.md#create)在呼叫函式。

- 使用者已選取 （定位至） 此頁面。

呼叫`Construct`如果其中一個其他類別建構函式被呼叫。 `Construct`成員函式是具彈性，因為您可以將參數陳述式保留空白，然後在您的程式碼中指定多個參數並建構在任何時間點。

您必須使用`Construct`當您搭配使用陣列、 且您必須呼叫`Construct`陣列的每個成員，讓資料成員指派適當的值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

##  <a name="cpropertypage"></a>  CPropertyPage::CPropertyPage

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

*nIDTemplate*<br/>
此頁面所用的範本識別碼。

*nIDCaption*<br/>
要放在這個頁面的索引標籤名稱的識別碼。 如果為 0，名稱會取自對話方塊範本，此頁面。

*dwSize*<br/>
*lpszTemplateName*指向字串，包含此頁面範本的名稱。 不可以是 NULL。

*nIDHeaderTitle*<br/>
要放在標題位置，在屬性頁面標頭名稱的識別碼。

*nIDHeaderSubTitle*<br/>
要放在子標題的位置，在屬性頁面標頭名稱的識別碼。

### <a name="remarks"></a>備註

所有下列條件都符合之後，會顯示物件：

- 頁面已加入至屬性工作表[cpropertysheet:: Addpage](../../mfc/reference/cpropertysheet-class.md#addpage)。

- 屬性工作表[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或是[建立](../../mfc/reference/cpropertysheet-class.md#create)在呼叫函式。

- 使用者已選取 （定位至） 此頁面。

如果您有多個參數 （例如，如果您使用的陣列），使用[CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct)而不是`CPropertyPage`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

##  <a name="getpsp"></a>  CPropertyPage::GetPSP

擷取 Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2)相關聯的結構`CPropertyPage`物件。

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>傳回值

參考`PROPSHEETPAGE`結構。

##  <a name="m_psp"></a>  CPropertyPage::m_psp

`m_psp` 是的結構，其成員儲存的特性[PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2)。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>備註

使用此結構來建構後即初始化屬性頁面的外觀。

如需這個結構，包括其成員，清單的詳細資訊，請參閱`PROPSHEETPAGE`Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

##  <a name="onapply"></a>  CPropertyPage::OnApply

此成員函式是由架構呼叫，當使用者選擇 [確定] 或 [立即套用] 按鈕。

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>傳回值

如果接受變更，為非零否則為 0。

### <a name="remarks"></a>備註

當架構會呼叫此函式時，接受在屬性工作表中的所有屬性頁上所做的變更時，屬性工作表會保留焦點，和`OnApply`，則傳回 TRUE （1 的值）。 再`OnApply`可以呼叫由架構中，您必須先呼叫[SetModified](#setmodified)並設定其參數為 TRUE。 當使用者進行變更，在 [屬性] 頁面上，這會啟動 [立即套用] 按鈕。

覆寫此成員函式，指定您的程式在使用者按一下 [立即套用] 按鈕時所採取的動作。 覆寫時，此函數應該傳回 TRUE，以接受變更，而 false 則會防止變更生效。

預設實作`OnApply`呼叫`OnOK`。

如需有關使用者屬性工作表中按 [立即套用] 或 [確定] 按鈕時傳送通知訊息的詳細資訊，請參閱[PSN_APPLY](/windows/desktop/Controls/psn-apply) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CPropertyPage::OnOK](#onok)。

##  <a name="oncancel"></a>  CPropertyPage::OnCancel

選取 [取消] 按鈕時，此成員函式是由架構呼叫。

```
virtual void OnCancel();
```

### <a name="remarks"></a>備註

覆寫此成員函式，執行 [取消] 按鈕的動作。 預設值變換正負號所做的任何變更。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

##  <a name="onkillactive"></a>  CPropertyPage::OnKillActive

此成員函式是由架構呼叫，當頁面不再使用中的頁面。

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>傳回值

非零值，如果資料已成功更新，否則為 0。

### <a name="remarks"></a>備註

覆寫此成員函式，以執行特殊的資料驗證工作。

此成員函式的預設實作會將設定從 [屬性] 頁面中的控制項複製到成員變數的屬性頁。 如果因為對話方塊資料驗證 (DDV) 錯誤，所以未成功更新資料，頁面會保留焦點。

此成員函式會傳回成功之後，架構會在呼叫的頁面[OnOK](#onok)函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

##  <a name="onok"></a>  CPropertyPage::OnOK

當使用者選擇 [確定] 或 [立即套用] 按鈕，這個架構會呼叫之後立即由架構呼叫此成員函式[OnKillActive](#onkillactive)。

```
virtual void OnOK();
```

### <a name="remarks"></a>備註

當使用者選擇 [確定] 或 [立即套用] 按鈕時，架構就會收到[PSN_APPLY](/windows/desktop/Controls/psn-apply)通知從 [屬性] 頁面。 若要在呼叫`OnOK`如果您呼叫不會進行[CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton)因為 [屬性] 頁面不會在此情況下傳送通知。

覆寫此成員函式，以實作特有的目前使用中頁面的其他行為，當使用者關閉整個屬性工作表。

此成員函式的預設實作會將標示為 「 清除 」，以反映在資料已更新頁面`OnKillActive`函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

##  <a name="onquerycancel"></a>  CPropertyPage::OnQueryCancel

當使用者按一下 [取消] 按鈕，並取消之前採取動作的地方，此成員函式是由架構呼叫。

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>傳回值

若要避免取消作業，則為 FALSE 或 TRUE 表示允許它傳回。

### <a name="remarks"></a>備註

覆寫此成員函式，來指定程式在使用者按一下 [取消] 按鈕時所採取的動作。

預設實作`OnQueryCancel`，則傳回 TRUE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

##  <a name="onreset"></a>  CPropertyPage::OnReset

此成員函式是由架構呼叫，當使用者選擇 [取消] 按鈕。

```
virtual void OnReset();
```

### <a name="remarks"></a>備註

時，架構會呼叫此函式，到先前選擇 [立即套用] 按鈕的使用者所做的所有屬性頁面的變更都會被捨棄，和屬性工作表會保留焦點。

覆寫此成員函式，指定程式在使用者按一下 [取消] 按鈕時所採取的動作。

預設實作`OnReset`不執行任何動作。

### <a name="example"></a>範例

  範例，請參閱[CPropertyPage::OnCancel](#oncancel)。

##  <a name="onsetactive"></a>  CPropertyPage::OnSetActive

此成員函式是由架構呼叫，當頁面由使用者選擇而變成使用中的頁面。

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>傳回值

非零值，如果頁面已成功設定為使用中;否則為 0。

### <a name="remarks"></a>備註

覆寫此成員函式，來啟動頁面時執行工作。 此成員函式的覆寫通常會在更新資料成員，才能使用新的資料更新頁面控制項之後呼叫的預設版本。

預設實作建立視窗中的頁面上，如果不是之前建立，並可讓使用中的頁面。

### <a name="example"></a>範例

  範例，請參閱[CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext)。

##  <a name="onwizardback"></a>  CPropertyPage::OnWizardBack

當使用者按一下精靈中的 [上一頁] 按鈕時，此成員函式是由架構呼叫。

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>傳回值

0，會自動前進到下一個頁面中;若要防止頁面變更為-1。 若要跳至下一個以外的頁面，會傳回要顯示對話方塊的識別碼。

### <a name="remarks"></a>備註

覆寫此成員函式，來指定當使用者按下 [上一頁] 按鈕時，必須採取某些動作。

如需有關如何讓精靈類型的屬性工作表的詳細資訊，請參閱 < [cpropertysheet:: Domodal](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

##  <a name="onwizardfinish"></a>  CPropertyPage::OnWizardFinish

當使用者按一下 [完成] 按鈕，在精靈中，此成員函式是由架構呼叫。

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>傳回值

如果屬性工作表損毀，在精靈完成; 時，非零值。否則為零。

### <a name="remarks"></a>備註

當使用者按一下**完成**按鈕，在精靈中，架構會呼叫此函式; 當`OnWizardFinish`則傳回 TRUE （非零值），屬性工作表是能夠將終結 （但並不會實際損毀）。 呼叫`DestroyWindow`終結屬性工作表。 請勿呼叫`DestroyWindow`從`OnWizardFinish`; 這樣會造成堆積損毀或其他錯誤。

您可以覆寫此成員函式，來指定當使用者按下 [完成] 按鈕時，必須採取某些動作。 當覆寫這個函式，會傳回 FALSE，以防止屬性工作表被終結。

如需有關當使用者按下精靈屬性工作表中的 [完成] 按鈕時傳送通知訊息的詳細資訊，請參閱[PSN_WIZFINISH](/windows/desktop/Controls/psn-wizfinish) Windows SDK 中。

如需有關如何讓精靈類型的屬性工作表的詳細資訊，請參閱 < [cpropertysheet:: Domodal](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

##  <a name="onwizardnext"></a>  CPropertyPage::OnWizardNext

當使用者按一下精靈中的 [下一步] 按鈕時，此成員函式是由架構呼叫。

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>傳回值

0，會自動前進到下一個頁面中;若要防止頁面變更為-1。 若要跳至下一個以外的頁面，會傳回要顯示對話方塊的識別碼。

### <a name="remarks"></a>備註

覆寫此成員函式，來指定當使用者按下 [下一步] 按鈕時，必須採取某些動作。

如需有關如何讓精靈類型的屬性工作表的詳細資訊，請參閱 < [cpropertysheet:: Domodal](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

##  <a name="querysiblings"></a>  CPropertyPage::QuerySiblings

呼叫此成員函式，來轉送訊息至屬性工作表中的每個頁面。

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*wParam*<br/>
指定訊息相關的其他資訊。

*lParam*<br/>
指定訊息相關的其他資訊

### <a name="return-value"></a>傳回值

從屬性工作表或 0 中的網頁的非零值的所有頁面都傳回值為 0。

### <a name="remarks"></a>備註

如果頁面傳回非零值，屬性工作表不會傳送訊息至後續頁面。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

##  <a name="setmodified"></a>  CPropertyPage::SetModified

呼叫此成員函式可啟用或停用 [立即套用] 按鈕，根據是否在屬性頁中的設定應該套用到適當的外部物件。

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>參數

*bChanged*<br/>
TRUE 表示的屬性頁設定已遭到修改這些交易套用; 最後一次如果為 false，則表示屬性頁設定已套用，或應該予以忽略。

### <a name="remarks"></a>備註

架構會保留頁面的 「 變更 」，也就是追蹤、 屬性頁，您必須呼叫`SetModified( TRUE )`。 如果您呼叫，就一律會啟用 [立即套用] 按鈕`SetModified( TRUE )`的其中一個頁面。 當您呼叫時立即套用 按鈕將會停用`SetModified( FALSE )`的其中一個頁面，但如果沒有任何其他頁面時才 「 中途 」。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)

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
ms.openlocfilehash: 6a6223708c83f7a5b3e6532a2016660d558f8270
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502798"
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

|名稱|說明|
|----------|-----------------|
|[CPropertyPage::CancelToClose](#canceltoclose)|將 [確定] 按鈕變更為 [關閉], 並停用模式屬性工作表頁面中無法復原的變更之後的 [取消] 按鈕。|
|[CPropertyPage::Construct](#construct)|建構 `CPropertyPage` 物件。 如果`Construct`您想要在執行時間指定參數, 或如果您使用陣列, 請使用。|
|[CPropertyPage::GetPSP](#getpsp)|抓取與`CPropertyPage`物件相關聯的 Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)結構。|
|[CPropertyPage::OnApply](#onapply)|當按一下 [立即套用] 按鈕時, 由架構呼叫。|
|[CPropertyPage::OnCancel](#oncancel)|當按一下 [取消] 按鈕時由架構呼叫。|
|[CPropertyPage::OnKillActive](#onkillactive)|當目前的頁面不再是使用中的頁面時, 由架構呼叫。 在這裡執行資料驗證。|
|[CPropertyPage::OnOK](#onok)|當按一下 [確定]、[立即套用] 或 [關閉] 按鈕時, 由架構呼叫。|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|當按一下 [取消] 按鈕時, 以及在取消動作之前, 由架構呼叫。|
|[CPropertyPage::OnReset](#onreset)|當按一下 [取消] 按鈕時由架構呼叫。|
|[CPropertyPage::OnSetActive](#onsetactive)|當頁面設為使用中頁面時由架構呼叫。|
|[CPropertyPage::OnWizardBack](#onwizardback)|在使用 wizard 類型的屬性工作表時, 按一下 [上一頁] 按鈕時由架構呼叫。|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|在使用 wizard 類型的屬性工作表時, 按一下 [完成] 按鈕時由架構呼叫。|
|[CPropertyPage::OnWizardNext](#onwizardnext)|在使用 wizard 類型的屬性工作表時, 按一下 [下一步] 按鈕時由架構呼叫。|
|[CPropertyPage::QuerySiblings](#querysiblings)|將訊息轉送至屬性工作表的每個頁面。|
|[CPropertyPage::SetModified](#setmodified)|呼叫以啟用或停用 [立即套用] 按鈕。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)結構。 提供基本屬性頁參數的存取權。|

## <a name="remarks"></a>備註

如同標準對話方塊, 您可以從`CPropertyPage`為屬性工作表中的每個頁面衍生一個類別。 若要`CPropertyPage`使用衍生物件, 請先建立[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)物件, 然後為屬性工作表中的每個頁面建立物件。 針對工作表中的每個頁面呼叫[CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) , 然後藉由呼叫模式屬性工作表的[CPropertySheet::D omodal](../../mfc/reference/cpropertysheet-class.md#domodal) , 或針對非模式屬性工作表的[CPropertySheet:: Create](../../mfc/reference/cpropertysheet-class.md#create) , 顯示內容表。

您可以建立一個稱為「wizard」的 [索引標籤] 對話方塊, 其中包含具有一系列屬性頁的屬性工作表, 可引導使用者完成作業的步驟, 例如設定裝置或建立電子報。 在 [wizard-類型] 索引標籤對話方塊中, 屬性頁沒有索引標籤, 而且一次只能顯示一個屬性頁。 此外, [wizard type] 索引標籤對話方塊會有 [上一頁] 按鈕、[下一步] 或 [完成] 按鈕和 [取消] 按鈕, 而不是 [確定] 和 [立即套用] 按鈕。

如需將屬性工作表建立為 wizard 的詳細資訊, 請參閱[CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。 如需使用`CPropertyPage`物件的詳細資訊, 請參閱[屬性工作表和屬性頁](../../mfc/property-sheets-and-property-pages-in-mfc.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>需求

**標頭:** afxdlgs。h

##  <a name="canceltoclose"></a>CPropertyPage:: CancelToClose

在對模式屬性工作表的頁面中的資料進行無法復原的變更之後, 呼叫此函式。

```
void CancelToClose();
```

### <a name="remarks"></a>備註

此函式會變更 [確定] 按鈕, 以關閉並停用 [取消] 按鈕。 這種變更會向使用者通知變更為永久性, 而且無法取消修改。

`CancelToClose`成員函式不會在非模式屬性工作表中執行任何操作, 因為非模式屬性工作表預設不會有 [取消] 按鈕。

### <a name="example"></a>範例

  請參閱[CPropertyPage:: QuerySiblings](#querysiblings)的範例。

##  <a name="construct"></a>CPropertyPage:: 結構

呼叫這個成員函式以建立`CPropertyPage`物件。

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
此頁面所使用之範本的識別碼。

*nIDCaption*<br/>
要放置在此頁面索引標籤中的名稱識別碼。 如果是 0, 則會從這個頁面的對話方塊範本取得名稱。

*lpszTemplateName*<br/>
包含以 null 終止的字串, 這是範本資源的名稱。

*nIDHeaderTitle*<br/>
要放在屬性頁標頭之標題位置的名稱識別碼。 預設為0。

*nIDHeaderSubTitle*<br/>
要放在屬性頁標題之副標題位置的名稱識別碼。 預設為0。

### <a name="remarks"></a>備註

符合下列所有條件之後, 就會顯示物件:

- 已使用[CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)將頁面新增至屬性工作表。

- 已呼叫屬性工作表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[Create](../../mfc/reference/cpropertysheet-class.md#create)函式。

- 使用者已選取 (索引標籤式) 此頁面。

如果`Construct`未呼叫其中一個其他類別的函式, 請呼叫。 `Construct`成員函式很有彈性, 因為您可以將參數語句保留空白, 然後在程式碼中的任何時間點指定多個參數和結構。

當您使用`Construct`陣列時, 必須使用, 而且您必須針對`Construct`陣列的每個成員呼叫, 以便將適當的值指派給資料成員。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

##  <a name="cpropertypage"></a>CPropertyPage:: CPropertyPage

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
此頁面所使用之範本的識別碼。

*nIDCaption*<br/>
要放置在此頁面索引標籤中的名稱識別碼。 如果是 0, 則會從這個頁面的對話方塊範本取得名稱。

*dwSize*<br/>
*lpszTemplateName*指向包含此頁面之範本名稱的字串。 不可以是 NULL。

*nIDHeaderTitle*<br/>
要放在屬性頁標頭之標題位置的名稱識別碼。

*nIDHeaderSubTitle*<br/>
要放在屬性頁標題之副標題位置的名稱識別碼。

### <a name="remarks"></a>備註

符合下列所有條件之後, 就會顯示物件:

- 已使用[CPropertySheet:: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)將頁面新增至屬性工作表。

- 已呼叫屬性工作表的[DoModal](../../mfc/reference/cpropertysheet-class.md#domodal)或[Create](../../mfc/reference/cpropertysheet-class.md#create)函式。

- 使用者已選取 (索引標籤式) 此頁面。

如果您有多個參數 (例如, 如果您使用的是陣列), 請使用[CPropertySheet:: 結構](../../mfc/reference/cpropertysheet-class.md#construct), `CPropertyPage`而不是。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

##  <a name="getpsp"></a>CPropertyPage:: GetPSP

抓取與`CPropertyPage`物件相關聯的 Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)結構。

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>傳回值

`PROPSHEETPAGE`結構的參考。

##  <a name="m_psp"></a>CPropertyPage:: m_psp

`m_psp`是一種結構, 其成員會儲存[PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)的特性。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>備註

使用此結構來初始化屬性頁在建立後的外觀。

如需此結構的詳細資訊, 包括其成員的清單, 請`PROPSHEETPAGE`參閱 Windows SDK 中的。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

##  <a name="onapply"></a>CPropertyPage:: OnApply

當使用者選擇 [確定] 或 [立即套用] 按鈕時, 架構會呼叫這個成員函式。

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>傳回值

如果接受變更, 則為非零值;否則為0。

### <a name="remarks"></a>備註

當架構呼叫此函式時, 會接受在屬性工作表中對所有屬性頁所做的變更, 屬性工作表會保留`OnApply`焦點, 並傳回 TRUE (值 1)。 在`OnApply`可由架構呼叫之前, 您必須先呼叫[SetModified](#setmodified) , 並將其參數設定為 TRUE。 這會在使用者于屬性頁上進行變更時立即啟用 [立即套用] 按鈕。

覆寫此成員函式, 以指定當使用者按一下 [立即套用] 按鈕時, 您的程式所採取的動作。 覆寫時, 函式應該傳回 TRUE 以接受變更, FALSE 則會防止變更生效。

預設的`OnApply`呼叫`OnOK`執行。

如需使用者在屬性工作表中按下 [立即套用] 或 [確定] 按鈕時所傳送之通知訊息的詳細資訊, 請參閱 Windows SDK 中的[PSN_APPLY](/windows/win32/Controls/psn-apply) 。

### <a name="example"></a>範例

  請參閱[CPropertyPage:: OnOK](#onok)的範例。

##  <a name="oncancel"></a>CPropertyPage:: OnCancel

選取 [取消] 按鈕時, 架構會呼叫這個成員函式。

```
virtual void OnCancel();
```

### <a name="remarks"></a>備註

覆寫此成員函式以執行 [取消] 按鈕動作。 預設會否定已進行的任何變更。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

##  <a name="onkillactive"></a>CPropertyPage:: OnKillActive

當頁面不再是使用中的頁面時, 架構會呼叫這個成員函式。

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>傳回值

如果成功更新資料, 則為非零, 否則為0。

### <a name="remarks"></a>備註

覆寫這個成員函式以執行特殊的資料驗證工作。

這個成員函式的預設實作用會將設定從屬性頁中的控制項複製到屬性頁的成員變數。 如果資料因為對話方塊資料驗證 (DDV) 錯誤而未成功更新, 則頁面會保留焦點。

在此成員函式傳回成功之後, 架構會呼叫頁面的[OnOK](#onok)函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

##  <a name="onok"></a>CPropertyPage:: OnOK

當使用者在架構呼叫[OnKillActive](#onkillactive)之後, 立即選擇 [確定] 或 [立即套用] 按鈕時, 架構會呼叫這個成員函式。

```
virtual void OnOK();
```

### <a name="remarks"></a>備註

當使用者選擇 [確定] 或 [立即套用] 按鈕時, 架構會從屬性頁接收[PSN_APPLY](/windows/win32/Controls/psn-apply)通知。 如果您呼叫`OnOK` [CPropertySheet::P ressbutton](../../mfc/reference/cpropertysheet-class.md#pressbutton) , 將不會進行呼叫, 因為屬性頁不會在該情況下傳送通知。

當使用者關閉整個屬性工作表時, 請覆寫這個成員函式, 以執行目前使用中頁面的其他特定行為。

此成員函式的預設執行會將頁面標示為「清除」, 以反映該資料已在函`OnKillActive`式中更新。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

##  <a name="onquerycancel"></a>CPropertyPage:: OnQueryCancel

當使用者按一下 [取消] 按鈕時, 以及在取消動作執行之前, 架構會呼叫這個成員函式。

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>傳回值

傳回 FALSE 以防止取消作業, 或傳回 TRUE 來允許它。

### <a name="remarks"></a>備註

覆寫這個成員函式, 以指定當使用者按一下 [取消] 按鈕時, 程式所採取的動作。

的預設實`OnQueryCancel`值會傳回 TRUE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

##  <a name="onreset"></a>CPropertyPage:: OnReset

當使用者選擇 [取消] 按鈕時, 架構會呼叫這個成員函式。

```
virtual void OnReset();
```

### <a name="remarks"></a>備註

當架構呼叫此函式時, 使用者先前選擇 [立即套用] 按鈕所做的所有屬性頁變更都會被捨棄, 且屬性工作表會保留焦點。

覆寫這個成員函式, 以指定當使用者按一下 [取消] 按鈕時, 程式所採取的動作。

的預設`OnReset`執行不會執行任何操作。

### <a name="example"></a>範例

  請參閱[CPropertyPage:: OnCancel](#oncancel)的範例。

##  <a name="onsetactive"></a>CPropertyPage:: OnSetActive

當使用者選擇頁面時, 架構會呼叫這個成員函式, 並成為使用中的頁面。

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>傳回值

如果已成功設定頁面, 則為非零值;否則為0。

### <a name="remarks"></a>備註

當網頁啟動時, 覆寫此成員函式以執行工作。 您在更新資料成員之後, 此成員函式的覆寫通常會呼叫預設版本, 讓它能夠以新的資料更新頁面控制項。

預設的執行會建立頁面的視窗 (如果先前未建立), 並將它變成使用中的頁面。

### <a name="example"></a>範例

  請參閱[CPropertySheet:: SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext)的範例。

##  <a name="onwizardback"></a>CPropertyPage:: OnWizardBack

當使用者按一下 wizard 中的 [上一頁] 按鈕時, 架構會呼叫這個成員函式。

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>傳回值

0會自動前進到下一個頁面;-1 以防止頁面變更。 若要跳至下一頁以外的頁面, 請傳回要顯示之對話方塊的識別碼。

### <a name="remarks"></a>備註

覆寫這個成員函式, 以指定當按下 [上一頁] 按鈕時, 使用者必須採取的動作。

如需如何建立 wizard 類型屬性工作表的詳細資訊, 請參閱[CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

##  <a name="onwizardfinish"></a>CPropertyPage:: OnWizardFinish

當使用者按一下 wizard 中的 [完成] 按鈕時, 架構會呼叫這個成員函式。

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>傳回值

如果在 wizard 完成時終結屬性工作表則為非零, 否則為。否則為零。

### <a name="remarks"></a>備註

當使用者按一下 wizard 中的 [**完成]** 按鈕時, 架構會呼叫這個函式;當`OnWizardFinish`傳回 TRUE (非零值) 時, 可以終結屬性工作表 (但實際上並不會損毀)。 呼叫`DestroyWindow`以摧毀屬性工作表。 請勿從`DestroyWindow` `OnWizardFinish`呼叫; 這麼做會造成堆積損毀或其他錯誤。

您可以覆寫這個成員函式, 以指定當按下 [完成] 按鈕時, 使用者必須採取的動作。 覆寫這個函式時, 會傳回 FALSE, 以防止屬性工作表遭到終結。

如需使用者按下 wizard 屬性工作表中的 [完成] 按鈕時所傳送之通知訊息的詳細資訊, 請參閱 Windows SDK 中的[PSN_WIZFINISH](/windows/win32/Controls/psn-wizfinish) 。

如需如何建立 wizard 類型屬性工作表的詳細資訊, 請參閱[CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

##  <a name="onwizardnext"></a>CPropertyPage:: OnWizardNext

當使用者按一下嚮導中的 [下一步] 按鈕時, 架構會呼叫這個成員函式。

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>傳回值

0會自動前進到下一個頁面;-1 以防止頁面變更。 若要跳至下一頁以外的頁面, 請傳回要顯示之對話方塊的識別碼。

### <a name="remarks"></a>備註

覆寫這個成員函式, 以指定當按下 [下一步] 按鈕時, 使用者必須採取的動作。

如需如何建立 wizard 類型屬性工作表的詳細資訊, 請參閱[CPropertySheet:: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

##  <a name="querysiblings"></a>CPropertyPage:: QuerySiblings

呼叫這個成員函式, 將訊息轉送至屬性工作表中的每個頁面。

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*wParam*<br/>
指定與訊息相關的其他資訊。

*lParam*<br/>
指定與訊息相關的其他資訊

### <a name="return-value"></a>傳回值

來自屬性工作表中頁面的非零值, 如果所有頁面都傳回0值, 則為0。

### <a name="remarks"></a>備註

如果頁面傳回非零值, 則屬性工作表不會將訊息傳送至後續頁面。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

##  <a name="setmodified"></a>CPropertyPage:: SetModified

根據屬性頁中的設定是否應該套用至適當的外部物件, 呼叫這個成員函式來啟用或停用 [立即套用] 按鈕。

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>參數

*bChanged*<br/>
TRUE 表示屬性頁設定自上次套用之後已經修改;FALSE 表示已套用屬性頁設定, 或應予以忽略。

### <a name="remarks"></a>備註

架構會持續追蹤哪些頁面是「已變更」, 也就是您已呼叫`SetModified( TRUE )`的屬性頁。 如果您呼叫`SetModified( TRUE )`其中一個頁面, 一律會啟用 [立即套用] 按鈕。 當您呼叫`SetModified( FALSE )`其中一個頁面時, 只會停用 [立即套用] 按鈕, 但只有在沒有其他頁面「已變更」時, 才會停用。

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

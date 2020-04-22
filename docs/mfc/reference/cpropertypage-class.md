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
ms.openlocfilehash: f46566eb562f1515e98aedf938ca68b225ee1b67
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751097"
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
|[C 屬性頁:C屬性頁](#cpropertypage)|建構 `CPropertyPage` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 屬性頁::取消關閉](#canceltoclose)|在模態屬性表頁面發生不可恢復更改後,將"確定"按鈕更改為"關閉",並禁用"取消"按鈕。|
|[C 屬性頁:建構](#construct)|建構 `CPropertyPage` 物件。 `Construct`如果要在運行時指定參數,或者使用陣列,請使用。|
|[C 屬性頁:取得 PSP](#getpsp)|檢索與`CPropertyPage`物件關聯的 Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)結構。|
|[C屬性頁::在申請上](#onapply)|按下「立即應用」按鈕時由框架調用。|
|[C 屬性頁:開啟取消](#oncancel)|按下「取消」按鈕時由框架呼叫。|
|[C 屬性頁:在活動](#onkillactive)|當當前頁面不再是活動頁時,由框架調用。 在此處執行數據驗證。|
|[C 屬性頁:ONOK](#onok)|按下「確定」「立即應用」或「關閉」按鈕時,由框架調用。|
|[C 屬性頁:在查詢取消](#onquerycancel)|按下「取消」按鈕時和取消發生之前,由框架調用。|
|[C 屬性頁:開啟重設](#onreset)|按下「取消」按鈕時由框架呼叫。|
|[C 屬性頁開啟活動](#onsetactive)|當頁面成為活動頁時,由框架調用。|
|[C屬性頁::在嚮導背面](#onwizardback)|使用嚮導類型屬性表按兩擊「後退」按鈕時,由框架調用。|
|[C 屬性頁:在精靈完成](#onwizardfinish)|使用嚮導類型屬性表按兩擊"完成"按鈕時,由框架調用。|
|[C屬性頁::在精靈下一頁](#onwizardnext)|使用嚮導類型屬性表按下「下一步」按鈕時,由框架調用。|
|[C 屬性頁:查詢同級](#querysiblings)|將消息轉發到屬性表的每個頁面。|
|[C 屬性頁::已修改](#setmodified)|呼叫以啟動或停用「立即應用」按鈕。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C 屬性頁:m_psp](#m_psp)|Windows [PROPPAGE 結構](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)。 提供對基本屬性頁參數的訪問。|

## <a name="remarks"></a>備註

與標準對話框一樣,從屬性表中的每個頁面`CPropertyPage`派生一個類。 要使用`CPropertyPage`派生物件,請先創建[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)物件,然後為屬性表中的每個頁面創建一個物件。 呼叫[CPropertySheet::為工作表中的每個頁面新增 Page,](../../mfc/reference/cpropertysheet-class.md#addpage)然後透過呼叫模式屬性表的[CPropertySheet::DoModal)](../../mfc/reference/cpropertysheet-class.md#domodal)或[CPropertySheet::為](../../mfc/reference/cpropertysheet-class.md#create)無模式屬性表創建來顯示屬性表。

您可以創建稱為嚮導的選項卡對話框類型,該對話方塊由包含一系列屬性頁的屬性表組成,該屬性頁指導使用者完成操作的步驟,例如設置設備或創建新聞稿。 在嚮導類型選項卡對話方塊中,屬性頁沒有選項卡,並且一次只能看到一個屬性頁。 此外,嚮導類型選項卡對話框沒有"確定"和"立即應用"按鈕,而是具有"後退"按鈕、"下一步"或"完成"按鈕以及"取消"按鈕。

有關將屬性表設定為精靈的詳細資訊,請參閱[CPropertySheet:setWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。 有關使用`CPropertyPage`物件的詳細資訊,請參閱文章[「屬性表」和「屬性頁](../../mfc/property-sheets-and-property-pages-in-mfc.md)」。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>需求

**標題:** afxdlgs.h

## <a name="cpropertypagecanceltoclose"></a><a name="canceltoclose"></a>C 屬性頁::取消關閉

對模態屬性表頁面中的數據進行了不可恢復的更改後,請調用此函數。

```cpp
void CancelToClose();
```

### <a name="remarks"></a>備註

此功能將「確定」按鈕更改為"關閉"並禁用"取消"按鈕。 此更改提醒使用者更改是永久性的,並且無法取消修改。

成員`CancelToClose`函數在無模式屬性表中不執行任何操作,因為默認情況下,無模式屬性表沒有"取消"按鈕。

### <a name="example"></a>範例

  請參考[CPropertyPage:查詢同級的範例](#querysiblings)。

## <a name="cpropertypageconstruct"></a><a name="construct"></a>C 屬性頁:建構

呼叫此成員函數以建構物件`CPropertyPage`。

```cpp
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
用於此頁面的範本的 ID。

*nIDCaption*<br/>
要放置在此頁選項卡中的名稱的 ID。 如果為 0,則名稱將從此頁面的對話方塊樣本中獲取。

*lpszTemplate 名稱*<br/>
包含一個 null 連接端字串,該字串是樣本資源的名稱。

*nIDHeader標題*<br/>
要放置在屬性頁頁頁標題的標題位置的名稱的 ID。 默認情況下,0。

*nIDHeader 子標題*<br/>
要放置在屬性頁頁標題的字幕位置的名稱的 ID。 默認情況下,0。

### <a name="remarks"></a>備註

滿足以下所有條件後,將顯示該物件:

- 該頁已使用[CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)添加到屬性表。

- 屬性表的[「DoModal」](../../mfc/reference/cpropertysheet-class.md#domodal)或[「創建」](../../mfc/reference/cpropertysheet-class.md#create)函數已呼叫。

- 使用者已選擇(選項卡到)此頁面。

如果`Construct`尚未調用其他類構造函數之一,則調用。 `Construct`成員函數是靈活的,因為您可以將參數語句留空,然後在代碼中的任何點指定多個參數和構造。

在使用陣列`Construct`時必須使用,並且必須調`Construct`用 陣列的每個成員,以便為數據成員分配正確的值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

## <a name="cpropertypagecpropertypage"></a><a name="cpropertypage"></a>C 屬性頁:C屬性頁

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
用於此頁面的範本的 ID。

*nIDCaption*<br/>
要放置在此頁選項卡中的名稱的 ID。 如果為 0,則名稱將從此頁面的對話方塊樣本中獲取。

*dwSize*<br/>
*lpszTemplate 名稱*指向包含此頁面樣本名稱的字串。 不能是 NULL。

*nIDHeader標題*<br/>
要放置在屬性頁頁頁標題的標題位置的名稱的 ID。

*nIDHeader 子標題*<br/>
要放置在屬性頁頁標題的字幕位置的名稱的 ID。

### <a name="remarks"></a>備註

滿足以下所有條件後,將顯示該物件:

- 該頁已使用[CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage)添加到屬性表。

- 屬性表的[「DoModal」](../../mfc/reference/cpropertysheet-class.md#domodal)或[「創建」](../../mfc/reference/cpropertysheet-class.md#create)函數已呼叫。

- 使用者已選擇(選項卡到)此頁面。

如果有多個參數(例如,如果您正在使用陣列),請使用[CPropertySheet::建構](../../mfc/reference/cpropertysheet-class.md#construct)而不是`CPropertyPage`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

## <a name="cpropertypagegetpsp"></a><a name="getpsp"></a>C 屬性頁:取得 PSP

檢索與`CPropertyPage`物件關聯的 Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)結構。

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>傳回值

對結構的`PROPSHEETPAGE`引用。

## <a name="cpropertypagem_psp"></a><a name="m_psp"></a>C 屬性頁:m_psp

`m_psp`是一個結構,其成員存儲[PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2)的特徵。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>備註

使用此結構在構造屬性頁后初始化屬性頁的外觀。

有關此結構的詳細資訊(包括其成員的清單),請參閱`PROPSHEETPAGE`Windows SDK。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

## <a name="cpropertypageonapply"></a><a name="onapply"></a>C屬性頁::在申請上

當使用者選擇"確定"或"立即應用"按鈕時,框架將調用此成員函數。

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>傳回值

如果接受更改,則非零;否則 0。

### <a name="remarks"></a>備註

當框架調用此函數時,接受在屬性表中的所有屬性頁上所做的更改,屬性表將保留焦點,並`OnApply`返回 TRUE(值 1)。 在`OnApply`框架可以調用之前,必須調用[Set修改](#setmodified)並將其參數設置為 TRUE。 當使用者在屬性頁上進行更改時,這將啟動"立即應用"按鈕。

覆蓋此成員函數,以指定當使用者按下「立即應用」按鈕時程式執行的操作。 重寫時,函數應返回 TRUE 以接受更改和 FALSE,以防止更改生效。

調用`OnApply``OnOK`的默認實現。

有關使用者在屬性表中按下「立即應用」或「確定」按鈕時發送的通知訊息的詳細資訊,請參閱 Windows SDK 中的[PSN_APPLY。](/windows/win32/Controls/psn-apply)

### <a name="example"></a>範例

  請參考[CPropertyPage 範例::OnOK](#onok)。

## <a name="cpropertypageoncancel"></a><a name="oncancel"></a>C 屬性頁:開啟取消

選擇"取消"按鈕時,框架將調用此成員函數。

```
virtual void OnCancel();
```

### <a name="remarks"></a>備註

覆蓋此成員函數以執行"取消"按鈕操作。 默認值將否定已進行的任何更改。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

## <a name="cpropertypageonkillactive"></a><a name="onkillactive"></a>C 屬性頁:在活動

當頁面不再是活動頁時,框架將調用此成員函數。

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>傳回值

如果數據已成功更新,則非零,否則為 0。

### <a name="remarks"></a>備註

重寫此成員函數以執行特殊的資料驗證任務。

此成員函數的預設實現將設置從屬性頁的控制項複製到屬性頁的成員變數。 如果由於對話框數據驗證 (DDV) 錯誤而未成功更新數據,則頁面將保留焦點。

此成員函數成功返回後,框架將調用頁面的[OnOK](#onok)函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

## <a name="cpropertypageonok"></a><a name="onok"></a>C 屬性頁:ONOK

當用戶選擇"確定"或"立即申請"按鈕時,在框架調用[OnKillActive](#onkillactive)之後,框架會調用此成員函數。

```
virtual void OnOK();
```

### <a name="remarks"></a>備註

當使用者選擇"確定"或"立即應用"按鈕時,框架將從屬性頁收到[PSN_APPLY](/windows/win32/Controls/psn-apply)通知。 如果您調用`OnOK`[CPropertySheet::PresButton,](../../mfc/reference/cpropertysheet-class.md#pressbutton)則不會調用 to,因為在這種情況下,屬性頁不會發送通知。

重寫此成員函數,在使用者關閉整個屬性表時實現特定於當前活動頁的其他行為。

此成員函數的預設實現將頁面標記為"乾淨",以反映數據在`OnKillActive`函數中已更新。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

## <a name="cpropertypageonquerycancel"></a><a name="onquerycancel"></a>C 屬性頁:在查詢取消

當用戶按下「取消」按鈕並在執行取消操作之前,框架將調用此成員函數。

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>傳回值

返回 FALSE 以防止取消操作或 TRUE 以允許它。

### <a name="remarks"></a>備註

覆蓋此成員函數以指定程式在使用者按下「取消」按鈕時執行的操作。

預設實現`OnQueryCancel`返回 TRUE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

## <a name="cpropertypageonreset"></a><a name="onreset"></a>C 屬性頁:開啟重設

當用戶選擇"取消"按鈕時,框架將調用此成員函數。

```
virtual void OnReset();
```

### <a name="remarks"></a>備註

當框架調用此函數時,將放棄使用者以前選擇"立即應用"按鈕所做的所有屬性頁的更改,並且屬性表將保留焦點。

覆蓋此成員函數以指定當用戶按下「取消」按鈕時程式執行的操作。

的`OnReset`默認實現不執行任何操作。

### <a name="example"></a>範例

  請參考[CPropertyPage 範例:開啟取消](#oncancel)。

## <a name="cpropertypageonsetactive"></a><a name="onsetactive"></a>C 屬性頁開啟活動

當用戶選擇頁面並成為活動頁時,框架將調用此成員函數。

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>傳回值

如果頁面已成功設置為活動,則非零;否則 0。

### <a name="remarks"></a>備註

覆蓋此成員函數,以在啟動頁面時執行任務。 重寫此成員函數通常會在更新數據成員後調用預設版本,以允許它使用新數據更新頁面控制項。

預設實現為頁面創建視窗(如果不是以前創建)並使其成為活動頁。

### <a name="example"></a>範例

  請參閱[CPropertySheet 的範例:setFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext)。

## <a name="cpropertypageonwizardback"></a><a name="onwizardback"></a>C屬性頁::在嚮導背面

當用戶單擊嚮導中的"後退"按鈕時,框架將調用此成員函數。

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>傳回值

0 自動前進到下一頁;-1 以防止頁面更改。 要跳到下一個頁面以外的頁面,傳回要顯示的對話框的標識符。

### <a name="remarks"></a>備註

重寫此成員函數以指定按下"後退"按鈕時用戶必須執行的操作。

有關如何創建精靈類型屬性表的詳細資訊,請參閱[CPropertySheet:setWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

## <a name="cpropertypageonwizardfinish"></a><a name="onwizardfinish"></a>C 屬性頁:在精靈完成

當用戶單擊嚮導中的"完成"按鈕時,框架將調用此成員函數。

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>傳回值

如果屬性表在嚮導完成時銷毀,則非零;否則為零。

### <a name="remarks"></a>備註

當使用者按一下精靈中的「完成」按鈕時,框架將呼叫此函數;當使用者按一下精靈中的 **「完成」** 按鈕時,框架將呼叫此函數。當`OnWizardFinish`返回 TRUE(非零值)時,屬性表可以銷毀(但實際上不會銷毀)。 調用`DestroyWindow`以銷毀屬性表。 不要從`OnWizardFinish``DestroyWindow`撥打 。這樣做將導致堆損壞或其他錯誤。

您可以重寫此成員函數,以指定使用者在按下"完成"按鈕時必須執行的操作。 重寫此函數時,返回 FALSE 以防止屬性表被銷毀。

有關使用者在嚮導屬性表中按下"完成"按鈕時發送的通知消息的詳細資訊,請參閱 Windows SDK 中的[PSN_WIZFINISH。](/windows/win32/Controls/psn-wizfinish)

有關如何創建精靈類型屬性表的詳細資訊,請參閱[CPropertySheet:setWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

## <a name="cpropertypageonwizardnext"></a><a name="onwizardnext"></a>C屬性頁::在精靈下一頁

當用戶單擊嚮導中的"下一步"按鈕時,框架將調用此成員函數。

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>傳回值

0 自動前進到下一頁;-1 以防止頁面更改。 要跳到下一個頁面以外的頁面,傳回要顯示的對話框的標識符。

### <a name="remarks"></a>備註

重寫此成員函數以指定按下「下一步」按鈕時用戶必須執行的操作。

有關如何創建精靈類型屬性表的詳細資訊,請參閱[CPropertySheet:setWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

## <a name="cpropertypagequerysiblings"></a><a name="querysiblings"></a>C 屬性頁:查詢同級

調用此成員函數將消息轉發到屬性表中的每個頁面。

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

*wParam*<br/>
指定其他與消息相關的資訊。

*lParam*<br/>
指定其他與訊息相關的資訊

### <a name="return-value"></a>傳回值

屬性表中的頁面中的非零值;如果所有頁面返回值 0,則為 0。

### <a name="remarks"></a>備註

如果頁面返回非零值,則屬性表不會將消息發送到後續頁面。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

## <a name="cpropertypagesetmodified"></a><a name="setmodified"></a>C 屬性頁::已修改

調用此成員函數以啟用或禁用"立即應用"按鈕,具體取決於屬性頁中的設置是否應應用於相應的外部物件。

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>參數

*b 已變更*<br/>
TRUE 以指示自上次應用屬性頁設置以來已修改屬性頁設置;FALSE 以指示已應用屬性頁設置,或應忽略。

### <a name="remarks"></a>備註

框架追蹤哪些頁面是「臟」的,即您為其調用`SetModified( TRUE )`的屬性頁。 如果調用`SetModified( TRUE )`其中一個頁面,則始終啟用"立即應用"按鈕。 當您調用`SetModified( FALSE )`其中一個頁面時,將禁用"立即應用"按鈕,但前提是其他頁面均未"臟"。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet 類別](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)

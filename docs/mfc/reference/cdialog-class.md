---
title: CDialog 類別
ms.date: 09/07/2019
f1_keywords:
- CDialog
- AFXWIN/CDialog
- AFXWIN/CDialog::CDialog
- AFXWIN/CDialog::Create
- AFXWIN/CDialog::CreateIndirect
- AFXWIN/CDialog::DoModal
- AFXWIN/CDialog::EndDialog
- AFXWIN/CDialog::GetDefID
- AFXWIN/CDialog::GotoDlgCtrl
- AFXWIN/CDialog::InitModalIndirect
- AFXWIN/CDialog::MapDialogRect
- AFXWIN/CDialog::NextDlgCtrl
- AFXWIN/CDialog::OnInitDialog
- AFXWIN/CDialog::OnSetFont
- AFXWIN/CDialog::PrevDlgCtrl
- AFXWIN/CDialog::SetDefID
- AFXWIN/CDialog::SetHelpID
- AFXWIN/CDialog::OnCancel
- AFXWIN/CDialog::OnOK
helpviewer_keywords:
- CDialog [MFC], CDialog
- CDialog [MFC], Create
- CDialog [MFC], CreateIndirect
- CDialog [MFC], DoModal
- CDialog [MFC], EndDialog
- CDialog [MFC], GetDefID
- CDialog [MFC], GotoDlgCtrl
- CDialog [MFC], InitModalIndirect
- CDialog [MFC], MapDialogRect
- CDialog [MFC], NextDlgCtrl
- CDialog [MFC], OnInitDialog
- CDialog [MFC], OnSetFont
- CDialog [MFC], PrevDlgCtrl
- CDialog [MFC], SetDefID
- CDialog [MFC], SetHelpID
- CDialog [MFC], OnCancel
- CDialog [MFC], OnOK
ms.assetid: ca64b77e-2cd2-47e3-8eff-c2645ad578f9
ms.openlocfilehash: cad762f426012d9d1931b96d54d8a53c9bab465d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375652"
---
# <a name="cdialog-class"></a>CDialog 類別

用於在螢幕上顯示對話框的基類。

## <a name="syntax"></a>語法

```
class CDialog : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDialog:CDialog](#cdialog)|建構 `CDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDialog:建立](#create)|初始化 `CDialog` 物件。 創建無模式對話方塊並將其附加`CDialog`到 物件。|
|[CDialog:建立間接](#createindirect)|從記憶體中的對話方塊樣本創建無模式對話方塊(不基於資源)。|
|[CDialog::Do模態](#domodal)|調用模態對話方塊,並在完成後返回。|
|[CDialog:結束對話](#enddialog)|關閉模式對話方塊。|
|[CDialog:GetDefID](#getdefid)|獲取對話框的預設按鈕控制項的識別碼。|
|[CDialog:GotoDlgCtrl](#gotodlgctrl)|將焦點移動到對話框中的指定對話框控制項。|
|[CDialog:in模態間接](#initmodalindirect)|從記憶體中的對話方塊樣本創建模式對話方塊(不基於資源)。 參數將一直存儲到調用函數`DoModal`為止。|
|[C對話::映射對話](#mapdialogrect)|將矩形的對話框單位轉換為屏幕單位。|
|[CDialog::下一個DlgCtrl](#nextdlgctrl)|將焦點移動到對話框中的下一個對話方塊控制項。|
|[CDialog:onInitDialog](#oninitdialog)|覆蓋以增強對話框初始化。|
|[CDialog::放大縮小字型功能 放大縮小字型功能](#onsetfont)|覆蓋以指定對話方塊控制檔在繪製文本時要使用的字型。|
|[CDialog::PrevDlgCtrl](#prevdlgctrl)|將焦點移動到對話框中的上一個對話方塊控制項。|
|[CDialog:setDefID](#setdefid)|將對話框的預設按鈕控制項更改為指定的按鈕。|
|[CDialog:設定幫助ID](#sethelpid)|為對話框設置上下文相關的幫助 ID。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CDialog:開啟取消](#oncancel)|覆蓋以執行「取消」按鈕或 ESC 鍵操作。 默認值關閉對話方塊`DoModal`並返回 IDCANCEL。|
|[CDialog::OnOK](#onok)|覆蓋以在模式對話框中執行"確定"按鈕操作。 默認值關閉對話方塊`DoModal`並返回 IDOK。|

## <a name="remarks"></a>備註

對話框有兩種類型:模態和無模式。 在應用程式繼續之前,用戶必須關閉模式對話方塊。 無模式對話框允許使用者顯示對話方塊並返回到其他任務,而無需取消或刪除對話方塊。

對`CDialog`像是對話框範本和`CDialog`派生類的組合。 使用對話框編輯器創建對話方塊樣本並將其存儲在資源中,然後使用"添加類"嚮導創建派生自的`CDialog`類。

與任何其他視窗一樣,對話框接收來自 Windows 的消息。 在對話框中,您特別有興趣處理來自對話框控件的通知消息,因為這是使用者與對話方塊互動的方式。 使用[類別匯](mfc-class-wizard.md)選擇要處理的郵件,它將為您向類添加適當的消息映射項目和訊息處理程式成員函數。 您只需在處理程式成員函數中編寫特定於應用程式的代碼。

如果您願意,您可以隨時手動編寫消息映射條目和成員函數。

在除了最瑣碎的對話框外的所有對話框中,您將成員變數添加到派生對話方塊類中,以儲存使用者在對話方塊控制項中輸入的數據或顯示用戶的數據。 可以使用「添加變數」嚮導創建成員變數並將其與控制項關聯。 同時,為每個變數選擇變數類型和允許的值範圍。 代碼向導將成員變數添加到派生對話方塊類。

生成數據映射以自動處理成員變數和對話方塊控制元件之間的數據交換。 數據映射提供函數,用於用正確的值初始化對話方塊中的控制項、檢索數據並驗證數據。

要創建模態對話框,請使用派生對話框類的構造函數在堆疊上構造對象,然後調`DoModal`用 以創建對話框視窗及其控制項。 如果要創建無模式對話框,請調用`Create`對話方塊類的構造函數。

您還可以使用 Windows SDK 中描述的[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)數據結構在記憶體中創建範本。 建構`CDialog`物件後,調用[CreateIndirect](#createindirect)以建立無模式對話框,或調用[InitModal 間接](#initmodalindirect)和[DoModal](#domodal)以創建模式對話方塊。

交換和驗證資料對應以添加到新對話方塊類的`CWnd::DoDataExchange`重寫形式編寫。 有關交換和驗證功能的更多,請參閱`CWnd`中的[DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成員函數。

程式員和框架都通過調用`DoDataExchange`[CWnd::updateData](../../mfc/reference/cwnd-class.md#updatedata)間接調用。

當使用者按下「`UpdateData`確定」 按鈕以關閉模式對話框時,框架將調用。 (如果按下"取消"按鈕,則不會檢索數據。[OnInitDialog](#oninitdialog)的預設實現還調`UpdateData`用 設置控制項的初始值。 通常重寫`OnInitDialog`以進一步初始化控制件。 `OnInitDialog`在創建所有對話方塊控制程式後並在顯示對話框之前調用。

在執行模式或`CWnd::UpdateData`無模式對話框期間,您可以隨時呼叫。

如果手動開發一個對話框,則自己向派生的對話方塊類添加必要的成員變數,並添加成員函數來設置或獲取這些值。

當使用者按下"確定"或"取消"按鈕或代碼調用`EndDialog`成員函數時,模式對話框將自動關閉。

實現無模式對話方塊時,始終`OnCancel`覆蓋成員函數並從其中調用`DestroyWindow`。 不要調用基類`CDialog::OnCancel`,因為它調`EndDialog`用 ,這將使對話框不可見,但不會破壞它。 您還應重寫`PostNcDestroy`無模式對話方塊,以便刪除**此**,因為無模式對話方塊通常使用**new**分配。 模態對話框通常構建在框架上,不需要`PostNcDestroy`清理。

有關 的詳細`CDialog`資訊 ,請參閱[對話框](../../mfc/dialog-boxes.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDialog`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cdialogcdialog"></a><a name="cdialog"></a>CDialog:CDialog

要建構基於資源的模式對話框,請調用構造函數的兩種公共形式。

```
explicit CDialog(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

explicit CDialog(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);

CDialog();
```

### <a name="parameters"></a>參數

*lpszTemplate 名稱*<br/>
包含一個 null 連接端字串,該字串是對話方塊樣本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊樣本資源的 ID 號。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件[(CWnd](../../mfc/reference/cwnd-class.md)類型)。 如果為 NULL,則對話方塊物件的父視窗將設置為主應用程式視窗。

### <a name="remarks"></a>備註

建構函數的一種形式按範本名稱提供對對話方塊資源的訪問。 另一個構造函數按範本 ID 號提供訪問,通常帶有**IDD_** 前綴(例如,IDD_DIALOG1)。

要從記憶體中的樣本建構模態對話框,請先呼叫無參數、受保護的建構函數,然後呼叫`InitModalIndirect`。

使用上述方法之一建構模式對話框後,呼叫`DoModal`。

要建構無模式對話方塊,請`CDialog`使用建構函數的受保護形式。 構造函數受到保護,因為必須派生自己的對話框類才能實現無模式對話方塊。 構建無模式對話框是一個兩步過程。 首先調用構造函數;然後調用`Create`成員函數以創建基於資源的對話框,或調`CreateIndirect`用 從記憶體中的範本創建對話方塊。

## <a name="cdialogcreate"></a><a name="create"></a>CDialog:建立

呼叫`Create`使用來自資源的對話方塊樣本建立無模式對話方塊。

```
virtual BOOL Create(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd = NULL);

virtual BOOL Create(
    UINT nIDTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*lpszTemplate 名稱*<br/>
包含一個 null 連接端字串,該字串是對話方塊樣本資源的名稱。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗物件[(CWnd](../../mfc/reference/cwnd-class.md)類型)。 如果為 NULL,則對話方塊物件的父視窗將設置為主應用程式視窗。

*nIDTemplate*<br/>
包含對話方塊樣本資源的 ID 號。

### <a name="return-value"></a>傳回值

如果對話框創建和初始化成功,則兩種窗體都返回非零;否則 0。

### <a name="remarks"></a>備註

可以將調用放在`Create`建構函數內部,或在調用構造函數後調用它。

`Create`提供了兩種形式的成員函數,以便通過範本名稱或範本 ID 號(例如,IDD_DIALOG1)訪問對話方塊範本資源。

對於任一窗體,將指標傳遞給父窗口物件。 如果*pParentWnd*為 NULL,則對話方塊將創建其父視窗或擁有者視窗設置為主應用程式視窗。

成員`Create`函數在創建對話方塊後立即返回。

如果在創建父視窗時應顯示對話框,則在對話框範本中使用WS_VISIBLE樣式。 否則,您必須呼叫`ShowWindow`。 有關進一步的對話框樣式及其應用程式,請參閱*MFC 參考*中的 Windows SDK 和[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)中的[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)結構。

使用`CWnd::DestroyWindow`函數銷毀由`Create`該函數創建的對話方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#62](../../mfc/codesnippet/cpp/cdialog-class_1.cpp)]

## <a name="cdialogcreateindirect"></a><a name="createindirect"></a>CDialog:建立間接

調用此成員函數從記憶體中的對話方塊範本創建無模式對話方塊。

```
virtual BOOL CreateIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

virtual BOOL CreateIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*lpDialog範本*<br/>
包含用於創建對話框的對話方塊樣本的記憶體點。 此範本以[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)結構和控制資訊的形式出現,如 Windows SDK 中所述。

*pparentwnd*<br/>
指向對話框物件的父視窗物件[(CWnd](../../mfc/reference/cwnd-class.md)類型)。 如果為 NULL,則對話方塊物件的父視窗將設置為主應用程式視窗。

*lpDialogInit*<br/>
指向 DLGINIT 資源。

*h 對話範本*<br/>
包含包含對話框範本的全域記憶體的句柄。 此範本以對話框中每個控制項的`DLGTEMPLATE`結構和資料的形式出現。

### <a name="return-value"></a>傳回值

如果對話框已成功創建並初始化,則非零;否則 0。

### <a name="remarks"></a>備註

成員`CreateIndirect`函數在創建對話方塊後立即返回。

如果在創建父視窗時應顯示對話框,則在對話框範本中使用WS_VISIBLE樣式。 否則,必須調用`ShowWindow`以使其顯示。 有關如何在範本中指定其他對話框樣式的詳細資訊,請參閱 Windows SDK 中的[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)結構。

使用`CWnd::DestroyWindow`函數銷毀由`CreateIndirect`該函數創建的對話方塊。

包含 ActiveX 控件的對話方塊需要 DLGINIT 資源中提供的其他資訊。

## <a name="cdialogdomodal"></a><a name="domodal"></a>CDialog::Do模態

調用此成員函數以調用模態對話方塊,並在完成後返回對話框結果。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

指定傳遞給[CDialog:endDialog](#enddialog)成員函數的*nResult*參數的值的**int**值,用於關閉對話方塊。 如果函數無法建立對話框,則返回值為 -1;如果發生其他錯誤,則返回值為 -1,如果發生其他錯誤,則返回值為 -1,在這種情況下,輸出視窗將包含[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)中的錯誤資訊。

### <a name="remarks"></a>備註

此成員函數處理與使用者的所有交互,當對話框處於活動狀態時。 這就是使對話框模態的原因;也就是說,在關閉對話方塊之前,用戶無法與其他窗互。

如果用戶按一下對話方塊中的一個按鈕(如"確定"或"取消"),則會調用消息處理程式成員函數(如[OnOK](#onok)或[OnCancel)](#oncancel)以嘗試關閉該對話方塊。 默認`OnOK`成員函數將驗證和更新對話框資料,並關閉具有結果 IDOK 的對話方`OnCancel`塊,預設成員函數將關閉具有結果 IDCANCEL 的對話方塊,而無需驗證或更新對話框數據。 您可以重寫這些消息處理程式函數來更改其行為。

> [!NOTE]
> `PreTranslateMessage`現在調用模態對話框消息處理。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#63](../../mfc/codesnippet/cpp/cdialog-class_2.cpp)]

## <a name="cdialogenddialog"></a><a name="enddialog"></a>CDialog:結束對話

調用此成員函數以終止模式對話方塊。

```
void EndDialog(int nResult);
```

### <a name="parameters"></a>參數

*nResult*<br/>
包含要從對話框傳回到的呼叫方的`DoModal`值 。

### <a name="remarks"></a>備註

此成員函數返回*nResult*`DoModal`作為的返回值。 每當創建模式對話框`EndDialog`時,都必須使用函數完成處理。

您可以隨時呼叫`EndDialog`,即使在[OnInitDialog](#oninitdialog)中,在顯示對話方塊之前或設置輸入焦點之前,也應關閉該對話框。

`EndDialog`不會立即關閉該對話方塊。 相反,它會設置一個標誌,指示對話框在當前消息處理程式返回后立即關閉。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#64](../../mfc/codesnippet/cpp/cdialog-class_3.cpp)]

[!code-cpp[NVC_MFCControlLadenDialog#65](../../mfc/codesnippet/cpp/cdialog-class_4.cpp)]

## <a name="cdialoggetdefid"></a><a name="getdefid"></a>CDialog:GetDefID

呼叫`GetDefID`成員函數獲取對話方塊的預設按鈕控制項的 ID。

```
DWORD GetDefID() const;
```

### <a name="return-value"></a>傳回值

32 位元`DWORD`值 ( 。 如果默認按鈕具有 ID 值,則高階單詞包含DC_HASDEFID,低階單詞包含 ID 值。 如果默認按鈕沒有 ID 值,則返回值為 0。

### <a name="remarks"></a>備註

這通常是一個確定按鈕。

## <a name="cdialoggotodlgctrl"></a><a name="gotodlgctrl"></a>CDialog:GotoDlgCtrl

將焦點移動到對話方塊中的指定控制項。

```
void GotoDlgCtrl(CWnd* pWndCtrl);
```

### <a name="parameters"></a>參數

*pWndCtrl*<br/>
標識接收焦點的視窗(控制項)。

### <a name="remarks"></a>備註

要獲取指向控制項(子視窗)的指標以*pWndCtrl*身份傳遞,請`CWnd::GetDlgItem`調用成員函數,該函數返回指向[CWnd](../../mfc/reference/cwnd-class.md)物件的指標。

### <a name="example"></a>範例

  請參閱[CWnd 的範例:GetDlgItem](../../mfc/reference/cwnd-class.md#getdlgitem)。

## <a name="cdialoginitmodalindirect"></a><a name="initmodalindirect"></a>CDialog:in模態間接

呼叫此成員函數,使用您在記憶體中建構的對話方塊樣本初始化模式對話方塊物件。

```
BOOL InitModalIndirect(
    LPCDLGTEMPLATE lpDialogTemplate,
    CWnd* pParentWnd = NULL,
    void* lpDialogInit = NULL);

    BOOL InitModalIndirect(
    HGLOBAL hDialogTemplate,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>參數

*lpDialog範本*<br/>
包含用於創建對話框的對話方塊樣本的記憶體點。 此範本以[DLGTEMPLATE](/windows/win32/api/winuser/ns-winuser-dlgtemplate)結構和控制資訊的形式出現,如 Windows SDK 中所述。

*h 對話範本*<br/>
包含包含對話框範本的全域記憶體的句柄。 此範本以對話框中每個控制項的`DLGTEMPLATE`結構和資料的形式出現。

*pparentwnd*<br/>
指向對話框物件所屬的父視窗或所有者視窗物件[(CWnd](../../mfc/reference/cwnd-class.md)類型)。 如果為 NULL,則對話方塊物件的父視窗將設置為主應用程式視窗。

*lpDialogInit*<br/>
指向 DLGINIT 資源。

### <a name="return-value"></a>傳回值

如果對話框物件已成功創建並初始化,則非零;否則 0。

### <a name="remarks"></a>備註

要間接創建模式對話框,請先分配全域記憶體塊,然後用對話框範本填充它。 然後調用空`CDialog`構造函數來構造對話框物件。 接下來,調用`InitModalIndirect`將句柄存儲到記憶體中對話框範本。 稍後調用[DoModal](#domodal)成員函數時,將創建並顯示 Windows 對話方塊。

包含 ActiveX 控件的對話方塊需要 DLGINIT 資源中提供的其他資訊。

## <a name="cdialogmapdialogrect"></a><a name="mapdialogrect"></a>C對話::映射對話

調用以將矩形的對話框單位轉換為屏幕單位。

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向包含要轉換的對話方塊座標的[RECT](/windows/win32/api/windef/ns-windef-rect)結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件。

### <a name="remarks"></a>備註

對話框單位根據當前對話框基本單位表示,該單位派生自對話框文本字體中字元的平均寬度和高度。 一個水平單位是對話框基寬單位的四分之一,一個垂直單位是對話框基本高度單位的八分之一。

Windows`GetDialogBaseUnits`函數傳回系統字型的大小資訊,但如果在資源定義檔中使用DS_SETFONT樣式,則可以為每個對話方塊指定不同的字型。 Windows`MapDialogRect`函數為此對話框使用相應的字體。

成員`MapDialogRect`函數將*lpRect*中的對話框單元替換為螢幕單位(圖元),以便矩形可用於創建對話方塊或在框中放置控制項。

## <a name="cdialognextdlgctrl"></a><a name="nextdlgctrl"></a>CDialog::下一個DlgCtrl

將焦點移到對話方塊中的下一個控制項。

```
void NextDlgCtrl() const;
```

### <a name="remarks"></a>備註

如果焦點位於對話框中的最後一個控制項,則它移動到第一個控制項。

## <a name="cdialogoncancel"></a><a name="oncancel"></a>CDialog:開啟取消

當用戶按下 **「取消」** 或在模態或無模式對話框中按 ESC 鍵時,框架將調用此方法。

```
virtual void OnCancel();
```

### <a name="remarks"></a>備註

在用戶通過按下 **「取消」** 或按一下 ESC 鍵關閉對話方塊時,重寫此方法以執行操作(如還原舊資料)。 默認值通過調用[EndDialog](#enddialog)並導致[DoModal](#domodal)返回 IDCANCEL 來關閉模式對話方塊。

如果在無模式對話框中實現 **「取消」** 按鈕,則必須`OnCancel`重寫 該方法並在其中調用[「銷毀視窗](../../mfc/reference/cwnd-class.md#destroywindow)」。 不要調用基類方法,因為它調用`EndDialog`,這將使對話框不可見,但不會破壞它。

> [!NOTE]
> 在 Windows XP 下編`CFileDialog`譯的程式 中使用物件時,無法重寫此方法。 有關 的詳細`CFileDialog`資訊 ,請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#66](../../mfc/codesnippet/cpp/cdialog-class_5.cpp)]

## <a name="cdialogoninitdialog"></a><a name="oninitdialog"></a>CDialog:onInitDialog

呼叫此方法以回應訊息`WM_INITDIALOG`。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

指定應用程式是否已將輸入焦點設定為對話框中的一個控制項。 如果`OnInitDialog`返回非零,Windows 會將輸入焦點設置到預設位置,即對話框中的第一個控制項。 僅當應用程式顯示式將輸入焦點設定為對話框中的一個控制項時,應用程式才能返回 0。

### <a name="remarks"></a>備註

Windows`WM_INITDIALOG`在["創建](#create)、[創建間接](#createindirect)"或["DoModal"](#domodal)呼叫期間將訊息發送到對話框,這些調用在顯示對話框之前發生。

如果要在初始化對話框時執行特殊處理,則重寫此方法。 在重寫版本中,首先調用基類`OnInitDialog`,但忽略其返回值。 您通常會從重寫`TRUE`的方法返回。

Windows`OnInitDialog`使用 所有 Microsoft 基礎類庫對話框共有的標準全域對話框過程調用該函數。 它不通過消息映射調用此函數,因此不需要此方法的消息映射條目。

> [!NOTE]
> 在 Windows Vista 或`CFileDialog`更高版本的 作業系統下編譯的程式中使用物件時,無法重寫此方法。 有關 Windows`CFileDialog`Vista 下和更高版本更改的詳細資訊,請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#67](../../mfc/codesnippet/cpp/cdialog-class_6.cpp)]

## <a name="cdialogonok"></a><a name="onok"></a>CDialog::OnOK

當使用者按下 **「確定」** 按鈕(IDOK IDOK 的按鈕)時調用。

```
virtual void OnOK();
```

### <a name="remarks"></a>備註

重寫此方法,在啟動 **「確定」** 按鈕時執行操作。 如果對話框包括自動資料驗證和交換,則此方法的預設實現將驗證對話框數據並更新應用程式中的相應變數。

如果在無模式對話框中實現 **「確定」** 按鈕,則必須`OnOK`重寫 該方法並在其中調用[「銷毀視窗](../../mfc/reference/cwnd-class.md#destroywindow)」。 不要調用基類方法,因為它調用[EndDialog,](#enddialog)它使對話方塊不可見,但不會破壞它。

> [!NOTE]
> 在 Windows XP 下編`CFileDialog`譯的程式 中使用物件時,無法重寫此方法。 有關 的詳細`CFileDialog`資訊 ,請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#68](../../mfc/codesnippet/cpp/cdialog-class_7.cpp)]

## <a name="cdialogonsetfont"></a><a name="onsetfont"></a>CDialog::放大縮小字型功能 放大縮小字型功能

指定繪製文字時對話方塊控制件將使用的字型。

```
Virtual void OnSetFont(CFont* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
[在]指定指向字型的指標,該指標將用作此對話框中所有控制項的預設字型。

### <a name="remarks"></a>備註

該對話框將使用指定的字體作為其所有控制項的預設值。

對話框編輯器通常將對話方塊字體設置為對話方塊範本資源的一部分。

> [!NOTE]
> 在 Windows Vista 或`CFileDialog`更高版本的 作業系統下編譯的程式中使用物件時,無法重寫此方法。 有關 Windows`CFileDialog`Vista 下和更高版本更改的詳細資訊,請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。

## <a name="cdialogprevdlgctrl"></a><a name="prevdlgctrl"></a>CDialog::PrevDlgCtrl

將焦點設置到對話框中以前的控制項。

```
void PrevDlgCtrl() const;
```

### <a name="remarks"></a>備註

如果焦點位於對話框中的第一個控制項處,它將移動到框中的最後一個控制項。

## <a name="cdialogsetdefid"></a><a name="setdefid"></a>CDialog:setDefID

更改對話框的預設按鈕控制項。

```
void SetDefID(UINT nID);
```

### <a name="parameters"></a>參數

*nID*<br/>
指定將成為預設值的按鈕控制項的識別碼。

## <a name="cdialogsethelpid"></a><a name="sethelpid"></a>CDialog:設定幫助ID

為對話框設置上下文相關的幫助 ID。

```
void SetHelpID(UINT nIDR);
```

### <a name="parameters"></a>參數

*尼德*<br/>
指定上下文相關的幫助 ID。

## <a name="see-also"></a>另請參閱

[MFC 樣品 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 DLGTEMPL](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)

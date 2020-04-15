---
title: CMFCKeyMapDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
ms.openlocfilehash: 22aa006ce214ca720192bb761e2ff2b35a64fce3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374407"
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog 類別

類`CMFCKeyMapDialog`支援將命令映射到鍵盤上的鍵的控制項。

## <a name="syntax"></a>語法

```
class CMFCKeyMapDialog : public CDialogEx
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC鍵對應對話::CMFC鍵對應對話](#cmfckeymapdialog)|建構 `CMFCKeyMapDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC鍵映射對話::Do模態](#domodal)|顯示鍵盤映射對話方塊。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFC 鍵對應對話::格式項目](#formatitem)|由框架呼叫以產生描述金鑰映射的字串。 預設情況下,字串包含命令名稱、使用的快捷鍵和快速鍵說明。|
|[CMFC鍵對應對話::取得命令金鑰](#getcommandkeys)|檢索包含與指定命令關聯的快捷鍵清單的字串。|
|[CMFC鍵對應對話:插入專案](#oninsertitem)|在將新專案插入支援鍵盤映射控制件的內部清單控制項之前,由框架調用。|
|[CMFC鍵對應對話::在列印標題上](#onprintheader)|由框架調用在新頁面上列印鍵盤映射的標頭。|
|[CMFC鍵對應對話::在列印專案](#onprintitem)|由框架調用以列印鍵盤映射項。|
|[CMFC鍵對應對話::開啟欄](#onsetcolumns)|框架呼叫,為支援鍵盤映射控制項的內部清單控制件中的列設置標題。|
|[CMFC鍵對應對話::PrintKeyMap](#printkeymap)|當使用者按下 **「列印」** 按鈕時,由框架調用。|
|[CMFC鍵對應對話::設定欄寬度](#setcolumnswidth)|由框架呼叫,以設定支援鍵盤映射控制項的內部清單控制件中的欄的寬度。|

## <a name="remarks"></a>備註

使用`CMFCKeyMapDialog`類實現可調整大小的鍵盤映射對話框。 該對話框使用清單檢視控制項來顯示鍵盤快捷鍵及其關聯的命令。

要在應用程式中`CMFCKeyMapDialog`使用 類,請將指向主框架視窗的指標作為參數傳遞`CMFCKeyMapDialog`給構造函數。 然後調用`DoModal`方法以啟動模態對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>需求

**標題:** afxkeymapdialog.h

## <a name="cmfckeymapdialogcmfckeymapdialog"></a><a name="cmfckeymapdialog"></a>CMFC鍵對應對話::CMFC鍵對應對話

建構 `CMFCKeyMapDialog` 物件。

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>參數

*pwnd 父架構*<br/>
[在]指向物件的父視窗的`CMFCKeyMapDialog`指標。

*bEnablePrint*<br/>
[在]如果可以列印快捷鍵清單,則為 TRUE;否則,FALSE。 預設值為 FALSE。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCKeyMapDialog`類的物件。 此示例是[可視化工作室演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

## <a name="cmfckeymapdialogdomodal"></a><a name="domodal"></a>CMFC鍵映射對話::Do模態

顯示鍵盤映射對話方塊。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>傳回值

傳遞給[CDialog::結束對話](../../mfc/reference/cdialog-class.md#enddialog)方法的已簽名整數,如 IDOK 或 IDCANCEL。 該方法依次關閉對話方塊。 有關詳細資訊,請參閱[CDialog::Do 模態](../../mfc/reference/cdialog-class.md#domodal)。

### <a name="remarks"></a>備註

鍵盤對應對話框允許您選擇和分配快速鍵到各種類別的命令。 此外,您可以將選定的快速鍵及其說明複製到剪貼簿。

## <a name="cmfckeymapdialogformatitem"></a><a name="formatitem"></a>CMFC 鍵對應對話::格式項目

由框架呼叫以產生描述金鑰映射的字串。 預設情況下,字串包含命令名稱、使用的快捷鍵和快速鍵說明。

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>參數

*nItem*<br/>
[在]鍵映射內部清單中項的零基索引。

### <a name="return-value"></a>傳回值

包含`CString`格式化項目文字的物件。

### <a name="remarks"></a>備註

## <a name="cmfckeymapdialoggetcommandkeys"></a><a name="getcommandkeys"></a>CMFC鍵對應對話::取得命令金鑰

檢索字串值。 該字串包含與指定命令關聯的快捷鍵清單。

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>參數

*烏伊CmdID*<br/>
[在]命令識別碼。

### <a name="return-value"></a>傳回值

與指定命令關聯的快捷鍵的分號分隔 (';'' 清單)。

### <a name="remarks"></a>備註

## <a name="cmfckeymapdialogoninsertitem"></a><a name="oninsertitem"></a>CMFC鍵對應對話:插入專案

在將新專案插入支援鍵盤映射控制件的內部清單控制項之前,由框架調用。

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>參數

*pButton*<br/>
[在]指向工具列按鈕的指標,用於將鍵盤鍵組合映射到命令名稱和說明。 鍵對應儲存在內部清單控制項中。

*nItem*<br/>
[在]一個基於零的索引,用於指定在內部清單控制項中插入新鍵映射項的位置。

### <a name="remarks"></a>備註

## <a name="cmfckeymapdialogonprintheader"></a><a name="onprintheader"></a>CMFC鍵對應對話::在列印標題上

由框架調用在新頁面上列印鍵盤映射的標頭。

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>參數

*直流*<br/>
[在]印表機的設備上下文。

*nPage*<br/>
[在]要列印的頁碼。

*殘雪*<br/>
[在]標題的水準偏移(以像素為單位)。

### <a name="return-value"></a>傳回值

如果成功,則列印文本的高度。 有關詳細資訊,請參閱[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)的返回值部分。

### <a name="remarks"></a>備註

框架使用此方法列印鍵盤映射。 預設情況下,此方法列印頁碼、應用程式名稱和對話框標題。

## <a name="cmfckeymapdialogonprintitem"></a><a name="onprintitem"></a>CMFC鍵對應對話::在列印專案

由框架調用以列印鍵盤映射項。

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>參數

*直流*<br/>
[在]印表機的設備上下文。

*nItem*<br/>
[在]要列印的項的零基索引。

*Y*<br/>
[在]頁面頂部和專案位置之間的垂直偏移。

*殘雪*<br/>
[在]頁面左側和專案位置之間的水準偏移。

*bCalcHeight*<br/>
[在]TRUE 以計算列印專案的最佳高度;FALSE 可截截列印項,使其適合預設空間。

### <a name="return-value"></a>傳回值

列印專案的高度。

### <a name="remarks"></a>備註

框架調用此方法來列印鍵映射對話框項。 預設情況下,此方法列印項的命令名稱、快捷鍵和命令說明。

## <a name="cmfckeymapdialogonsetcolumns"></a><a name="onsetcolumns"></a>CMFC鍵對應對話::開啟欄

框架呼叫,為支援鍵盤映射控制項的內部清單控制件中的列設置標題。

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>備註

預設情況下,此方法從三個資源獲取列的標題。 命令列標題來自IDS_AFXBARRES_COMMAND,鍵列標題來自IDS_AFXBARRES_KEYS,描述列標題來自IDS_AFXBARRES_DESCRIPTION。

## <a name="cmfckeymapdialogprintkeymap"></a><a name="printkeymap"></a>CMFC鍵對應對話::PrintKeyMap

當使用者按下 **「列印」** 按鈕時,由框架調用。

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>備註

該方法`PrintKeyMap`列印鍵映射。 它啟動新的列印作業,然後反覆調用[CMFCKeyMapDialog::在列印標題](#onprintheader)和[CMFCKeyMapDialog::在列印專案](#onprintitem)方法,直到列印所有鍵映射。

## <a name="cmfckeymapdialogsetcolumnswidth"></a><a name="setcolumnswidth"></a>CMFC鍵對應對話::設定欄寬度

由框架呼叫,以設定支援鍵盤映射控制項的內部清單控制件中的欄的寬度。

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>備註

此方法將內部清單控制件的列設定為預設寬度。 首先,計算快捷鍵列的寬度。 然後,剩餘寬度的三分之一分配給命令列,其餘三分之二分配給描述列。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)

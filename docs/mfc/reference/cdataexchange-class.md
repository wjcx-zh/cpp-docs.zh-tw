---
title: CDataExchange 類別
ms.date: 11/04/2016
f1_keywords:
- CDataExchange
- AFXWIN/CDataExchange
- AFXWIN/CDataExchange::CDataExchange
- AFXWIN/CDataExchange::Fail
- AFXWIN/CDataExchange::PrepareCtrl
- AFXWIN/CDataExchange::PrepareEditCtrl
- AFXWIN/CDataExchange::PrepareOleCtrl
- AFXWIN/CDataExchange::m_bSaveAndValidate
- AFXWIN/CDataExchange::m_pDlgWnd
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
ms.openlocfilehash: 0e7a9d429acb1acd72942e5f10ac0815232ddc69
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776306"
---
# <a name="cdataexchange-class"></a>CDataExchange 類別

支援 Microsoft Foundation 類別使用的對話方塊資料交換 (DDX) 和對話方塊資料驗證 (DDV) 常式。

## <a name="syntax"></a>語法

```
class CDataExchange
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDataExchange::CDataExchange](#cdataexchange)|建構 `CDataExchange` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDataExchange::Fail](#fail)|當驗證失敗時呼叫。 重設焦點至上一個控制項，並擲回例外狀況。|
|[CDataExchange::PrepareCtrl](#preparectrl)|指定的控制項來準備資料交換或驗證。 Nonedit 控制項中使用。|
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|指定的編輯控制項來準備資料交換或驗證。|
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|指定的 OLE 控制項來準備資料交換或驗證。 Nonedit 控制項中使用。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|DDX 和 DDV 方向旗標。|
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|對話方塊或視窗的項目，其中資料交換會發生。|

## <a name="remarks"></a>備註

`CDataExchange` 沒有基底類別。

使用這個類別，如果您正在撰寫資料交換常式的自訂資料類型或控制項，或如果您要撰寫您自己的資料驗證常式。 如需有關撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱 <<c0> [ 技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 DDX 和 DDV 概觀，請參閱[ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)並[Dialog Boxes](../../mfc/dialog-boxes.md)。

A`CDataExchange`物件提供 DDX 和 DDV，才會將所需的內容資訊。 旗標*m_bSaveAndValidate*時 DDX 用來填滿資料成員的對話方塊控制項的起始值為 FALSE。 旗標*m_bSaveAndValidate* DDX 用來設定資料成員和 DDV 時用於驗證資料值的對話方塊控制項的目前值時為 TRUE。 如果 DDV 驗證失敗，DDV 程序就會顯示訊息方塊，說明輸入的錯誤。 DDV 程序會接著呼叫`Fail`重焦點設為違規的控制項，並擲回例外狀況停止驗證程序。

## <a name="inheritance-hierarchy"></a>繼承階層

`CDataExchange`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cdataexchange"></a>  CDataExchange::CDataExchange

呼叫此成員函式來建構`CDataExchange`物件。

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>參數

*pDlgWnd*<br/>
包含控制項之父視窗指標。 這通常是[CDialog](../../mfc/reference/cdialog-class.md)-衍生物件。

*bSaveAndValidate*<br/>
如果為 TRUE，這個物件會驗證資料，然後控制項中的資料寫入的成員。 如果為 FALSE，這個物件會移動資料成員的控制項。

### <a name="remarks"></a>備註

建構`CDataExchange`物件自行將額外的資訊儲存在資料交換物件傳遞至您的視窗[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

##  <a name="fail"></a>  CDataExchange::Fail

對話方塊資料驗證 (DDV) 作業失敗時，架構會呼叫此成員函式。

```
void Fail();
```

### <a name="remarks"></a>備註

`Fail` 還原至其驗證失敗 （如果沒有要還原的控制項） 控制項的焦點和選取範圍。 `Fail` 則會擲回例外狀況型別的[CUserException](../../mfc/reference/cuserexception-class.md)停止驗證程序。 例外狀況會導致訊息方塊，說明要顯示的錯誤。 DDV 驗證失敗後，使用者可以重新輸入有問題的控制項中的資料。

可以呼叫自訂 DDV 常式的實作項`Fail`從其驗證失敗時的常式。

如需有關撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱 <<c0> [ 技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱 <<c0> [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)並[對話方塊主題](../../mfc/dialog-boxes.md)。

##  <a name="m_bsaveandvalidate"></a>  CDataExchange::m_bSaveAndValidate

這個旗標表示對話方塊資料交換 (DDX) 作業的方向。

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>備註

旗標為非零值如果`CDataExchange`物件用來將資料移 dialog 控制項至對話方塊類別資料成員之後使用者編輯控制項。 旗標為零，如果物件要用來初始化從對話方塊類別資料成員的對話方塊控制項。

對話方塊資料驗證 (DDV) 時，還有非零的旗標。

如需有關撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱 <<c0> [ 技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱 <<c0> [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)並[對話方塊主題](../../mfc/dialog-boxes.md)。

##  <a name="m_pdlgwnd"></a>  CDataExchange::m_pDlgWnd

包含的指標[CWnd](../../mfc/reference/cwnd-class.md)的對話方塊資料交換 (DDX) 或驗證 (DDV) 正在進行中的物件。

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>備註

此物件通常是[CDialog](../../mfc/reference/cdialog-class.md)物件。 自訂的 DDX 或 DDV 常式的實作項可用來取得存取權的對話方塊視窗包含的控制項在操作此指標。

如需有關撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱 <<c0> [ 技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱 <<c0> [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)並[對話方塊主題](../../mfc/dialog-boxes.md)。

##  <a name="preparectrl"></a>  CDataExchange::PrepareCtrl

架構會呼叫此成員函式，以準備對話方塊資料交換 (DDX) 和驗證 (DDV) 指定的控制項。

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>參數

*nIDC*<br/>
做好 DDX 或 DDV 控制項 ID。

### <a name="return-value"></a>傳回值

正在準備 DDX 或 DDV 控制項 HWND。

### <a name="remarks"></a>備註

使用  [PrepareEditCtrl](#prepareeditctrl)改為編輯控制項; 所有其他控制項中使用此成員函式。

準備工作包括儲存在控制項的 HWND`CDataExchange`類別。 架構會將焦點還原至先前擁有焦點的控制項，DDX 或 DDV 失敗時，使用此控制代碼。

自訂的 DDX 或 DDV 常式的實作項應該呼叫`PrepareCtrl`對所有非編輯控制項，它們會交換資料透過 DDX 或驗證資料透過 DDV。

如需有關撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱 <<c0> [ 技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱 <<c0> [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)並[對話方塊主題](../../mfc/dialog-boxes.md)。

##  <a name="prepareeditctrl"></a>  CDataExchange::PrepareEditCtrl

架構會呼叫此成員函式，以準備指定的編輯控制項的對話方塊資料交換 (DDX) 和驗證 (DDV)。

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>參數

*nIDC*<br/>
做好 DDX 或 DDV 編輯控制項的 ID。

### <a name="return-value"></a>傳回值

正在準備 DDX 或 DDV 編輯控制項的 HWND。

### <a name="remarks"></a>備註

使用[PrepareCtrl](#preparectrl)改為所有非編輯控制項。

準備作業是由兩個項目所組成。 首先，`PrepareEditCtrl`會儲存在控制項的 HWND`CDataExchange`類別。 架構會將焦點還原至先前擁有焦點的控制項，DDX 或 DDV 失敗時，使用此控制代碼。 第二個，`PrepareEditCtrl`中設定旗標`CDataExchange`類別，表示要交換其資料，或驗證為編輯控制項的控制項。

自訂的 DDX 或 DDV 常式的實作項應該呼叫`PrepareEditCtrl`的所有編輯的控制項，它們會交換資料透過 DDX 或驗證資料透過 DDV。

如需有關撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱 <<c0> [ 技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱 <<c0> [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)並[對話方塊主題](../../mfc/dialog-boxes.md)。

##  <a name="prepareolectrl"></a>  CDataExchange::PrepareOleCtrl

架構會呼叫此成員函式，以準備指定的 OLE 控制項的對話方塊資料交換 (DDX) 和驗證 (DDV)。

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>參數

*nIDC*<br/>
做好 DDX 或 DDV OLE 控制項的 ID。

### <a name="return-value"></a>傳回值

OLE 控制項站台指標。

### <a name="remarks"></a>備註

使用[PrepareEditCtrl](#prepareeditctrl)改為編輯控制項或[PrepareCtrl](#preparectrl)其他所有非 OLE 控制項。

自訂的 DDX 或 DDV 常式的實作項應該呼叫`PrepareOleCtrl`所有 OLE 控制項，它們會交換資料透過 DDX 或驗證資料透過 DDV。

如需有關撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱 <<c0> [ 技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱 <<c0> [ 對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)並[對話方塊主題](../../mfc/dialog-boxes.md)。

## <a name="see-also"></a>另請參閱

[MFC 範例 VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)

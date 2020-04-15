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
ms.openlocfilehash: 73319ad898bfebf4caf191954ebb3935bd4ebce9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321958"
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
|[CDataExchange:CDataExchange](#cdataexchange)|建構 `CDataExchange` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDataExchange:失敗](#fail)|驗證失敗時調用。 將焦點重置為上一個控制者並引發異常。|
|[CDataExchange::P雷帕雷克拉爾](#preparectrl)|準備指定的控制項以進行數據交換或驗證。 用於非編輯控制件。|
|[CDataExchange::P回覆編輯](#prepareeditctrl)|準備指定的編輯控制項以進行數據交換或驗證。|
|[CDataExchange::P雷帕雷奧塞爾](#prepareolectrl)|準備指定的 OLE 控制項以進行資料交換或驗證。 用於非編輯控制件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDataExchange:m_bSaveAndValidate](#m_bsaveandvalidate)|為 DDX 和 DDV 方向標記。|
|[CDataExchange:m_pDlgWnd](#m_pdlgwnd)|發生數據交換的對話框或視窗。|

## <a name="remarks"></a>備註

`CDataExchange`沒有基類。

如果要為自定義數據類型或控制程式編寫資料交換例程,或者編寫自己的資料驗證例程,請使用此類。 有關編寫自己的 DDX 和 DDV 例設計的詳細資訊,請參閱[技術說明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有關 DDX 與 DDV 的概述,請參考[對話框交換與驗證](../../mfc/dialog-data-exchange-and-validation.md), 以及[對話框](../../mfc/dialog-boxes.md)。

物件`CDataExchange`提供發生 DDX 和 DDV 所需的上下文資訊。 當 DDX 用於填充數據成員對話方塊控制的初始值時 *,標誌m_bSaveAndValidate*為 FALSE。 當使用 DDX 將對話方塊控制項的目前值設定為資料成員以及使用 DDV 驗證資料值時,標誌*m_bSaveAndValidate*為 TRUE。 如果 DDV 驗證失敗,DDV 過程將顯示一個消息框,解釋輸入錯誤。 然後,DDV 過程`Fail`將調用將焦點重置為違規控制項,並引發異常以停止驗證過程。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CDataExchange`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cdataexchangecdataexchange"></a><a name="cdataexchange"></a>CDataExchange:CDataExchange

呼叫此成員函數以建構物件`CDataExchange`。

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>參數

*普德格溫德*<br/>
指向包含控制的父視窗的指標。 通常這是[CDialog](../../mfc/reference/cdialog-class.md)派生物件。

*b 儲存與驗證*<br/>
如果 TRUE,則此物件驗證數據,然後將數據從控件寫入成員。 如果 FALSE,此物件會將數據從成員移動到控制項。

### <a name="remarks"></a>備註

自行構造`CDataExchange`一個物件,以將數據交換物件中存儲額外資訊以傳遞到視窗的[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

## <a name="cdataexchangefail"></a><a name="fail"></a>CDataExchange:失敗

當對話框資料驗證 (DDV) 操作失敗時,框架將調用此成員函數。

```
void Fail();
```

### <a name="remarks"></a>備註

`Fail`將焦點和選擇還原到驗證失敗的控制項(如果有要還原的控制)。 `Fail`然後引發[CUserException](../../mfc/reference/cuserexception-class.md)類型的異常以停止驗證過程。 該異常會導致顯示一個消息框,解釋要顯示的錯誤。 DDV 驗證失敗後,用戶可以在違規控制項中重新輸入數據。

當驗證失敗時,自定義 DDV`Fail`例程的實現者可以從其例程調用。

有關編寫自己的 DDX 和 DDV 例設計的詳細資訊,請參閱[技術說明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有關 DDX 與 DDV 的概述,請參考[對話框來建立 。](../../mfc/dialog-data-exchange-and-validation.md)[Dialog Box Topics](../../mfc/dialog-boxes.md)

## <a name="cdataexchangem_bsaveandvalidate"></a><a name="m_bsaveandvalidate"></a>CDataExchange:m_bSaveAndValidate

此標誌指示對話框資料交換 (DDX) 操作的方向。

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>備註

如果`CDataExchange`物件用於在使用者編輯控制項後將數據從對話方塊控制件移動到對話方塊類資料成員,則該標誌為非零。 如果物件用於從對話框類數據成員初始化對話方塊控制項,則標誌為零。

在對話框數據驗證 (DDV) 期間,標誌也是非零。

有關編寫自己的 DDX 和 DDV 例設計的詳細資訊,請參閱[技術說明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有關 DDX 與 DDV 的概述,請參考[對話框來建立 。](../../mfc/dialog-data-exchange-and-validation.md)[Dialog Box Topics](../../mfc/dialog-boxes.md)

## <a name="cdataexchangem_pdlgwnd"></a><a name="m_pdlgwnd"></a>CDataExchange:m_pDlgWnd

包含指向正在為其進行對話數據交換 (DDX) 或驗證 (DDV) 的[CWnd](../../mfc/reference/cwnd-class.md)物件的指標。

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>備註

此物件通常是[CDialog](../../mfc/reference/cdialog-class.md)物件。 自訂 DDX 或 DDV 例程式設計的實現者可以使用此指標獲取對包含它們正在操作的控制項的對話框視窗的存取。

有關編寫自己的 DDX 和 DDV 例設計的詳細資訊,請參閱[技術說明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有關 DDX 與 DDV 的概述,請參考[對話框來建立 。](../../mfc/dialog-data-exchange-and-validation.md)[Dialog Box Topics](../../mfc/dialog-boxes.md)

## <a name="cdataexchangepreparectrl"></a><a name="preparectrl"></a>CDataExchange::P雷帕雷克拉爾

框架呼叫此成員函數以準備為對話框資料交換 (DDX) 和驗證 (DDV) 指定的控制項。

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>參數

*nIDC*<br/>
要為 DDX 或 DDV 準備的控制項的 ID。

### <a name="return-value"></a>傳回值

為 DDX 或 DDV 準備的控制項的 HWND。

### <a name="remarks"></a>備註

使用[準備編輯Ctrl](#prepareeditctrl)代替編輯控制項;將此成員函數用於所有其他控制項。

準備包含控制項的 HWND 儲存在類別`CDataExchange`中 。 框架使用此句柄在 DDX 或 DDV 發生故障時將焦點還原到以前重點控制項。

自定義 DDX 或 DDV 例`PrepareCtrl`程的實現者 應呼叫所有非編輯控制項,它們正在透過 DDX 交換資料或透過 DDV 驗證資料。

有關編寫自己的 DDX 和 DDV 例設計的詳細資訊,請參閱[技術說明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有關 DDX 與 DDV 的概述,請參考[對話框來建立 。](../../mfc/dialog-data-exchange-and-validation.md)[Dialog Box Topics](../../mfc/dialog-boxes.md)

## <a name="cdataexchangeprepareeditctrl"></a><a name="prepareeditctrl"></a>CDataExchange::P回覆編輯

框架呼叫此成員函數以準備為對話方塊資料交換 (DDX) 和驗證 (DDV) 指定的編輯控制項。

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>參數

*nIDC*<br/>
為 DDX 或 DDV 準備的編輯控制項的 ID。

### <a name="return-value"></a>傳回值

為 DDX 或 DDV 準備的編輯控制件的 HWND。

### <a name="remarks"></a>備註

對所有非編輯控制項使用[PrepareCtrl。](#preparectrl)

準備包括兩件事。 首先,`PrepareEditCtrl`將控件的 HWND`CDataExchange`儲存在類 中。 框架使用此句柄在 DDX 或 DDV 發生故障時將焦點還原到以前重點控制項。 其次,`PrepareEditCtrl``CDataExchange`在 類中設置一個標誌,以指示正在交換或驗證其數據的控件是編輯控制件。

自定義 DDX 或 DDV 例`PrepareEditCtrl`程的實現者 應呼叫所有編輯控制項,它們正在透過 DDX 交換資料或透過 DDV 驗證資料。

有關編寫自己的 DDX 和 DDV 例設計的詳細資訊,請參閱[技術說明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有關 DDX 與 DDV 的概述,請參考[對話框來建立 。](../../mfc/dialog-data-exchange-and-validation.md)[Dialog Box Topics](../../mfc/dialog-boxes.md)

## <a name="cdataexchangeprepareolectrl"></a><a name="prepareolectrl"></a>CDataExchange::P雷帕雷奧塞爾

框架呼叫此成員函數以準備為對話方塊資料交換 (DDX) 和驗證 (DDV) 指定的 OLE 控制項。

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>參數

*nIDC*<br/>
為 DDX 或 DDV 準備的 OLE 控制項的 ID。

### <a name="return-value"></a>傳回值

指向 OLE 控制網站的指標。

### <a name="remarks"></a>備註

使用[準備編輯Ctrl](#prepareeditctrl)改為編輯控制項或[準備Ctrl](#preparectrl)的所有其他非OLE控制項。

自定義 DDX 或 DDV 例`PrepareOleCtrl`程的實現者 應呼叫所有 OLE 控制項,它們正在透過 DDX 交換資料或透過 DDV 驗證資料。

有關編寫自己的 DDX 和 DDV 例設計的詳細資訊,請參閱[技術說明 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 有關 DDX 與 DDV 的概述,請參考[對話框來建立 。](../../mfc/dialog-data-exchange-and-validation.md)[Dialog Box Topics](../../mfc/dialog-boxes.md)

## <a name="see-also"></a>另請參閱

[MFC 樣品檢視](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)

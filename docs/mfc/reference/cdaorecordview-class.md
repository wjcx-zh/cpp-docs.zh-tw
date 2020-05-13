---
title: CDaoRecordView 類別
ms.date: 11/04/2016
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
ms.openlocfilehash: b8c411dbd29316219759351f1f1633b6e57b92e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377135"
---
# <a name="cdaorecordview-class"></a>CDaoRecordView 類別

在控制項中顯示資料庫記錄的檢視。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CDao記錄檢視:CDaoRecordView](#cdaorecordview)|建構 `CDaoRecordView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDaoRecord 檢視:Ison 第一記錄](#isonfirstrecord)|如果當前記錄是關聯記錄集中的第一個記錄,則返回非零。|
|[CDaoRecord 檢視:IslastRecord](#isonlastrecord)|如果當前記錄是關聯記錄集中的最後一條記錄,則返回非零。|
|[CDaoRecordView::OngetRecordset](#ongetrecordset)|返回指向 派生`CDaoRecordset`自的類對象的指標。 ClassWizard 會為您重寫此函數,並在必要時創建記錄集。|
|[CDao記錄檢視:移動](#onmove)|如果當前記錄已更改,則在數據源上更新它,然後移動到指定的記錄(下一個、上一個、第一個或最後一個)。|

## <a name="remarks"></a>備註

視圖是直接連接到`CDaoRecordset`物件的表單檢視。 視圖是從對話方塊樣本資源創建的,並在對話方塊範本的控制項中`CDaoRecordset`顯示 物件的欄位。 對`CDaoRecordView`象 使用對話框資料交換 (DDX) 和 DAO 記錄欄位交換 (DFX) 來自動在窗體上的控制項和記錄集的欄位之間行動資料。 `CDaoRecordView`還提供用於移動到第一個、下一個、上一個或最後一個記錄的預設實現,以及用於更新當前視圖中記錄的介面。

> [!NOTE]
> DAO 資料庫類不同於基於開放資料庫連接 (ODBC) 的 MFC 資料庫類。 所有 DAO 資料庫類名稱都有「CDao」首碼。 您仍可以使用 DAO 類訪問 ODBC 資料來源;DAO 類通常提供卓越的功能,因為它們使用 Microsoft Jet 資料庫引擎。

創建記錄檢視的最常見方法是使用應用程式嚮導。 應用程式精靈將創建記錄檢視類及其關聯的記錄集類,作為骨架初學者應用程式的一部分。

如果您只需要一個表單,則應用程式嚮導方法會更容易。 ClassWizard允許您決定在開發過程的稍後時間使用記錄檢視。 如果不使用應用程式嚮導創建記錄視圖類,則可以稍後使用 ClassWizard 創建它。 使用 ClassWizard 分別建立記錄檢視和記錄集,然後連接它們是最靈活的方法,因為它為您提供了命名記錄集類及其的更多控制權。H/.CPP 檔。 此方法還允許您在同一記錄集類上具有多個記錄視圖。

為了使最終使用者在記錄檢視中輕鬆從記錄移動到記錄,應用程式嚮導將創建功能表(和可選工具列)資源,以便移動到第一、下一個、上一個或最後一個記錄。 如果使用 ClassWizard 創建記錄檢視類,則需要使用菜單和位圖編輯器自行創建這些資源。

有關`IsOnFirstRecord`從紀錄移至紀錄的預設的資訊,請參閱`IsOnLastRecord`與 以及[文章「使用紀錄檢視](../../data/using-a-record-view-mfc-data-access.md)」,該檢視同時適用於`CRecordView`和`CDaoRecordView`。

`CDaoRecordView`追蹤使用者在記錄集中的位置,以便記錄檢視可以更新使用者介面。 當使用者移動到記錄集的任一端時,記錄檢視將禁用使用者介面物件(如功能表項或工具列按鈕)以向同一方向進一步移動。

有關聲明和使用記錄檢視和記錄集類的詳細資訊,請參閱文章[「記錄視圖](../../data/record-views-mfc-data-access.md)」中的「設計和創建記錄視圖」。 有關記錄檢視的工作原理以及如何使用它們的詳細資訊,請參閱[文章"使用記錄視圖](../../data/using-a-record-view-mfc-data-access.md)"。 所有條款均`CRecordView`適用於與`CDaoRecordView`。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="cdaorecordviewcdaorecordview"></a><a name="cdaorecordview"></a>CDao記錄檢視:CDaoRecordView

創建派生自`CDaoRecordView`的類型的物件時,調用構造函數的任一形式來初始化視圖物件並標識視圖所基於的對話框資源。

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>參數

*lpszTemplate 名稱*<br/>
包含一個 null 連接端字串,該字串是對話方塊樣本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊樣本資源的 ID 號。

### <a name="remarks"></a>備註

您可以按名稱識別資源(將字串作為參數傳遞給建構函數)或通過其 ID(傳遞未簽名的整數作為參數)。 建議使用資源識別碼。

> [!NOTE]
> 派生類必須提供其自己的構造函數。 在派生類的構造函數中,將資源名稱或`CDaoRecordView::CDaoRecordView`ID 的構造函數稱為參數。

`CDaoRecordView::OnInitialUpdate`呼叫`CWnd::UpdateData`,呼`CWnd::DoDataExchange`叫 。 此初始調用將`DoDataExchange`控制`CDaoRecordView`件 (間接)`CDaoRecordset`連接到 ClassWizard 創建的欄位數據成員。 在調用基類`CFormView::OnInitialUpdate`成員函數之前,不能使用這些數據成員。

> [!NOTE]
> 如果使用 ClassWizard,嚮導將在類聲明中定義**枚舉**值`CDaoRecordView::IDD`,並在構造函數的成員初始化清單中使用它。

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

## <a name="cdaorecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CDaoRecord 檢視:Ison 第一記錄

調用此成員函數以確定當前記錄是否是與此記錄檢視關聯的記錄集物件中的第一個記錄。

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>傳回值

如果當前記錄是記錄集中的第一個記錄,則非零;否則 0。

### <a name="remarks"></a>備註

此函數可用於編寫由 ClassWizard 編寫的預設命令更新處理程序的實現。

如果使用者移動到第一條記錄,框架將禁用移動到第一條或上一條記錄時具有的任何使用者介面物件(例如,功能表項或工具列按鈕)。

## <a name="cdaorecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CDaoRecord 檢視:IslastRecord

調用此成員函數以確定當前記錄是否是與此記錄檢視關聯的記錄集物件中的最後一條記錄。

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>傳回值

如果當前記錄是記錄集中的最後一條記錄,則非零;否則 0。

### <a name="remarks"></a>備註

此函數可用於編寫 ClassWizard 編寫的預設命令更新處理程式的實現,以支援使用者介面從記錄移動到記錄。

> [!CAUTION]
> 此功能的結果是可靠的,只不過視圖可能無法檢測記錄集的末尾,直到用戶移動過它。 使用者可能必須超出最後一條記錄,然後記錄視圖才能判斷它必須禁用任何使用者介面物件才能移動到下一條或最後一條記錄。 如果使用者移動過去最後一條記錄,然後移回最後一條記錄(或之前),記錄視圖可以跟蹤使用者在記錄集中的位置並正確禁用使用者界面物件。

## <a name="cdaorecordviewongetrecordset"></a><a name="ongetrecordset"></a>CDaoRecordView::OngetRecordset

返回指向與記錄視圖`CDaoRecordset`關聯的派生物件的指標。

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>傳回值

如果成功創建了物件`CDaoRecordset`,則指向派生物件的指標;否則為 NULL 指標。

### <a name="remarks"></a>備註

必須重寫此成員函數以構造或獲取記錄集物件,並返回指向它的指標。 如果使用 ClassWizard 聲明記錄檢視類,精靈將為您編寫預設覆蓋。 ClassWizard 的預設實現返回存儲在記錄視圖中的記錄集指標(如果存在)。 如果沒有,它將建構使用 ClassWizard 指定的類型的記錄集物件,並調用`Open`其成員 函數打開表或運行查詢,然後返回指向該物件的指標。

有關詳細資訊和範例,請參閱[文章記錄檢視:使用紀錄檢視](../../data/using-a-record-view-mfc-data-access.md)。

## <a name="cdaorecordviewonmove"></a><a name="onmove"></a>CDao記錄檢視:移動

調用此成員函數以移動到記錄集中的不同記錄,並在記錄檢視的控制項中顯示其欄位。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>參數

*nIDMove命令*<br/>
以下標準命令 ID 值之一:

- ID_RECORD_FIRST移動到記錄集中的第一個記錄。

- ID_RECORD_LAST移動到記錄集中的最後一條記錄。

- ID_RECORD_NEXT移動到記錄集中的下一個記錄。

- ID_RECORD_PREV移動到記錄集中的上一條記錄。

### <a name="return-value"></a>傳回值

如果移動成功,則非零;否則 0 如果移動請求被拒絕。

### <a name="remarks"></a>備註

預設實現調用與記錄檢視關聯的`CDaoRecordset`物件的相應 Move 成員函數。

預設情況下,`OnMove`如果使用者在記錄檢視中更改了資料來源上的現記錄,則更新該紀錄。

"應用程式精靈"創建具有"第一條記錄"、"最後一條記錄"、"下一個記錄"和"上一個記錄"功能表項的功能表資源。 如果選擇「初始工具列」選項,則「應用程式精靈」還會創建一個工具列,其中按鈕對應於這些命令。

如果移動超過記錄集中的最後一條記錄,記錄視圖將繼續顯示最後一條記錄。 如果向後移動超過第一條記錄,則記錄視圖將繼續顯示第一條記錄。

> [!CAUTION]
> 如果`OnMove`記錄集沒有記錄,則調用將引發異常。 在相應的行動操作之前調用相應的使用者介面更新`OnUpdateRecordFirst`處理`OnUpdateRecordLast`程式`OnUpdateRecordNext`函`OnUpdateRecordPrev`數 *、、 或「以確定記錄集是否具有任何記錄。

## <a name="see-also"></a>另請參閱

[CFormView 類別](../../mfc/reference/cformview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CFormView 類別](../../mfc/reference/cformview-class.md)

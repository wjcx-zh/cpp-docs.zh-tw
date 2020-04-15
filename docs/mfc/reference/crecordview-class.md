---
title: CRecordView 類別
ms.date: 11/04/2016
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
ms.openlocfilehash: b706a80f91a3c952d80da13f453a807c775b9405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368359"
---
# <a name="crecordview-class"></a>CRecordView 類別

在控制項中顯示資料庫記錄的檢視。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CRecordView:CRecordView](#crecordview)|建構 `CRecordView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRecordView::Ison 第一記錄](#isonfirstrecord)|如果當前記錄是關聯記錄集中的第一個記錄,則返回非零。|
|[CRecordView::IslastRecord](#isonlastrecord)|如果當前記錄是關聯記錄集中的最後一條記錄,則返回非零。|
|[CRecordView::開啟記錄集](#ongetrecordset)|返回指向 派生`CRecordset`自的類對象的指標。 ClassWizard 會為您重寫此函數,並在必要時創建記錄集。|
|[CRecordView::移動](#onmove)||

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CRecordView::移動](#onmove)|如果當前記錄已更改,則在數據源上更新它,然後移動到指定的記錄(下一個、上一個、第一個或最後一個)。|

## <a name="remarks"></a>備註

視圖是直接連接到`CRecordset`物件的表單檢視。 視圖是從對話方塊樣本資源創建的,並在對話方塊範本的控制項中`CRecordset`顯示 物件的欄位。 對`CRecordView`象 使用對話框資料交換 (DDX) 和記錄欄位交換 (RFX) 來自動在窗體上的控制項和記錄集的欄位之間行動資料。 `CRecordView`還提供用於移動到第一個、下一個、上一個或最後一個記錄的預設實現,以及用於更新當前查看的記錄的介面。

> [!NOTE]
> 如果使用資料存取物件 (DAO) 類別而不是開放資料庫連接 (ODBC) 類別,請使用類[CDaoRecordView。](../../mfc/reference/cdaorecordview-class.md) 有關詳細資訊,請參閱文章[概述:資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

創建記錄檢視的最常見方法是使用應用程式嚮導。 應用程式精靈將創建記錄檢視類及其關聯的記錄集類,作為骨架初學者應用程式的一部分。 如果不使用應用程式嚮導創建記錄視圖類,則可以稍後使用 ClassWizard 創建它。 如果您只需要一個表單,則應用程式嚮導方法會更容易。 ClassWizard允許您決定在開發過程的稍後時間使用記錄檢視。 使用 ClassWizard 分別建立記錄檢視和記錄集,然後連接它們是最靈活的方法,因為它為您提供了命名記錄集類及其的更多控制權。H/.CPP 檔。 此方法還允許您在同一記錄集類上具有多個記錄視圖。

為了使最終使用者在記錄檢視中輕鬆從記錄移動到記錄,應用程式嚮導將創建功能表(和可選工具列)資源,以便移動到第一、下一個、上一個或最後一個記錄。 如果使用 ClassWizard 創建記錄檢視類,則需要使用菜單和位圖編輯器自行創建這些資源。

有關從記錄移動到記錄的預設實現的資訊,請參`IsOnFirstRecord`閱`IsOnLastRecord`和[以及文章"使用記錄視圖](../../data/using-a-record-view-mfc-data-access.md)"。

`CRecordView`追蹤使用者在記錄集中的位置,以便記錄檢視可以更新使用者介面。 當使用者移動到記錄集的任一端時,記錄檢視將禁用使用者介面物件(如功能表項或工具列按鈕)以向同一方向進一步移動。

有關聲明和使用記錄檢視和記錄集類的詳細資訊,請參閱文章[「記錄視圖](../../data/record-views-mfc-data-access.md)」中的「設計和創建記錄視圖」。 有關記錄檢視的工作原理以及如何使用它們的詳細資訊,請參閱[文章"使用記錄視圖](../../data/using-a-record-view-mfc-data-access.md)"。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="crecordviewcrecordview"></a><a name="crecordview"></a>CRecordView:CRecordView

創建派生自`CRecordView`的類型的物件時,調用構造函數的任一形式來初始化視圖物件並標識視圖所基於的對話框資源。

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>參數

*lpszTemplate 名稱*<br/>
包含一個 null 連接端字串,該字串是對話方塊樣本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊樣本資源的 ID 號。

### <a name="remarks"></a>備註

您可以按名稱識別資源(將字串作為參數傳遞給建構函數)或通過其 ID(傳遞未簽名的整數作為參數)。 建議使用資源識別碼。

> [!NOTE]
> 派生類*必須*提供其自己的構造函數。 在派生類的構造函數中,將資源名稱或`CRecordView::CRecordView`ID 的構造函數稱為參數,如下例所示。

`CRecordView::OnInitialUpdate`呼叫`UpdateData`,呼`DoDataExchange`叫 。 此初始調用將`DoDataExchange`控制`CRecordView`件 (間接)`CRecordset`連接到 ClassWizard 創建的欄位數據成員。 在調用基類`CFormView::OnInitialUpdate`成員函數之前,不能使用這些數據成員。

> [!NOTE]
> 如果使用 ClassWizard,嚮導將定義**枚舉**值`CRecordView::IDD`,在類聲明中指定它,並在構造函數的成員初始化清單中使用它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

## <a name="crecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CRecordView::Ison 第一記錄

調用此成員函數以確定當前記錄是否是與此記錄檢視關聯的記錄集物件中的第一個記錄。

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>傳回值

如果當前記錄是記錄集中的第一個記錄,則非零;否則 0。

### <a name="remarks"></a>備註

此函數可用於編寫由 ClassWizard 編寫的預設命令更新處理程序的實現。

如果使用者移動到第一條記錄,框架將禁用移動到第一條或上一條記錄時具有的任何使用者介面物件。

## <a name="crecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CRecordView::IslastRecord

調用此成員函數以確定當前記錄是否是與此記錄檢視關聯的記錄集物件中的最後一條記錄。

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>傳回值

如果當前記錄是記錄集中的最後一條記錄,則非零;否則 0。

### <a name="remarks"></a>備註

此函數可用於編寫 ClassWizard 編寫的預設命令更新處理程式的實現,以支援使用者介面從記錄移動到記錄。

> [!CAUTION]
> 此功能的結果是可靠的,只不過視圖在使用者移動過去記錄集之前無法檢測到記錄集的末尾。 用戶必須超越最後一條記錄,記錄視圖才能判斷它必須禁用任何使用者介面物件才能移動到下一條或最後一條記錄。 如果使用者移動過去最後一條記錄,然後移回最後一條記錄(或之前),記錄視圖可以跟蹤使用者在記錄集中的位置並正確禁用使用者界面物件。 `IsOnLastRecord`對處理ID_RECORD_LAST命令的`OnRecordLast``CRecordset::MoveLast`實現函數的調用後也不可靠。

## <a name="crecordviewongetrecordset"></a><a name="ongetrecordset"></a>CRecordView::開啟記錄集

返回指向與記錄視圖`CRecordset`關聯的派生物件的指標。

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>傳回值

如果成功創建了物件`CRecordset`,則指向派生物件的指標;否則為 NULL 指標。

### <a name="remarks"></a>備註

必須重寫此成員函數以構造或獲取記錄集物件,並返回指向它的指標。 如果使用 ClassWizard 聲明記錄檢視類,精靈將為您編寫預設覆蓋。 ClassWizard 的預設實現返回存儲在記錄視圖中的記錄集指標(如果存在)。 如果沒有,它將建構使用 ClassWizard 指定的類型的記錄集物件,並調用`Open`其成員 函數打開表或運行查詢,然後返回指向該物件的指標。

有關詳細資訊和範例,請參閱[文章記錄檢視:使用紀錄檢視](../../data/using-a-record-view-mfc-data-access.md)。

## <a name="crecordviewonmove"></a><a name="onmove"></a>CRecordView::移動

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

預設實現調用與記錄檢視`Move`關聯的`CRecordset`物件的相應成員函數。

預設情況下,`OnMove`如果使用者在記錄檢視中更改了資料來源上的現記錄,則更新該紀錄。

"應用程式精靈"創建具有"第一條記錄"、"最後一條記錄"、"下一個記錄"和"上一個記錄"功能表項的功能表資源。 如果選擇「可停靠工具列」選項,則「應用程式精靈」還會創建一個工具列,其中按鈕對應於這些命令。

如果移動超過記錄集中的最後一條記錄,記錄視圖將繼續顯示最後一條記錄。 如果向後移動超過第一條記錄,則記錄視圖將繼續顯示第一條記錄。

> [!CAUTION]
> 如果`OnMove`記錄集沒有記錄,則調用將引發異常。 在相應的行動操作之前調用相應的使用者介面更新`OnUpdateRecordFirst`處理`OnUpdateRecordLast`程式`OnUpdateRecordNext`函`OnUpdateRecordPrev`數 *、、 或「以確定記錄集是否具有任何記錄。

## <a name="see-also"></a>另請參閱

[CFormView 類別](../../mfc/reference/cformview-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)<br/>
[CFormView 類別](../../mfc/reference/cformview-class.md)

---
title: COleDBRecordView 類別
ms.date: 11/04/2016
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
ms.openlocfilehash: b862ce5176a1fd4fa4ac48cabf7830cd8ebf3d92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599598"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView 類別

在控制項中顯示資料庫記錄的檢視。

## <a name="syntax"></a>語法

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|建構 `COleDBRecordView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDBRecordView::OnGetRowset](#ongetrowset)|傳回標準的 HRESULT 值。|
|[COleDBRecordView::OnMove](#onmove)|更新資料來源上目前的記錄 （如果已變更），然後再移到指定的記錄 （下一步、 上一個，第一個或最後一個）。|

## <a name="remarks"></a>備註

檢視是表單檢視，直接連線到`CRowset`物件。 檢視從對話方塊範本資源建立，並顯示的欄位`CRowset`對話方塊範本的控制項中的物件。 `COleDBRecordView`物件會使用對話方塊資料交換 (DDX)，並瀏覽功能內建`CRowset`、 自動化的表單上的控制項和資料列集的欄位之間的資料移動。 `COleDBRecordView` 也提供移動的預設實作第一筆、 下一步 上, 一個或最後一筆和更新目前的檢視記錄的介面。

您可以使用 DDX 函式與`COleDbRecordView`直接從資料庫資料錄集取得資料，並顯示在對話方塊控制項。 您應該使用`DDX_*`方法 (例如`DDX_Text`)，而非`DDX_Field*`函式 (例如`DDX_FieldText`) 與`COleDbRecordView`。 `DDX_FieldText` 不適用於`COleDbRecordView`因為`DDX_FieldText`採用其他引數的型別`CRecordset*`(如`CRecordView`) 或`CDaoRecordset*`(針對`CDaoRecordView`)。

> [!NOTE]
>  如果您正在使用的資料存取物件 (DAO) 類別，而不是 OLE DB 消費者範本類別，使用類別[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)改。 如需詳細資訊，請參閱文章[概觀： 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

`COleDBRecordView` 會追蹤的資料列集中的使用者的位置，以便資料錄檢視可以更新使用者介面。 當使用者移至任一端的資料列集時，資料錄檢視停用使用者介面物件，例如功能表項目或工具列按鈕 — 移動中相同的方向。

如需有關資料列集類別的詳細資訊，請參閱 <<c0> [ 使用 OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)文章。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>需求

**標頭：** afxoledb.h

##  <a name="coledbrecordview"></a>  COleDBRecordView::COleDBRecordView

建構 `COleDBRecordView` 物件。

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>參數

*lpszTemplateName*<br/>
包含以 null 結束的字串，這是對話方塊範本資源的名稱。

*nIDTemplate*<br/>
包含對話方塊範本資源的識別碼。

### <a name="remarks"></a>備註

當您建立的物件型別的衍生自`COleDBRecordView`，叫用其中一個建構函式建立的檢視物件，並找出檢視所依據的對話方塊資源。 您可以依名稱 (pass 字串做為引數的建構函式) 或依識別碼 (pass 不帶正負號的整數做為引數) 來識別資源。

> [!NOTE]
>  您的衍生的類別*必須*提供它自己的建構函式。 建構函式，在叫用建構函式， `COleDBRecordView::COleDBRecordView`、 資源名稱或識別碼做為引數。

##  <a name="ongetrowset"></a>  COleDBRecordView::OnGetRowset

傳回之控制代碼**CRowset <>** 資料錄檢視相關聯的物件。

```
virtual CRowset<>* OnGetRowset() = 0;

```

### <a name="return-value"></a>傳回值

標準的 HRESULT 值。

### <a name="remarks"></a>備註

您必須覆寫此成員函式，來建構或取得資料列集物件，並傳回給它的控制代碼。 如果您宣告您的資料錄檢視類別與 ClassWizard，精靈會為您撰寫的預設覆寫。 ClassWizard 的預設實作會傳回資料列控制代碼儲存在記錄檢視中，如果有的話。 您如果不是，它會建構類型的資料列集物件指定 ClassWizard 並呼叫其`Open`成員函式以開啟資料表或執行查詢，並再傳回物件的控制代碼。

> [!NOTE]
>  上一步 MFC 7.0`OnGetRowset`傳回的指標`CRowset`。 如果您有呼叫的程式碼`OnGetRowset`，您需要將變更的範本化的類別的傳回型別**CRowset <>**。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

如需詳細資訊和範例，請參閱文章[資料錄檢視： 使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)。

##  <a name="onmove"></a>  COleDBRecordView::OnMove

移至不同的記錄中的資料列集和顯示其欄位中記錄的控制項檢視。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>參數

*nIDMoveCommand*<br/>
其中一個下列的標準命令 ID 值：

- ID_RECORD_FIRST — 將移至資料錄集的第一個記錄。

- ID_RECORD_LAST — 移動中資料錄集的最後一筆記錄。

- ID_RECORD_NEXT — 將移至下一個資料錄集記錄。

- ID_RECORD_PREV — 將移至前一筆記錄，在資料錄集。

### <a name="return-value"></a>傳回值

如果移動不成功則為非零否則為 0，表示移動要求遭到拒絕。

### <a name="remarks"></a>備註

預設實作會呼叫適當`Move`成員函式`CRowset`資料錄檢視相關聯的物件。

根據預設，`OnMove`更新資料來源上目前的記錄，如果使用者資料錄檢視中已變更。

應用程式精靈 建立功能表資源的第一筆、 最後一筆記錄、 下一筆記錄和上一筆記錄的功能表項目。 如果您選取可停駐工具列選項，應用程式精靈 也建立工具列按鈕對應至這些命令。

如果您跳過資料錄集的最後一筆記錄時，[記錄] 檢視會繼續顯示最後一筆記錄。 如果您向後跳過第一筆記錄，[記錄] 檢視會繼續顯示第一筆記錄。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)


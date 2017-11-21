---
title: "COleDBRecordView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
dev_langs: C++
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fb13fc956ffffe2e58953aa29f02c56344b07a44
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="coledbrecordview-class"></a>COleDBRecordView 類別
在控制項中顯示資料庫記錄的檢視。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDBRecordView : public CFormView  
```  
  
## <a name="members"></a>成員  
  
### <a name="protected-constructors"></a>受保護的建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|建構 `COleDBRecordView` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDBRecordView::OnGetRowset](#ongetrowset)|傳回標準`HRESULT`值。|  
|[COleDBRecordView::OnMove](#onmove)|更新資料來源上目前的記錄 （如果已變更），然後將移至指定的記錄 （下一步、 前一個、 第一個或最後一個）。|  
  
## <a name="remarks"></a>備註  
 檢視是表單檢視，直接連接至`CRowset`物件。 檢視從對話方塊範本資源建立並顯示欄位的`CRowset`對話方塊範本的控制項中的物件。 `COleDBRecordView`物件會使用對話方塊資料交換 (DDX)，並瀏覽功能內建`CRowset`，若要自動化的表單上的控制項和資料列集的欄位之間的資料移動。 `COleDBRecordView`也提供的預設實作移動到第一個下, 一個、 上一個或最後一筆和更新記錄目前的檢視介面。  
  
 您可以使用 DDX 函式與**COleDbRecordView**可直接從資料庫資料錄集取得資料，並顯示在對話方塊的控制項。 您應該使用**DDX_\*** 方法 (例如`DDX_Text`)，而非**DDX_Field\*** 函式 (例如`DDX_FieldText`) 與**COleDbRecordView**. `DDX_FieldText`不適用於**COleDbRecordView**因為`DDX_FieldText`接受其他型別引數**CRecordset\***  (如`CRecordView`) 或**CDaoRecordset\***  (如`CDaoRecordView`)。  
  
> [!NOTE]
>  如果您正在使用的資料存取物件 (DAO) 類別，而不是 OLE DB 消費者樣板類別，使用類別[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)改為。 如需詳細資訊，請參閱文章[概觀： 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。  
  
 `COleDBRecordView`會追蹤的資料列集中的使用者的位置，使資料錄檢視可以更新使用者介面。 當使用者移至 資料列集結尾時，資料錄檢視停用使用者介面物件，例如功能表項目或工具列按鈕 — 移動中相同的方向。  
  
 如需詳細資料列集類別的詳細資訊，請參閱[使用 OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)發行項。  
  
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
  
##  <a name="coledbrecordview"></a>COleDBRecordView::COleDBRecordView  
 建構 `COleDBRecordView` 物件。  
  
```  
COleDBRecordView(LPCTSTR lpszTemplateName);  
COleDBRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>參數  
 `lpszTemplateName`  
 包含的對話方塊範本資源名稱的以 null 結尾字串。  
  
 `nIDTemplate`  
 包含對話方塊範本資源的識別碼。  
  
### <a name="remarks"></a>備註  
 當您建立的物件類型的衍生自`COleDBRecordView`，叫用的建構函式來建立檢視物件，並識別基礎檢視的對話方塊資源的其中一個。 您可以識別資源名稱 （傳遞字串做為引數的建構函式） 或它的 ID （傳遞的不帶正負號的整數，做為引數）。  
  
> [!NOTE]
>  您的衍生的類別*必須*提供它自己的建構函式。 在建構函式，來叫用建構函式， `COleDBRecordView::COleDBRecordView`、 資源名稱或識別碼做為引數。  
  
##  <a name="ongetrowset"></a>COleDBRecordView::OnGetRowset  
 傳回的控制代碼**CRowset <>**資料錄檢視相關聯的物件。  
  
```  
virtual CRowset<>* OnGetRowset() = 0;  
 
```  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
### <a name="remarks"></a>備註  
 您必須覆寫此成員函式，來建構或取得資料列集物件，並傳回它的控制代碼。 如果您宣告 ClassWizard 資料錄檢視類別，精靈會為您撰寫的預設覆寫。 ClassWizard 的預設實作會傳回資料列控制代碼儲存在資料錄檢視中，如果有的話。 建構類型的資料列集物件不是，如果您指定了與 ClassWizard 並呼叫其**開啟**成員函式，開啟資料表，或執行查詢，並再傳回物件的控制代碼。  
  
> [!NOTE]
>  若是使用 MFC 7.0 之前`OnGetRowset`傳回的指標`CRowset`。 如果您呼叫的程式碼`OnGetRowset`，您需要變更範本化類別的傳回型別**CRowset <>**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]  
  
 如需詳細資訊與範例，請參閱文章[資料錄檢視： 使用資料錄檢視](../../data/using-a-record-view-mfc-data-access.md)。  
  
##  <a name="onmove"></a>COleDBRecordView::OnMove  
 移至不同的記錄中的資料列集和顯示其欄位中記錄的控制項檢視。  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>參數  
 `nIDMoveCommand`  
 其中一個的下列標準命令 ID 值：  
  
- `ID_RECORD_FIRST`— 將移至資料錄集中的第一個記錄。  
  
- `ID_RECORD_LAST`— 將移到最後一個記錄中資料錄集。  
  
- `ID_RECORD_NEXT`— 將移至資料錄集的下一個記錄。  
  
- `ID_RECORD_PREV`— 將移至資料錄集中的前一筆記錄。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果移動成功。否則為 0，如果移動要求被拒。  
  
### <a name="remarks"></a>備註  
 預設實作會呼叫適當**移動**成員函式`CRowset`資料錄檢視相關聯的物件。  
  
 根據預設，`OnMove`更新目前的記錄資料來源上，如果使用者資料錄檢視中已變更。  
  
 應用程式精靈第一筆、 最後一筆記錄下, 一個記錄，以及上一筆記錄的功能表項目以建立功能表資源。 如果您選取可停駐工具列選項，應用程式精靈還會建立工具列含有對應至這些命令的按鈕。  
  
 如果您移動超過資料錄集中的最後一筆記錄，資料錄檢視會繼續顯示最後一筆記錄。 如果您向後移動超過第一筆資料錄，資料錄檢視會繼續顯示第一筆記錄。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)




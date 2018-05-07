---
title: CDragListBox 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
dev_langs:
- C++
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34655c244f13cb721693208fa93353582de452e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdraglistbox-class"></a>CDragListBox 類別
除了提供 Windows 清單方塊中，功能`CDragListBox`類別可讓使用者在清單方塊內移動清單方塊項目，例如檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```  
class CDragListBox : public CListBox  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDragListBox::CDragListBox](#cdraglistbox)|建構 `CDragListBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDragListBox::BeginDrag](#begindrag)|在拖曳作業開始時由架構呼叫。|  
|[CDragListBox::CancelDrag](#canceldrag)|在取消拖曳作業時，由架構呼叫。|  
|[CDragListBox::Dragging](#dragging)|在拖曳作業期間，由架構呼叫。|  
|[CDragListBox::DrawInsert](#drawinsert)|繪製拖放到清單方塊的插入的導線。|  
|[CDragListBox::Dropped](#dropped)|已卸除項目之後，由架構呼叫。|  
|[CDragListBox::ItemFromPt](#itemfrompt)|傳回座標正在拖曳的項目。|  
  
## <a name="remarks"></a>備註  
 使用這項功能的清單方塊讓使用者排序項目在清單中的方式是它們最有用。 根據預設，清單方塊會移到清單中的新位置的項目。 不過，`CDragListBox`可以自訂物件，以複製項目，而不需要移動它們。  
  
 清單方塊控制項相關聯`CDragListBox`類別不能**LBS_SORT**或**LBS_MULTIPLESELECT**樣式。 如需清單方塊樣式的說明，請參閱[清單方塊樣式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)。  
  
 若要使用現有的對話方塊中的應用程式中拖放到清單方塊，清單方塊控制項新增至您使用對話方塊編輯器的對話方塊範本，然後指派成員變數 (類別目錄的`Control`和變數類型`CDragListBox`) 對應至清單方塊在對話方塊範本中控制。  
  
 如需有關如何將控制項指派給成員變數的詳細資訊，請參閱[定義對話方塊控制項的成員變數的捷徑](../../windows/defining-member-variables-for-dialog-controls.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CDragListBox`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="begindrag"></a>  CDragListBox::BeginDrag  
 由呼叫發生事件時，framework 就可以開始拖曳作業，例如按下滑鼠左的按鈕。  
  
```  
virtual BOOL BeginDrag(CPoint pt);
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含正在拖曳的項目座標。  
  
### <a name="return-value"></a>傳回值  
 非零，如果拖曳允許，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您想要控制在拖曳作業開始時，會發生什麼事，請覆寫這個函式。 預設實作會擷取滑鼠，並會保持在拖放到模式，直到使用者按下滑鼠左鍵或右鍵按鈕或按 esc 鍵，此時取消拖曳作業。  
  
##  <a name="canceldrag"></a>  CDragListBox::CancelDrag  
 在取消拖曳作業時，由架構呼叫。  
  
```  
virtual void CancelDrag(CPoint pt);
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含正在拖曳的項目座標。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式，以處理您的清單方塊控制項的任何特殊處理。  
  
##  <a name="cdraglistbox"></a>  CDragListBox::CDragListBox  
 建構 `CDragListBox` 物件。  
  
```  
CDragListBox();
```  
  
##  <a name="dragging"></a>  CDragListBox::Dragging  
 當被拖曳的清單方塊項目內，由架構呼叫`CDragListBox`物件。  
  
```  
virtual UINT Dragging(CPoint pt);
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含 x 和 y 螢幕座標的資料指標。  
  
### <a name="return-value"></a>傳回值  
 要顯示的游標資源識別碼。 下列是可能值：  
  
- `DL_COPYCURSOR` 表示將複製的項目。  
  
- `DL_MOVECURSOR` 表示將會移動項目。  
  
- `DL_STOPCURSOR` 指出目前置放目標不是可接受。  
  
### <a name="remarks"></a>備註  
 傳回的預設行為`DL_MOVECURSOR`。 如果您想要提供額外的功能，請覆寫這個函式。  
  
##  <a name="drawinsert"></a>  CDragListBox::DrawInsert  
 由架構呼叫以繪製具有指定之索引的項目之前插入的導線。  
  
```  
virtual void DrawInsert(int nItem);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 插入點的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 值為-1 清除插入輔助線。 覆寫此函式可修改的外觀或行為插入輔助線。  
  
##  <a name="dropped"></a>  CDragListBox::Dropped  
 在卸除項目時由架構呼叫`CDragListBox`物件。  
  
```  
virtual void Dropped(
    int nSrcIndex,  
    CPoint pt);
```  
  
### <a name="parameters"></a>參數  
 *nSrcIndex*  
 指定已卸除字串之以零為起始的索引。  
  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含拖放站台的座標。  
  
### <a name="remarks"></a>備註  
 預設行為會將清單方塊項目和其資料複製到新位置，然後再刪除原始的項目。 覆寫此函式可自訂的預設行為，例如啟用清單項目拖曳到清單內的其他位置的複本。  
  
##  <a name="itemfrompt"></a>  CDragListBox::ItemFromPt  
 呼叫此函式可擷取的清單方塊項目以零為起始的索引位於`pt`。  
  
```  
int ItemFromPt(
    CPoint pt,  
    BOOL bAutoScroll = TRUE) const;  
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含在清單方塊內的點的座標。  
  
 *bAutoScroll*  
 非零，如果允許捲動，否則為 0。  
  
### <a name="return-value"></a>傳回值  
 拖放到清單方塊項目的以零為起始的索引。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 TSTCON](../../visual-cpp-samples.md)   
 [CListBox 類別](../../mfc/reference/clistbox-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CListBox 類別](../../mfc/reference/clistbox-class.md)

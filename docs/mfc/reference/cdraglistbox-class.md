---
title: "CDragListBox 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- drag list box [C++]
- dragging list items
- CDragListBox class
- Windows [C++], list boxes
- list boxes
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 3010fd9a363aa1ca1c946a6fe967a7ba415649d4
ms.lasthandoff: 02/24/2017

---
# <a name="cdraglistbox-class"></a>CDragListBox 類別
除了提供 Windows 清單方塊的功能，`CDragListBox`類別可讓使用者在清單方塊中移動清單方塊項目，例如檔案名稱。  
  
## <a name="syntax"></a>語法  
  
```  
class CDragListBox : public CListBox  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDragListBox::CDragListBox](#cdraglistbox)|建構 `CDragListBox` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDragListBox::BeginDrag](#begindrag)|在拖曳作業開始時，由架構呼叫。|  
|[CDragListBox::CancelDrag](#canceldrag)|在取消拖曳作業時，由架構呼叫。|  
|[CDragListBox::Dragging](#dragging)|在拖曳作業期間，由框架呼叫。|  
|[CDragListBox::DrawInsert](#drawinsert)|繪製拖放到清單方塊的插入輔助線。|  
|[CDragListBox::Dropped](#dropped)|已卸除項目之後，由架構呼叫。|  
|[CDragListBox::ItemFromPt](#itemfrompt)|傳回所拖曳的項目座標。|  
  
## <a name="remarks"></a>備註  
 清單方塊中的有這項功能可讓使用者排序的項目清單中的方式是最有用到它們。 根據預設，清單方塊會移到清單中的新位置的項目。 不過，`CDragListBox`物件可自訂以複製的項目，而不需要移動它們。  
  
 清單方塊控制項相關聯`CDragListBox`類別不能**LBS_SORT**或**LBS_MULTIPLESELECT**樣式。 清單方塊樣式的說明，請參閱[清單方塊樣式](../../mfc/reference/list-box-styles.md)。  
  
 若要使用現有的對話方塊中的應用程式中拖放到清單方塊，將清單方塊控制項新增至您使用對話方塊編輯器的對話方塊範本，然後指派一個成員變數 (類別目錄的`Control`和變數類型`CDragListBox`) 對應至對話方塊範本中的清單方塊控制項。  
  
 如需有關如何將控制項指派給成員變數的詳細資訊，請參閱[定義對話方塊控制項的成員變數的捷徑](../../windows/defining-member-variables-for-dialog-controls.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CDragListBox`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="begindrag"></a>CDragListBox::BeginDrag  
 由呼叫 framework 發生事件時，就可以開始拖曳作業，例如按下滑鼠左鍵。  
  
```  
virtual BOOL BeginDrag(CPoint pt);
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含要拖曳的項目座標。  
  
### <a name="return-value"></a>傳回值  
 如果拖曳允許，否則為 0，非零值。  
  
### <a name="remarks"></a>備註  
 如果您想要控制在拖曳作業開始時，會發生什麼事，請覆寫這個函式。 預設實作會捕捉到滑鼠，並且會保持在拖曳模式，直到使用者按下滑鼠左鍵或向右按鈕或按 esc 鍵，此時取消拖曳作業。  
  
##  <a name="canceldrag"></a>CDragListBox::CancelDrag  
 在取消拖曳作業時，由架構呼叫。  
  
```  
virtual void CancelDrag(CPoint pt);
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含要拖曳的項目座標。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式來處理您的清單方塊控制項的任何特殊處理。  
  
##  <a name="cdraglistbox"></a>CDragListBox::CDragListBox  
 建構 `CDragListBox` 物件。  
  
```  
CDragListBox();
```  
  
##  <a name="dragging"></a>CDragListBox::Dragging  
 當被拖曳的清單方塊項目內，由框架呼叫`CDragListBox`物件。  
  
```  
virtual UINT Dragging(CPoint pt);
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含 x 和 y 螢幕座標的資料指標。  
  
### <a name="return-value"></a>傳回值  
 要顯示的游標資源識別碼。 下列是可能︰  
  
- `DL_COPYCURSOR`表示將複製的項目。  
  
- `DL_MOVECURSOR`表示將會移動項目。  
  
- `DL_STOPCURSOR`指出目前的置放目標不是可接受。  
  
### <a name="remarks"></a>備註  
 預設行為會傳回`DL_MOVECURSOR`。 如果您想要提供額外的功能，請覆寫這個函式。  
  
##  <a name="drawinsert"></a>CDragListBox::DrawInsert  
 若要繪製具有指定索引的項目之前插入輔助線架構呼叫。  
  
```  
virtual void DrawInsert(int nItem);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 插入點的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 值為-1 會清除插入輔助線。 覆寫此函式可修改的外觀或行為插入輔助線。  
  
##  <a name="dropped"></a>CDragListBox::Dropped  
 卸除項目內時，由框架呼叫`CDragListBox`物件。  
  
```  
virtual void Dropped(
    int nSrcIndex,  
    CPoint pt);
```  
  
### <a name="parameters"></a>參數  
 *nSrcIndex*  
 指定已卸除字串之以零為起始的索引。  
  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含的儲藏室座標。  
  
### <a name="remarks"></a>備註  
 預設行為將清單方塊項目和其資料複製到新位置，，然後刪除原始的項目。 覆寫此函式可自訂的預設行為，例如啟用清單方塊項目拖曳到清單中的其他位置的複本。  
  
##  <a name="itemfrompt"></a>CDragListBox::ItemFromPt  
 呼叫此函式可擷取清單方塊項目的以零為起始的索引位於`pt`。  
  
```  
int ItemFromPt(
    CPoint pt,  
    BOOL bAutoScroll = TRUE) const;  
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)物件，其中包含在清單方塊內的點的座標。  
  
 *bAutoScroll*  
 如果允許捲動，否則為 0，非零值。  
  
### <a name="return-value"></a>傳回值  
 拖放到清單方塊項目的以零為起始的索引。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 TSTCON](../../visual-cpp-samples.md)   
 [CListBox 類別](../../mfc/reference/clistbox-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CListBox 類別](../../mfc/reference/clistbox-class.md)


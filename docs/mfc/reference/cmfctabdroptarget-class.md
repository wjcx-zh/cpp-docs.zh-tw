---
title: "CMFCTabDropTarget 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabDropTarget class
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 31f9950df5974fe1561d601d4e9c26b3e8a96a62
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget 類別
提供索引標籤控制項和 OLE 程式庫之間的通訊機制。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCTabDropTarget : public COleDropTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|說明|  
|`CMFCTabDropTarget::CMFCTabDropTarget`|預設建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|在使用者拖曳物件到索引標籤視窗時，由架構呼叫。 (覆寫[COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)。)|  
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|當使用者拖曳物件具有焦點的索引標籤視窗之外，由架構呼叫。 (覆寫[COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave)。)|  
|[CMFCTabDropTarget::OnDragOver](#ondragover)|當使用者將物件拖曳至索引標籤視窗具有焦點時，由架構呼叫。 (覆寫[COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)。)|  
|[CMFCTabDropTarget::OnDropEx](#ondropex)|當使用者放開滑鼠按鈕，在拖曳作業結束時，由架構呼叫。 (覆寫[COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。)|  
|[CMFCTabDropTarget::Register](#register)|註冊控制項為可為 OLE 拖放作業的目標。|  
  
### <a name="remarks"></a>備註  
 這個類別提供拖放支援`CMFCBaseTabCtrl`類別。 如果您的應用程式初始化 OLE 程式庫使用[AfxOleInit](ole-initialization.md#afxoleinit)函式，`CMFCBaseTabCtrl`物件註冊本身拖放作業。  
  
 `CMFCTabDropTarget`類別會擴充基底類別，藉由在拖曳作業時使用中，會在游標下的索引標籤。 如需拖放作業的詳細資訊，請參閱[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構 `CMFCTabDropTarget` 物件及使用其 `Register` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&39;](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)  
  
 [CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxbasetabctrl.h  
  
##  <a name="ondragenter"></a>CMFCTabDropTarget::OnDragEnter  
 在使用者拖曳物件到索引標籤視窗時，由架構呼叫。  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pWnd`|未使用。|  
|[in] `pDataObject`|在使用者拖曳物件的指標。|  
|[in] `dwKeyState`|包含輔助按鍵的狀態。 這是下列任何數目的組合︰ `MK_CONTROL`， `MK_SHIFT`， `MK_ALT`， `MK_LBUTTON`， `MK_MBUTTON`，和`MK_RBUTTON`。|  
|[in] `point`|在用戶端座標中的游標位置。|  
  
### <a name="return-value"></a>傳回值  
 如果下拉式清單就會發生在所指定的位置會造成的效果`point`。 它可以是下列一或多項動作︰  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>備註  
 這個方法會傳回`DROPEFFECT_NONE`如果工具列架構不是自訂模式，或無法使用剪貼簿資料格式。 否則，它會傳回呼叫結果`CMFCBaseTabCtrl::OnDragEnter`使用提供的參數。  
  
 如需自訂模式的詳細資訊，請參閱[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。  
  
##  <a name="ondragleave"></a>CMFCTabDropTarget::OnDragLeave  
 當使用者拖曳物件具有焦點的索引標籤視窗之外，由架構呼叫。  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pWnd`|未使用。|  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫`CMFCBaseTabCtrl::OnDragLeave`方法，以執行拖曳作業。  
  
##  <a name="ondragover"></a>CMFCTabDropTarget::OnDragOver  
 當使用者將物件拖曳至索引標籤視窗具有焦點時，由架構呼叫。  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pWnd`|未使用。|  
|[in] `pDataObject`|在使用者拖曳物件的指標。|  
|[in] `dwKeyState`|包含輔助按鍵的狀態。 這是下列任何數目的組合︰ `MK_CONTROL`， `MK_SHIFT`， `MK_ALT`， `MK_LBUTTON`， `MK_MBUTTON`，和`MK_RBUTTON`。|  
|[in] `point`|滑鼠指標在用戶端座標中的位置。|  
  
### <a name="return-value"></a>傳回值  
 如果下拉式清單就會發生在所指定的位置會造成的效果`point`。 它可以是下列一或多項動作︰  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>備註  
 此方法可讓 active 拖曳作業時，會在游標下的索引標籤。 它會傳回`DROPEFFECT_NONE`如果工具列架構不是自訂模式，或無法使用剪貼簿資料格式。 否則，它會傳回呼叫結果`CMFCBaseTabCtrl::OnDragOver`使用提供的參數。  
  
 如需自訂模式的詳細資訊，請參閱[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。  
  
##  <a name="ondropex"></a>CMFCTabDropTarget::OnDropEx  
 當使用者放開滑鼠按鈕，在拖曳作業結束時，由架構呼叫。  
  
```  
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pWnd`|未使用。|  
|[in] `pDataObject`|在使用者拖曳物件的指標。|  
|[in] `dropEffect`|預設的拖放作業。|  
|[in] `dropList`|未使用。|  
|[in] `point`|滑鼠指標在用戶端座標中的位置。|  
  
### <a name="return-value"></a>傳回值  
 產生的置放效果。 它可以是下列一或多項動作︰  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫`CMFCBaseTabCtrl::OnDrop`如果工具列架構為自訂模式，而且剪貼簿資料格式可以使用。 如果呼叫`CMFCBaseTabCtrl::OnDrop`傳回非零值，這個方法會傳回所指定的預設置放效果`dropEffect`。 否則，這個方法會傳回`DROPEFFECT_NONE`。 如需拖放效果的詳細資訊，請參閱[COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。  
  
 如需自訂模式的詳細資訊，請參閱[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。  
  
##  <a name="register"></a>CMFCTabDropTarget::Register  
 註冊控制項為可為 OLE 拖放作業的目標。  
  
```  
BOOL Register(CMFCBaseTabCtrl *pOwner);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `pOwner`|要登錄為置放目標的索引標籤控制項。|  
  
### <a name="return-value"></a>傳回值  
 非零，如果登錄成功。否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register)註冊控制項拖放作業。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [拖放 (OLE)](../../mfc/drag-and-drop-ole.md)





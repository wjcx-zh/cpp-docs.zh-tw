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
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ff17f7312f5e04b6ae900e792523155705a3b4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget 類別
提供索引標籤控制項和 OLE 程式庫之間的溝通機制。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCTabDropTarget : public COleDropTarget  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCTabDropTarget::CMFCTabDropTarget`|預設建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|在使用者拖曳物件到索引標籤視窗時，由架構呼叫。 (覆寫[COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)。)|  
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|在使用者拖曳物件之外的索引標籤視窗具有焦點時，由架構呼叫。 (覆寫[COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave)。)|  
|[CMFCTabDropTarget::OnDragOver](#ondragover)|當使用者將物件拖曳至 [索引標籤] 視窗具有焦點時，由架構呼叫。 (覆寫[COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)。)|  
|[CMFCTabDropTarget::OnDropEx](#ondropex)|當使用者放開滑鼠按鈕，在拖曳作業結束時由架構呼叫。 (覆寫[COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。)|  
|[CMFCTabDropTarget::Register](#register)|可以做為 OLE 拖放作業目標的其中一個註冊控制項。|  
  
### <a name="remarks"></a>備註  
 這個類別提供拖放支援`CMFCBaseTabCtrl`類別。 如果您的應用程式來初始化 OLE 程式庫[AfxOleInit](ole-initialization.md#afxoleinit)函式，`CMFCBaseTabCtrl`物件本身註冊為拖放作業。  
  
 `CMFCTabDropTarget`類別會擴充其基底類別，藉由拖曳作業發生作用中時，游標下的是 [] 索引標籤。 如需拖放作業的詳細資訊，請參閱[拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構 `CMFCTabDropTarget` 物件及使用其 `Register` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]  
  
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
|[輸入] `pWnd`|未使用。|  
|[輸入] `pDataObject`|在使用者拖曳物件的指標。|  
|[輸入] `dwKeyState`|包含輔助按鍵的狀態。 這是任意數目的下列組合： `MK_CONTROL`， `MK_SHIFT`， `MK_ALT`， `MK_LBUTTON`， `MK_MBUTTON`，和`MK_RBUTTON`。|  
|[輸入] `point`|用戶端座標中的資料指標的位置。|  
  
### <a name="return-value"></a>傳回值  
 如果下拉式清單，就會發生在所指定的位置會造成的效果`point`。 它可以是下列一或多個項目：  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>備註  
 這個方法會傳回`DROPEFFECT_NONE`如果工具列架構不是自訂模式，或無法使用剪貼簿資料格式。 否則，它會傳回呼叫`CMFCBaseTabCtrl::OnDragEnter`與提供的參數。  
  
 如需自訂模式的詳細資訊，請參閱[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。  
  
##  <a name="ondragleave"></a>CMFCTabDropTarget::OnDragLeave  
 在使用者拖曳物件之外的索引標籤視窗具有焦點時，由架構呼叫。  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[輸入] `pWnd`|未使用。|  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫`CMFCBaseTabCtrl::OnDragLeave`方法，以執行拖曳作業。  
  
##  <a name="ondragover"></a>CMFCTabDropTarget::OnDragOver  
 當使用者將物件拖曳至 [索引標籤] 視窗具有焦點時，由架構呼叫。  
  
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
|[輸入] `pWnd`|未使用。|  
|[輸入] `pDataObject`|在使用者拖曳物件的指標。|  
|[輸入] `dwKeyState`|包含輔助按鍵的狀態。 這是任意數目的下列組合： `MK_CONTROL`， `MK_SHIFT`， `MK_ALT`， `MK_LBUTTON`， `MK_MBUTTON`，和`MK_RBUTTON`。|  
|[輸入] `point`|滑鼠指標在用戶端座標中的位置。|  
  
### <a name="return-value"></a>傳回值  
 如果下拉式清單，就會發生在所指定的位置會造成的效果`point`。 它可以是下列一或多個項目：  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>備註  
 這個方法會在拖曳作業發生作用中時，游標下的是 [] 索引標籤。 它會傳回`DROPEFFECT_NONE`如果工具列架構不是自訂模式，或無法使用剪貼簿資料格式。 否則，它會傳回呼叫`CMFCBaseTabCtrl::OnDragOver`與提供的參數。  
  
 如需自訂模式的詳細資訊，請參閱[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。  
  
##  <a name="ondropex"></a>CMFCTabDropTarget::OnDropEx  
 當使用者放開滑鼠按鈕，在拖曳作業結束時由架構呼叫。  
  
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
|[輸入] `pWnd`|未使用。|  
|[輸入] `pDataObject`|在使用者拖曳物件的指標。|  
|[輸入] `dropEffect`|預設拖放作業。|  
|[輸入] `dropList`|未使用。|  
|[輸入] `point`|滑鼠指標在用戶端座標中的位置。|  
  
### <a name="return-value"></a>傳回值  
 產生的置放效果。 它可以是下列一或多個項目：  
  
- `DROPEFFECT_NONE`  
  
- `DROPEFFECT_COPY`  
  
- `DROPEFFECT_MOVE`  
  
- `DROPEFFECT_LINK`  
  
- `DROPEFFECT_SCROLL`  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫`CMFCBaseTabCtrl::OnDrop`如果工具列 framework 是以自訂模式，可剪貼簿資料格式。 如果呼叫`CMFCBaseTabCtrl::OnDrop`傳回非零值，這個方法會傳回所指定的預設置放效果`dropEffect`。 否則，這個方法會傳回`DROPEFFECT_NONE`。 如需拖放效果的詳細資訊，請參閱[COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。  
  
 如需自訂模式的詳細資訊，請參閱[CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。  
  
##  <a name="register"></a>CMFCTabDropTarget::Register  
 可以做為 OLE 拖放作業目標的其中一個註冊控制項。  
  
```  
BOOL Register(CMFCBaseTabCtrl *pOwner);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[輸入] `pOwner`|要登錄為置放目標的索引標籤控制項。|  
  
### <a name="return-value"></a>傳回值  
 如果登錄成功，則為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register)註冊拖放作業的控制項。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [拖放 (OLE)](../../mfc/drag-and-drop-ole.md)




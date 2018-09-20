---
title: CMFCTabDropTarget 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 717be77589e31292fe6adbb4920a704794979a57
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711629"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget 類別
提供索引標籤控制項和 OLE 程式庫之間的通訊機制。  
  
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
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|當使用者拖曳物件到索引標籤視窗時，由架構呼叫。 (覆寫[COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)。)|  
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|當使用者拖曳物件擁有焦點的索引標籤視窗之外，由架構呼叫。 (覆寫[COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave)。)|  
|[CMFCTabDropTarget::OnDragOver](#ondragover)|當使用者拖曳物件拖曳至索引標籤視窗具有焦點時，由架構呼叫。 (覆寫[COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)。)|  
|[CMFCTabDropTarget::OnDropEx](#ondropex)|當使用者放開滑鼠按鈕，在拖曳作業結束時由架構呼叫。 (覆寫[COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。)|  
|[CMFCTabDropTarget::Register](#register)|將控制項註冊為可以是 OLE 拖放作業目標的其中一個。|  
  
### <a name="remarks"></a>備註  
 這個類別會提供拖放支援`CMFCBaseTabCtrl`類別。 如果您的應用程式來初始化 OLE 程式庫[AfxOleInit](ole-initialization.md#afxoleinit)函式，`CMFCBaseTabCtrl`物件會將本身報名拖放作業。  
  
 `CMFCTabDropTarget`類別會擴充其基底類別，藉由拖曳作業發生作用中時，游標下的是 [] 索引標籤。 如需拖放作業的詳細資訊，請參閱 <<c0> [ 拖放 (OLE)](../../mfc/drag-and-drop-ole.md)。  
  
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
  
##  <a name="ondragenter"></a>  CMFCTabDropTarget::OnDragEnter  
 當使用者拖曳物件到索引標籤視窗時，由架構呼叫。  
  
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
|*pWnd*|[in]未使用。|  
|*pDataObject*|[in]在使用者拖曳物件的指標。|  
|*dwKeyState*|[in]包含的輔助按鍵的狀態。 這是任意數目的下列組合： MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。|  
|*點*|[in]工作區座標中的游標位置。|  
  
### <a name="return-value"></a>傳回值  
 如果下拉式清單，就會發生在所指定的位置會造成的影響*點*。 它可以是下列其中一個或多個項目：  
  
- DROPEFFECT_NONE  
  
- DROPEFFECT_COPY  
  
- DROPEFFECT_MOVE  
  
- DROPEFFECT_LINK  
  
- DROPEFFECT_SCROLL  
  
### <a name="remarks"></a>備註  
 如果工具列架構並不會在自訂模式，或無法使用剪貼簿資料格式，這個方法會傳回 DROPEFFECT_NONE。 否則，它會傳回呼叫`CMFCBaseTabCtrl::OnDragEnter`使用提供的參數。  
  
 如需有關自訂模式的詳細資訊，請參閱 < [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。  
  
##  <a name="ondragleave"></a>  CMFCTabDropTarget::OnDragLeave  
 當使用者拖曳物件擁有焦點的索引標籤視窗之外，由架構呼叫。  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|*pWnd*|[in]未使用。|  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫`CMFCBaseTabCtrl::OnDragLeave`方法，以執行拖曳作業。  
  
##  <a name="ondragover"></a>  CMFCTabDropTarget::OnDragOver  
 當使用者拖曳物件拖曳至索引標籤視窗具有焦點時，由架構呼叫。  
  
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
|*pWnd*|[in]未使用。|  
|*pDataObject*|[in]在使用者拖曳物件的指標。|  
|*dwKeyState*|[in]包含的輔助按鍵的狀態。 這是任意數目的下列組合： MK_CONTROL、 MK_SHIFT、 MK_ALT、 MK_LBUTTON、 MK_MBUTTON 和 MK_RBUTTON。|  
|*點*|[in]在 工作區座標中滑鼠指標的位置。|  
  
### <a name="return-value"></a>傳回值  
 如果下拉式清單，就會發生在所指定的位置會造成的影響*點*。 它可以是下列其中一個或多個項目：  
  
- DROPEFFECT_NONE  
  
- DROPEFFECT_COPY  
  
- DROPEFFECT_MOVE  
  
- DROPEFFECT_LINK  
  
- DROPEFFECT_SCROLL  
  
### <a name="remarks"></a>備註  
 這個方法會在拖曳作業發生作用中時，游標下的是 [] 索引標籤。 如果工具列架構並不會在自訂模式，或無法使用剪貼簿資料格式，則會傳回 DROPEFFECT_NONE。 否則，它會傳回呼叫`CMFCBaseTabCtrl::OnDragOver`使用提供的參數。  
  
 如需有關自訂模式的詳細資訊，請參閱 < [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。  
  
##  <a name="ondropex"></a>  CMFCTabDropTarget::OnDropEx  
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
|*pWnd*|[in]未使用。|  
|*pDataObject*|[in]在使用者拖曳物件的指標。|  
|*dropEffect*|[in]預設的拖放作業。|  
|*下拉清單*|[in]未使用。|  
|*點*|[in]在 工作區座標中滑鼠指標的位置。|  
  
### <a name="return-value"></a>傳回值  
 產生的拖放效果。 它可以是下列其中一個或多個項目：  
  
- DROPEFFECT_NONE  
  
- DROPEFFECT_COPY  
  
- DROPEFFECT_MOVE  
  
- DROPEFFECT_LINK  
  
- DROPEFFECT_SCROLL  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫`CMFCBaseTabCtrl::OnDrop`如果工具列架構已自訂模式，而且可用的剪貼簿資料格式。 如果在呼叫`CMFCBaseTabCtrl::OnDrop`傳回非零值，這個方法會傳回所指定的預設置放效果*dropEffect*。 否則，這個方法會傳回 DROPEFFECT_NONE。 如需拖放效果的詳細資訊，請參閱[COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)。  
  
 如需有關自訂模式的詳細資訊，請參閱 < [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)。 如需剪貼簿資料格式的詳細資訊，請參閱[COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)。  
  
##  <a name="register"></a>  CMFCTabDropTarget::Register  
 將控制項註冊為可以是 OLE 拖放作業目標的其中一個。  
  
```  
BOOL Register(CMFCBaseTabCtrl *pOwner);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|*pOwner*|[in]要登錄為置放目標的索引標籤控制項。|  
  
### <a name="return-value"></a>傳回值  
 非零值，如果登錄成功;否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register)註冊拖放作業的控制項。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [拖放 (OLE)](../../mfc/drag-and-drop-ole.md)




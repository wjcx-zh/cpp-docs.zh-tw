---
title: CDialogBar 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
dev_langs:
- C++
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ff69a4974cd85471b0cfa039f32ee0c1a76f82a
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336380"
---
# <a name="cdialogbar-class"></a>CDialogBar 類別
在控制列中提供 Windows 非強制回應對話方塊的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CDialogBar : public CControlBar  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDialogBar::CDialogBar](#cdialogbar)|建構 `CDialogBar` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDialogBar::Create](#create)|建立 Windows 對話方塊列，並將它附加至`CDialogBar`物件。|  
  
## <a name="remarks"></a>備註  
 對話方塊列，其中包含使用者可以使用 tab 鍵之間的標準 Windows 控制項，類似於對話方塊。 另一個的相似度就是您建立來代表對話方塊列的對話方塊範本。  
  
 建立和使用對話方塊列是類似於建立和使用`CFormView`物件。 首先，使用[對話方塊編輯器](../../windows/dialog-editor.md)定義樣式 WS_CHILD 的對話方塊範本和任何其他樣式。 範本不能有 WS_VISIBLE 的樣式。 在您的應用程式程式碼中呼叫建構函式來建構`CDialogBar`物件，然後呼叫`Create`建立對話方塊列視窗，並將其附加至`CDialogBar`物件。  
  
 如需詳細資訊`CDialogBar`，請參閱文章[對話方塊列](../../mfc/dialog-bars.md)並[技術提示 31](../../mfc/tn031-control-bars.md)，控制列。  
  
> [!NOTE]
>  在目前的版本中，`CDialogBar`物件不能在裝載 Windows Form 控制項。 如需 Visual c + + 的 Windows Form 控制項的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CDialogBar`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxext.h  
  
##  <a name="cdialogbar"></a>  CDialogBar::CDialogBar  
 建構 `CDialogBar` 物件。  
  
```  
CDialogBar();
```  
  
##  <a name="create"></a>  CDialogBar::Create  
 載入對話方塊資源範本，由指定`lpszTemplateName`或是`nIDTemplate`、 建立對話方塊列視窗、 設定其樣式中，並將其與相關聯`CDialogBar`物件。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID);

 
virtual BOOL Create(
    CWnd* pParentWnd,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *pParentWnd*  
 父代指標`CWnd`物件。  
  
 *lpszTemplateName*  
 名稱的指標`CDialogBar`物件的對話方塊中的資源範本。  
  
 *nStyle*  
 工具列的樣式。 支援的其他工具列樣式如下：  
  
- CBRS_TOP 控制列是在框架視窗的頂端。  
  
- CBRS_BOTTOM 控制列是在框架視窗的底部。  
  
- 父代調整大小時，不會重新定位 CBRS_NOALIGN 控制列。  
  
- CBRS_TOOLTIPS 控制列會顯示工具提示。  
  
- CBRS_SIZE_DYNAMIC 控制列是動態的。  
  
- 已修正 CBRS_SIZE_FIXED 控制列。  
  
- 浮動 CBRS_FLOATING 控制列。  
  
- CBRS_FLYBY 狀態列會顯示按鈕的相關資訊。  
  
- CBRS_HIDE_INPLACE 控制列不會顯示給使用者。  
  
 *nID*  
 對話方塊列控制項識別碼。  
  
 *nIDTemplate*  
 資源識別碼`CDialogBar`物件的對話方塊範本。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您指定的 CBRS_TOP 或 CBRS_BOTTOM 對齊樣式，對話方塊列的寬度是框架視窗的高度是所指定的資源*nIDTemplate*。 如果您指定的 CBRS_LEFT 或 CBRS_RIGHT 對齊樣式，對話方塊列的高度是框架視窗的寬度就是所指定的資源*nIDTemplate*。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CTRLBARS](../../visual-cpp-samples.md)   
 [CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFormView 類別](../../mfc/reference/cformview-class.md)   
 [CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)

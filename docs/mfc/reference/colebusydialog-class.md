---
title: "COleBusyDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
dev_langs:
- C++
helpviewer_keywords:
- Server Not Responding dialog box
- Server Busy dialog box
- COleBusyDialog class
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0c3ed264cdb83bc97337f13279a20f26b21d454b
ms.lasthandoff: 02/24/2017

---
# <a name="colebusydialog-class"></a>COleBusyDialog 類別
用於 OLE 的 [伺服器沒有回應] 或 [伺服器忙碌] 對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class COleBusyDialog : public COleDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|建構 `COleBusyDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleBusyDialog::DoModal](#domodal)|顯示 OLE 伺服器忙碌 對話方塊。|  
|[COleBusyDialog::GetSelectionType](#getselectiontype)|決定在對話方塊中進行選擇。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleBusyDialog::m_bz](#m_bz)|型別的結構**OLEUIBUSY**控制 對話方塊中的行為。|  
  
## <a name="remarks"></a>備註  
 建立類別的物件`COleBusyDialog`當您想要呼叫這些對話方塊。 之後`COleBusyDialog`在建構物件，您可以使用[m_bz](#m_bz)結構初始化的值或在對話方塊中控制項的狀態。 `m_bz`結構的型別是**OLEUIBUSY**。 如需有關如何使用這個對話方塊類別的詳細資訊，請參閱[DoModal](#domodal)成員函式。  
  
> [!NOTE]
>  應用程式精靈產生的容器程式碼會使用這個類別。  
  
 如需詳細資訊，請參閱[OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需有關特定 OLE 對話方塊的詳細資訊，請參閱文章[OLE 中的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleBusyDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxodlgs.h  
  
##  <a name="colebusydialog"></a>COleBusyDialog::COleBusyDialog  
 此函式只建構`COleBusyDialog`物件。  
  
```  
explicit COleBusyDialog(
    HTASK htaskBusy,  
    BOOL bNotResponding = FALSE,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 *htaskBusy*  
 忙線中的 「 伺服器 」 工作的控制代碼。  
  
 *bNotResponding*  
 如果**TRUE**，呼叫沒有回應 對話方塊，而非伺服器忙碌 對話方塊。 沒有回應 對話方塊中的文字會稍有不同於 伺服器忙碌 對話方塊中的文字，並已停用 取消 按鈕。  
  
 `dwFlags`  
 建立旗標。 可以包含零或多個以位元 OR 運算子結合的下列值︰  
  
- **BZ_DISABLECANCELBUTTON**呼叫對話方塊時，停用 [取消] 按鈕。  
  
- **BZ_DISABLESWITCHTOBUTTON**呼叫對話方塊時，停用 [切換至] 按鈕。  
  
- **BZ_DISABLERETRYBUTTON**呼叫對話方塊時，停用重試 按鈕。  
  
 `pParentWnd`  
 會指向父系或擁有者視窗物件 (型別`CWnd`) 對話方塊物件所屬。 如果是**NULL**，主應用程式視窗來設定對話方塊物件的父視窗。  
  
### <a name="remarks"></a>備註  
 若要顯示對話方塊，請呼叫[DoModal](#domodal)。  
  
 如需詳細資訊，請參閱[OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="domodal"></a>COleBusyDialog::DoModal  
 呼叫此函式來顯示 OLE 伺服器忙碌中或伺服器沒有回應 對話方塊。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
- **IDOK**如果對話方塊已成功地顯示。  
  
- **IDCANCEL**如果使用者已取消的對話方塊。  
  
- **IDABORT**發生錯誤。 如果**IDABORT**會傳回，呼叫`COleDialog::GetLastError`成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱[OleUIBusy](http://msdn.microsoft.com/library/windows/desktop/ms680125)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化不同的對話方塊控制項[m_bz](#m_bz)結構，您應該執行這項操作之前，先呼叫`DoModal`，但在建構對話方塊物件之後。  
  
 如果`DoModal`傳回**IDOK**，您可以呼叫其他成員函式來擷取設定或已由使用者輸入 對話方塊中的資訊。  
  
##  <a name="getselectiontype"></a>COleBusyDialog::GetSelectionType  
 呼叫此函式可取得使用者在 [伺服器忙碌] 對話方塊中選擇的選取項目類型。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 型別所做的選擇。  
  
### <a name="remarks"></a>備註  
 傳回型別值由**選取**中宣告列舉型別`COleBusyDialog`類別。  
  
```  
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```  
  
 請依照下列這些值的簡短描述︰  
  
- **COleBusyDialog::switchTo**已按下切換到按鈕。  
  
- **COleBusyDialog::retry**重試 按鈕已按下。  
  
- **COleBusyDialog::callUnblocked**呼叫啟用伺服器已解除封鎖。  
  
##  <a name="m_bz"></a>COleBusyDialog::m_bz  
 型別的結構**OLEUIBUSY**可用來控制伺服器忙碌 對話方塊的行為。  
  
```  
OLEUIBUSY m_bz;  
```  
  
### <a name="remarks"></a>備註  
 您可以修改此結構的成員，直接或透過成員函式。  
  
 如需詳細資訊，請參閱[OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)


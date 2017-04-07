---
title: "CMFCTasksPaneTaskGroup 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsBottom
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsCollapsed
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsSpecial
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_lstTasks
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rect
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rectGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_strName
dev_langs:
- C++
helpviewer_keywords:
- CMFCTasksPaneTaskGroup class
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
caps.latest.revision: 33
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 405a69a0c7d8c4179b36e1beec09fdfa7acd2d7b
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup 類別
`CMFCTasksPaneTaskGroup`類別是所使用的 helper 類別[CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)控制項。 屬於類型 `CMFCTasksPaneTaskGroup` 的物件表示「 *工作群組*」(Task Group)。 工作群組是 Framework 顯示在具有摺疊按鈕之不同方塊中的項目清單。 方塊可以有選擇性的標題 (群組名稱)。 如果群組已摺疊，工作清單是不可見的。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCTasksPaneTaskGroup : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|建構 `CMFCTasksPaneTaskGroup` 物件。|  
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|判斷目前的工作群組的存取範圍資料。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|決定是否要將工作群組對齊工作窗格控制項的底部。|  
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|決定是否要摺疊，工作群組。|  
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|判斷是否要為工作群組*特殊。* 架構會以不同的色彩顯示特殊的標題。|  
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|包含內部工作的清單。|  
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|指定在群組標題的周框矩形。|  
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|指定群組的周框矩形。|  
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|指定群組的名稱。|  
  
## <a name="remarks"></a>備註  
 下圖顯示已展開的工作群組︰  
  
 ![展開的工作群組](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
 下圖顯示摺疊的工作群組︰  
  
 ![摺疊的工作群組](../../mfc/reference/media/nexttaskgrpcollapse.png "nexttaskgrpcollapse")  
  
 下圖顯示沒有標題的工作群組︰  
  
 ![沒有標題的工作群組](../../mfc/reference/media/nexttaskgrpnocapt.png "nexttaskgrpnocapt")  
  
 下圖顯示兩個工作群組。 第一個工作群組設定標記特殊`m_bIsSpecial`旗標設為`TRUE`，而不是特殊的第二個工作群組。 請注意，第一個工作群組的標題深大於第二個工作群組︰  
  
 ![特殊工作群組](../../mfc/reference/media/nexttaskgrpspecial.png "nexttaskgrpspecial")  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxTasksPane.h  
  
##  <a name="cmfctaskspanetaskgroup"></a>CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup  
 建構 `CMFCTasksPaneTaskGroup` 物件。  
  
```  
CMFCTasksPaneTaskGroup(
    LPCTSTR lpszName,  
    BOOL bIsBottom,  
    BOOL bIsSpecial=FALSE,  
    BOOL bIsCollapsed=FALSE,  
    CMFCTasksPanePropertyPage* pPage=NULL,  
    HICON hIcon=NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 在群組標題中指定的群組名稱。  
  
 `bIsBottom`  
 指定群組是否工作窗格控制項的底部對齊。  
  
 `bIsSpecial`  
 指定是否要將群組指定為*特殊*，因此，是否在群組標題會填入不同的色彩。  
  
 `bIsCollapsed`  
 指定是否要摺疊群組。  
  
 `pPage`  
 指定這個工作群組所屬的屬性頁。  
  
 `hIcon`  
 指定在群組標題中顯示的圖示。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_bisbottom"></a>CMFCTasksPaneTaskGroup::m_bIsBottom  
 決定是否要將工作群組對齊工作窗格控制項的底部。  
  
```  
BOOL m_bIsBottom;  
```  
  
### <a name="remarks"></a>備註  
 只有一個群組可以工作窗格控制項的底部對齊。 最後必須加入這個工作群組。 如需詳細資訊，請參閱[CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup)。  
  
##  <a name="m_biscollapsed"></a>CMFCTasksPaneTaskGroup::m_bIsCollapsed  
 決定是否要摺疊，工作群組。  
  
```  
BOOL m_bIsCollapsed;  
```  
  
### <a name="remarks"></a>備註  
 您可以啟用或停用的功能，在工作窗格中摺疊群組，藉由呼叫[CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse)。  
  
##  <a name="m_bisspecial"></a>CMFCTasksPaneTaskGroup::m_bIsSpecial  
 判斷是否要為工作群組*特殊*和特殊工作群組的標題是否應該由不同的色彩。  
  
```  
BOOL m_bIsSpecial;  
```  
  
### <a name="remarks"></a>備註  
 如果您的應用程式使用 Windows XP 視覺化佈景主題和`m_bIsSpecial`是`FALSE`，架構會呼叫`DrawThemeBackground`與`EBP_NORMALGROUPBACKGROUND`旗標。 如果`m_bIsSpecial`是`TRUE`，架構會呼叫`DrawThemeBackground`與`EBP_SPECIALGROUPBACKGROUND`旗標。  
  
##  <a name="m_lsttasks"></a>CMFCTasksPaneTaskGroup::m_lstTasks  
 包含內部工作的清單。  
  
```  
CObList m_lstTasks;  
```  
  
### <a name="remarks"></a>備註  
 若要填滿此清單，請呼叫[CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask)。  
  
##  <a name="m_rect"></a>CMFCTasksPaneTaskGroup::m_rect  
 指定在群組標題的周框矩形。  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>備註  
 架構會自動計算此值。  
  
##  <a name="m_rectgroup"></a>CMFCTasksPaneTaskGroup::m_rectGroup  
 指定群組的周框矩形。  
  
```  
CRect m_rectGroup;  
```  
  
### <a name="remarks"></a>備註  
 這個值會由架構自動計算的。  
  
##  <a name="m_strname"></a>CMFCTasksPaneTaskGroup::m_strName  
 指定群組的名稱。  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>備註  
 如果這個值是空的不會顯示在群組標題，並不能摺疊群組。  
  
##  <a name="setaccdata"></a>CMFCTasksPaneTaskGroup::SetACCData  
 判斷目前的工作群組的存取範圍資料。  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>參數  
 [in] `pParent`  
 表示目前的工作群組的父視窗。  
  
 [輸出] `data`  
 型別的物件`CAccessibilityData`會填入目前的工作群組的存取範圍資料。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`data`參數已成功地填入目前的工作群組的存取範圍資料，否則`FALSE`。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCTasksPane 類別](../../mfc/reference/cmfctaskspane-class.md)   
 [CMFCTasksPaneTask 類別](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)


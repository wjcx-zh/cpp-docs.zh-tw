---
title: "CMFCRibbonQuickAccessToolBarDefaultState 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState class
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
caps.latest.revision: 28
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
ms.openlocfilehash: 211e8d897de923e7f07df389b0e9e7218cf45872
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>CMFCRibbonQuickAccessToolBarDefaultState 類別
協助程式類別，可快速存取工具列所放置在功能區列上管理預設狀態 ( [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md))。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonQuickAccessToolBarDefaultState  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|建構 `CMFCRibbonQuickAccessToolbarDefaultState` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|快速存取工具列將命令新增到預設狀態。 工具列本身不會變更。|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|將一個快速存取工具列的內容複製到另一個。|  
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|快速存取工具列中移除所有的命令。 工具列本身不會變更。|  
  
## <a name="remarks"></a>備註  
 您建立應用程式中的快速存取工具列之後，我們建議您設定其預設狀態，藉由呼叫[CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)。 當使用者按一下還原這個預設狀態**重設**按鈕**自訂**應用程式頁面**選項**對話方塊。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)  
  
## <a name="example"></a>範例  
 下列範例示範如何建構的物件`CMFCRibbonQuickAccessToolbarDefaultState`類別，以及如何新增快速存取工具列命令的預設狀態。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&21;](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxribbonquickaccesstoolbar.h  
  
##  <a name="addcommand"></a>CMFCRibbonQuickAccessToolBarDefaultState::AddCommand  
 快速存取工具列將命令新增到預設狀態。  
  
```  
void AddCommand(
    UINT uiCmd,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>參數  
 `[in] uiCmd`  
 指定命令識別碼。  
  
 `[in] bIsVisible`  
 快速存取工具列中的預設狀態時，請設定命令的可見性。  
  
### <a name="remarks"></a>備註  
 將命令加入至 CMFCRibbonQuickAccessToolBarDefaultState 完成三個結果。 首先，每個加入的命令列在快速存取工具列右邊的下拉式清單中。 以這種方式，使用者輕鬆地新增或移除快速存取工具列命令。 第二，快速存取工具列會重設為顯示只有所列出的命令為可見的預設狀態中當使用者按一下**重設**按鈕**自訂**對話方塊。 第三，如果您不呼叫[CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands)，快速存取工具列使用可見的指令，從這份清單做為預設顯示命令第一次使用者執行您的應用程式。 新增您想要的所有命令之後，呼叫[CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate)快速存取工具列的功能區列的這個執行個體設定為預設狀態。  
  
##  <a name="copyfrom"></a>CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom  
 將一個快速存取工具列的內容複製到另一個。  
  
```  
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```  
  
### <a name="parameters"></a>參數  
 [in] `src`  
 來源的參考`CMFCRibbonQuickAccessToolBarDefaultState`從複製的物件。  
  
### <a name="remarks"></a>備註  
 這個方法會從來源複製每個命令`CMFCRibbonQuickAccessToolBarDefaultState`物件與這個物件使用[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)方法。  
  
##  <a name="cmfcribbonquickaccesstoolbardefaultstate"></a>CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState  
 建構的快速存取工具列預設狀態物件。  
  
```  
CMFCRibbonQuickAccessToolBarDefaultState();
```  
  
### <a name="remarks"></a>備註  
 根據預設，清單的命令的新執行個體[CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)包含是空的。  
  
##  <a name="removeall"></a>CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll  
 清除 快速存取工具列中的預設命令的清單。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>備註  
 此函式會移除這個執行個體的所有命令的先前呼叫[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)加入。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)


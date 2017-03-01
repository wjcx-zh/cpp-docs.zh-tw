---
title: "CCmdUI 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCmdUI
dev_langs:
- C++
helpviewer_keywords:
- user interfaces, updating
- states, updating user interface object
- updating user interfaces for commands
- commands [C++], updating UI
- CCmdUI class
- toolbars [C++], updating
- command user interface
- menus [C++], updating as context changes
- buttons [C++], updating as context changes
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
caps.latest.revision: 21
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
ms.openlocfilehash: beb84a0f0f96c7a8acb5c432c7402b3e62b94518
ms.lasthandoff: 02/24/2017

---
# <a name="ccmdui-class"></a>CCmdUI 類別
只有在使用`ON_UPDATE_COMMAND_UI`中的處理常式`CCmdTarget`-衍生的類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CCmdUI  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CCmdUI::ContinueRouting](#continuerouting)|會告知命令路由機制，繼續傳送處理常式的鏈結中向下目前的訊息。|  
|[CCmdUI::Enable](#enable)|啟用或停用此命令的使用者介面項目。|  
|[CCmdUI::SetCheck](#setcheck)|設定此命令的使用者介面項目核取狀態。|  
|[CCmdUI::SetRadio](#setradio)|像`SetCheck`上選項群組的成員函式，但運作。|  
|[CCmdUI::SetText](#settext)|設定使用者介面項目，此命令的文字。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CCmdUI::m_nID](#m_nid)|使用者介面物件的識別碼。|  
|[CCmdUI::m_nIndex](#m_nindex)|使用者介面物件的索引。|  
|[CCmdUI::m_pMenu](#m_pmenu)|指向由功能表`CCmdUI`物件。|  
|[CCmdUI::m_pOther](#m_pother)|傳送通知的視窗物件的點。|  
|[CCmdUI::m_pSubMenu](#m_psubmenu)|指向由包含子功能表`CCmdUI`物件。|  
  
## <a name="remarks"></a>備註  
 `CCmdUI`沒有基底類別。  
  
 當應用程式的使用者提取下一個功能表、 每個功能表項目的需求，以得知是否應該顯示為已啟用或停用。 功能表命令的目標是提供這項資訊藉由實作`ON_UPDATE_COMMAND_UI`處理常式。 針對每個應用程式中的命令使用者介面物件，使用 [屬性] 視窗來建立每個處理常式的訊息對應項目，且函式原型。  
  
 當功能表撤下時，架構搜尋，並呼叫每一項`ON_UPDATE_COMMAND_UI`處理常式中，每個處理常式會呼叫`CCmdUI`成員函式，如**啟用**和**檢查**，架構然後適當地顯示每個功能表項目。  
  
 功能表項目可以使用工具列按鈕或其他命令的使用者介面物件而不需要變更中的程式碼取代`ON_UPDATE_COMMAND_UI`處理常式。  
  
 下表摘要說明影響`CCmdUI`的成員函式具有各種命令使用者介面項目上。  
  
|使用者介面項目|啟用|SetCheck|SetRadio|SetText|  
|--------------------------|------------|--------------|--------------|-------------|  
|Menu item|啟用或停用|檢查 （×） 或取消|使用點 （•） 檢查|設定項目文字|  
|工具列按鈕|啟用或停用|選取、 取消選取，或不明確|相同`SetCheck`|（不適用）|  
|狀態列窗格|會使文字可見或不可見|設定快顯或一般框線|相同`SetCheck`|設定文字窗格|  
|在一般的按鈕`CDialogBar`|啟用或停用|檢查或取消核取方塊|相同`SetCheck`|設定按鈕文字|  
|在正常的程式控制`CDialogBar`|啟用或停用|（不適用）|（不適用）|設定視窗的文字|  
  
 如需使用這個類別的詳細資訊，請參閱[如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CCmdUI`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-namecontinueroutinga--ccmduicontinuerouting"></a><a name="continuerouting"></a>CCmdUI::ContinueRouting  
 呼叫此成員函式，來告訴，繼續傳送目前的訊息處理常式的鏈結中向下的命令路由機制。  
  
```  
void ContinueRouting();
```  
  
### <a name="remarks"></a>備註  
 這是進階的成員函式，應該用於搭配`ON_COMMAND_EX`處理常式，傳回**FALSE**。 如需詳細資訊，請參閱[技術註 6](../../mfc/tn006-message-maps.md)。  
  
##  <a name="a-nameenablea--ccmduienable"></a><a name="enable"></a>CCmdUI::Enable  
 呼叫此成員函式可啟用或停用此命令的使用者介面項目。  
  
```  
virtual void Enable(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bOn`  
 **TRUE**啟用項目， **FALSE**停用它。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&46;](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView #&47;](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]  
  
##  <a name="a-namemnida--ccmduimnid"></a><a name="m_nid"></a>CCmdUI::m_nID  
 功能表項目、 工具列按鈕或由其他使用者介面物件的識別碼`CCmdUI`物件。  
  
```  
UINT m_nID;  
```  
  
##  <a name="a-namemnindexa--ccmduimnindex"></a><a name="m_nindex"></a>CCmdUI::m_nIndex  
 功能表項目、 工具列按鈕或由其他使用者介面物件的索引`CCmdUI`物件。  
  
```  
UINT m_nIndex;  
```  
  
##  <a name="a-namempmenua--ccmduimpmenu"></a><a name="m_pmenu"></a>CCmdUI::m_pMenu  
 指標 (的`CMenu`型別) 到由功能表`CCmdUI`物件。  
  
```  
CMenu* m_pMenu;  
```  
  
### <a name="remarks"></a>備註  
 **NULL**如果不是一個功能表項目。  
  
##  <a name="a-namempsubmenua--ccmduimpsubmenu"></a><a name="m_psubmenu"></a>CCmdUI::m_pSubMenu  
 指標 (的`CMenu`類型) 來代表包含子功能表`CCmdUI`物件。  
  
```  
CMenu* m_pSubMenu;  
```  
  
### <a name="remarks"></a>備註  
 **NULL**如果不是一個功能表項目。 如果子功能表快顯視窗，`m_nID`包含快顯功能表中的第一個項目識別碼。 如需詳細資訊，請參閱[技術提示 21](../../mfc/tn021-command-and-message-routing.md)。  
  
##  <a name="a-namempothera--ccmduimpother"></a><a name="m_pother"></a>CCmdUI::m_pOther  
 指標 (類型的`CWnd`) 的視窗物件，例如工具或狀態的列，會傳送通知。  
  
```  
CWnd* m_pOther;  
```  
  
### <a name="remarks"></a>備註  
 **NULL**項目是否為功能表或非`CWnd`物件。  
  
##  <a name="a-namesetchecka--ccmduisetcheck"></a><a name="setcheck"></a>CCmdUI::SetCheck  
 呼叫此成員函式，將此命令的使用者介面項目設定為適當的核取狀態。  
  
```  
virtual void SetCheck(int nCheck = 1);
```  
  
### <a name="parameters"></a>參數  
 `nCheck`  
 指定設定的核取狀態。 如果取消核取 0，;如果 1，會檢查。，若為 2，設定不定和。  
  
### <a name="remarks"></a>備註  
 此成員函式適用於功能表項目和工具列按鈕。 不定狀態只適用於工具列按鈕。  
  
##  <a name="a-namesetradioa--ccmduisetradio"></a><a name="setradio"></a>CCmdUI::SetRadio  
 呼叫此成員函式，將此命令的使用者介面項目設定為適當的核取狀態。  
  
```  
virtual void SetRadio(BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bOn`  
 **TRUE**啟用項目; 否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 此成員函式的運作方式相似`SetCheck`，只不過它作做為選項群組一部分的使用者介面項目。 取消核取 在群組中的其他項目不是自動除非項目本身維護選項群組的行為。  
  
##  <a name="a-namesettexta--ccmduisettext"></a><a name="settext"></a>CCmdUI::SetText  
 呼叫此成員函式設定的使用者介面項目，此命令的文字。  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 `lpszText`  
 文字字串的指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&48;](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDI](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)


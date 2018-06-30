---
title: DHTML 編輯命令對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d040f3cb4c9bf8e1f3afc0e8213cd4513fc8571
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123366"
---
# <a name="dhtml-editing-command-maps"></a>DHTML 編輯命令對應
下列巨集可以用來對應 DHTML 編輯命令中的[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-衍生的類別。 如需其用法的範例，請參閱[HTMLEdit 範例](../../visual-cpp-samples.md)。  
  
### <a name="dhtml-editing-command-map-macros"></a>DHTML 編輯命令對應巨集  
  
|||  
|-|-|  
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|宣告之 DHTML 編輯命令對應的類別。|  
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|啟動 DHTML 編輯命令對應類別內的定義。|  
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|標示 DHTML 編輯命令對應的結尾。|  
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|將命令 ID 對應至 HTML 編輯命令。|  
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|將命令 ID 對應至 HTML 編輯命令和訊息處理常式。|  
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|將命令 ID 對應至 HTML 編輯命令，使用者介面項目。|  
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|將命令 ID 對應至 HTML 編輯命令、訊息處理常式和使用者介面項目。|  
  
##  <a name="declare_dhtmlediting_cmdmap"></a>  DECLARE_DHTMLEDITING_CMDMAP  
 宣告之 DHTML 編輯命令對應的類別。  
  
```  
DECLARE_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>參數  
 *類別名稱*  
 類別的名稱。  
  
### <a name="remarks"></a>備註  
 這個巨集的定義中使用的[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-衍生的類別。  
  
 使用[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)實作對應。  
  
### <a name="example"></a>範例  
 請參閱[HTMLEdit 範例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxhtml.h  
  
##  <a name="begin_dhtmlediting_cmdmap"></a>  BEGIN_DHTMLEDITING_CMDMAP  
 啟動 DHTML 編輯命令對應類別內的定義。  
  
```  
BEGIN_DHTMLEDITING_CMDMAP(className)   
```  
  
### <a name="parameters"></a>參數  
 *類別名稱*  
 包含 DHTML 編輯命令對應的類別名稱。 這個類別應該直接或間接衍生自[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)並包含[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)其類別定義中的巨集。  
  
### <a name="remarks"></a>備註  
 DHTML 編輯命令對應加入至 HTML 編輯命令對應使用者介面的命令類別。  
  
 BEGIN_DHTMLEDITING_CMDMAP 巨集置於該類別的實作檔 (.cpp) 後面接著[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)巨集的類別是對應 （例如，從以 IDM_CUT ID_EDIT_CUT) 的命令。 使用[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)巨集，以標記事件對應的結尾。  
  
### <a name="requirements"></a>需求  
  **標頭**afxhtml.h  
  
##  <a name="end_dhtmlediting_cmdmap"></a>  END_DHTMLEDITING_CMDMAP  
 標示 DHTML 編輯命令對應的結尾。  
  
```  
END_DHTMLEDITING_CMDMAP()   
```  
  
### <a name="remarks"></a>備註  
 使用搭配[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)。  
  
### <a name="example"></a>範例  
 請參閱[HTMLEdit 範例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry"></a>  DHTMLEDITING_CMD_ENTRY  
 將命令 ID 對應至 HTML 編輯命令。  
  
```  
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)   
```  
  
### <a name="parameters"></a>參數  
 *cmdID*  
 命令 ID （例如 ID_EDIT_COPY)。  
  
 *dhtmlcmdID*  
 HTML 編輯命令*cmdID*對應 （例如 IDM_COPY)。  
  
### <a name="example"></a>範例  
 請參閱[HTMLEdit 範例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func"></a>  DHTMLEDITING_CMD_ENTRY_FUNC  
 將命令 ID 對應至 HTML 編輯命令和訊息處理常式。  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)   
```  
  
### <a name="parameters"></a>參數  
 *cmdID*  
 命令 ID （例如 ID_EDIT_COPY)。  
  
 *dhtmlcmdID*  
 HTML 編輯命令*cmdID*對應 （例如 IDM_COPY)。  
  
 *member_func_name*  
 命令對應的訊息處理函式名稱。  
  
### <a name="example"></a>範例  
 請參閱[HTMLEdit 範例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_type"></a>  DHTMLEDITING_CMD_ENTRY_TYPE  
 將命令 ID 對應至 HTML 編輯命令，使用者介面項目。  
  
```  
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)  
```  
  
### <a name="parameters"></a>參數  
 *cmdID*  
 命令 ID （例如 ID_EDIT_COPY)。  
  
 *dhtmlcmdID*  
 HTML 編輯命令*cmdID*對應 （例如 IDM_COPY)。  
  
 *elemType*  
 使用者介面項目類型。AFX_UI_ELEMTYPE_NORMAL、 AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO 的其中一個。  
  
### <a name="example"></a>範例  
 請參閱[HTMLEdit 範例](../../visual-cpp-samples.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxhtml.h  
  
##  <a name="dhtmlediting_cmd_entry_func_type"></a>  DHTMLEDITING_CMD_ENTRY_FUNC_TYPE  
 將命令 ID 對應至 HTML 編輯命令、訊息處理常式和使用者介面項目。  
  
```  
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)   
```  
  
### <a name="parameters"></a>參數  
 *cmdID*  
 命令 ID （例如 ID_EDIT_COPY)。  
  
 *dhtmlcmdID*  
 HTML 編輯命令*cmdID*對應 （例如 IDM_COPY)。  
  
 *member_func_name*  
 命令對應的訊息處理函式名稱。  
  
 *elemType*  
 使用者介面項目類型。AFX_UI_ELEMTYPE_NORMAL、 AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO 的其中一個。  
  
### <a name="example"></a>範例  
 請參閱[HTMLEdit 範例](../../visual-cpp-samples.md)。  

### <a name="requirements"></a>需求  
  **標頭**afxhtml.h  
    
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

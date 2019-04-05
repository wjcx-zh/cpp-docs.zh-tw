---
title: DHTML 編輯命令對應
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 7f420619983283c225ca8fca23c5ea349def1d1b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776150"
---
# <a name="dhtml-editing-command-maps"></a>DHTML 編輯命令對應

下列巨集可以用來對應 DHTML 編輯命令[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-衍生的類別。 如需其用法的範例，請參閱 < [HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="dhtml-editing-command-map-macros"></a>DHTML 編輯命令對應巨集

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|宣告 DHTML 編輯命令對應類別中。|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|啟動 DHTML 編輯命令對應類別內的定義。|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|標示 DHTML 編輯命令對應的結尾。|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|命令 ID 對應至 HTML 編輯命令。|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|命令 ID 對應至 HTML 編輯命令和訊息處理常式。|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|命令 ID 對應至 HTML 編輯命令和使用者介面項目。|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|將命令 ID 對應至 HTML 編輯命令、訊息處理常式和使用者介面項目。|

##  <a name="declare_dhtmlediting_cmdmap"></a>  DECLARE_DHTMLEDITING_CMDMAP

宣告 DHTML 編輯命令對應類別中。

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>參數

*className*<br/>
類別的名稱。

### <a name="remarks"></a>備註

這個巨集是用於定義[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)-衍生的類別。

使用[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)實作對應。

### <a name="example"></a>範例

請參閱[HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **標頭**afxhtml.h

##  <a name="begin_dhtmlediting_cmdmap"></a>  BEGIN_DHTMLEDITING_CMDMAP

啟動 DHTML 編輯命令對應類別內的定義。

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>參數

*className*<br/>
包含 DHTML 編輯命令對應的類別名稱。 這個類別應該直接或間接衍生自[CHtmlEditView](../../mfc/reference/chtmleditview-class.md) ，並包含[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)其類別定義中的巨集。

### <a name="remarks"></a>備註

DHTML 編輯命令對應加入您的類別，以 HTML 編輯命令對應使用者介面的命令。

將 BEGIN_DHTMLEDITING_CMDMAP 巨集放在類別的實作 (.cpp) 檔案，後面接著[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)巨集的類別是對應 （例如，從以 IDM_CUT ID_EDIT_CUT) 的命令。 使用[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)巨集來標示事件對應的結尾。

### <a name="requirements"></a>需求

  **標頭**afxhtml.h

##  <a name="end_dhtmlediting_cmdmap"></a>  END_DHTMLEDITING_CMDMAP

標示 DHTML 編輯命令對應的結尾。

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>備註

搭配使用[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)。

### <a name="example"></a>範例

請參閱[HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **標頭**afxhtml.h

##  <a name="dhtmlediting_cmd_entry"></a>  DHTMLEDITING_CMD_ENTRY

命令 ID 對應至 HTML 編輯命令。

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
（例如 ID_EDIT_COPY) 命令識別碼。

*dhtmlcmdID*<br/>
HTML 編輯命令*cmdID*對應 （例如 2&gt;idm_copy&lt;2)。

### <a name="example"></a>範例

請參閱[HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **標頭**afxhtml.h

##  <a name="dhtmlediting_cmd_entry_func"></a>  DHTMLEDITING_CMD_ENTRY_FUNC

命令 ID 對應至 HTML 編輯命令和訊息處理常式。

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
（例如 ID_EDIT_COPY) 命令識別碼。

*dhtmlcmdID*<br/>
HTML 編輯命令*cmdID*對應 （例如 2&gt;idm_copy&lt;2)。

*member_func_name*<br/>
命令對應的訊息處理函式名稱。

### <a name="example"></a>範例

請參閱[HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **標頭**afxhtml.h

##  <a name="dhtmlediting_cmd_entry_type"></a>  DHTMLEDITING_CMD_ENTRY_TYPE

命令 ID 對應至 HTML 編輯命令和使用者介面項目。

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
（例如 ID_EDIT_COPY) 命令識別碼。

*dhtmlcmdID*<br/>
HTML 編輯命令*cmdID*對應 （例如 2&gt;idm_copy&lt;2)。

*elemType*<br/>
使用者介面項目型別;其中一個 AFX_UI_ELEMTYPE_NORMAL、 AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO。

### <a name="example"></a>範例

請參閱[HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **標頭**afxhtml.h

##  <a name="dhtmlediting_cmd_entry_func_type"></a>  DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

將命令 ID 對應至 HTML 編輯命令、訊息處理常式和使用者介面項目。

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
（例如 ID_EDIT_COPY) 命令識別碼。

*dhtmlcmdID*<br/>
HTML 編輯命令*cmdID*對應 （例如 2&gt;idm_copy&lt;2)。

*member_func_name*<br/>
命令對應的訊息處理函式名稱。

*elemType*<br/>
使用者介面項目型別;其中一個 AFX_UI_ELEMTYPE_NORMAL、 AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO。

### <a name="example"></a>範例

請參閱[HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **標頭**afxhtml.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)

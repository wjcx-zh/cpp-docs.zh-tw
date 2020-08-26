---
title: DHTML 編輯命令對應
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: f4bbfb500e8de9594bbaa334b4e227caeaa845da
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837407"
---
# <a name="dhtml-editing-command-maps"></a>DHTML 編輯命令對應

下列宏可以用來對應 [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)衍生類別中的 DHTML 編輯命令。 如需其用法的範例，請參閱 [HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="dhtml-editing-command-map-macros"></a>DHTML 編輯命令對應宏

|名稱|描述|
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|宣告類別中的 DHTML 編輯命令對應。|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|在類別內啟動 DHTML 編輯命令對應的定義。|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|標記 DHTML 編輯命令對應的結尾。|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|將命令識別碼對應至 HTML 編輯命令。|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|將命令識別碼對應至 HTML 編輯命令和訊息處理常式。|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|將命令 ID 對應至 HTML 編輯命令和使用者介面元素。|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|將命令 ID 對應至 HTML 編輯命令、訊息處理常式和使用者介面項目。|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a> DECLARE_DHTMLEDITING_CMDMAP

宣告類別中的 DHTML 編輯命令對應。

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>參數

*className*<br/>
類別的名稱。

### <a name="remarks"></a>備註

這個宏是在 [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)衍生類別的定義中使用。

使用 [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap) 來執行對應。

### <a name="example"></a>範例

請參閱 [HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxhtml.h。h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a> BEGIN_DHTMLEDITING_CMDMAP

在類別內啟動 DHTML 編輯命令對應的定義。

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>參數

*className*<br/>
包含 DHTML 編輯命令對應之類別的名稱。 此類別應該直接或間接衍生自 [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) ，並在其類別定義中包含 [DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap) 宏。

### <a name="remarks"></a>備註

將 DHTML 編輯命令對應新增至您的類別，以將使用者介面命令對應至 HTML 編輯命令。

將 BEGIN_DHTMLEDITING_CMDMAP 宏放在類別的執行 ( .cpp) 檔中，然後針對類別要對應的命令 [DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry) 宏，例如，從 (到 ID_EDIT_CUT IDM_CUT。 使用 [END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap) 宏來標示事件對應的結尾。

### <a name="requirements"></a>規格需求

  **標頭** afxhtml.h。h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a> END_DHTMLEDITING_CMDMAP

標記 DHTML 編輯命令對應的結尾。

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>備註

搭配 [BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)使用。

### <a name="example"></a>範例

請參閱 [HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxhtml.h。h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a> DHTMLEDITING_CMD_ENTRY

將命令識別碼對應至 HTML 編輯命令。

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID (例如 ID_EDIT_COPY)。

*dhtmlcmdID*<br/>
*CmdID*對應 (的 HTML 編輯命令，例如 IDM_COPY) 。

### <a name="example"></a>範例

請參閱 [HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxhtml.h。h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a> DHTMLEDITING_CMD_ENTRY_FUNC

將命令識別碼對應至 HTML 編輯命令和訊息處理常式。

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID (例如 ID_EDIT_COPY)。

*dhtmlcmdID*<br/>
*CmdID*對應 (的 HTML 編輯命令，例如 IDM_COPY) 。

*member_func_name*<br/>
命令對應的訊息處理函式名稱。

### <a name="example"></a>範例

請參閱 [HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxhtml.h。h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a> DHTMLEDITING_CMD_ENTRY_TYPE

將命令 ID 對應至 HTML 編輯命令和使用者介面元素。

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID (例如 ID_EDIT_COPY)。

*dhtmlcmdID*<br/>
*CmdID*對應 (的 HTML 編輯命令，例如 IDM_COPY) 。

*elemType*<br/>
使用者介面項目類型；AFX_UI_ELEMTYPE_NORMAL、AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO 中的其中一項。

### <a name="example"></a>範例

請參閱 [HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxhtml.h。h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a> DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

將命令 ID 對應至 HTML 編輯命令、訊息處理常式和使用者介面項目。

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID (例如 ID_EDIT_COPY)。

*dhtmlcmdID*<br/>
*CmdID*對應 (的 HTML 編輯命令，例如 IDM_COPY) 。

*member_func_name*<br/>
命令對應的訊息處理函式名稱。

*elemType*<br/>
使用者介面項目類型；AFX_UI_ELEMTYPE_NORMAL、AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO 中的其中一項。

### <a name="example"></a>範例

請參閱 [HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxhtml.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)

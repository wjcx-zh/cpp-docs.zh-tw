---
title: DHTML 編輯命令對應
ms.date: 11/04/2016
ms.assetid: c1b49876-039e-4a26-bb24-ea98ccf254a1
ms.openlocfilehash: 62b388eb178be018655ea2b2be00d7321da50335
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365812"
---
# <a name="dhtml-editing-command-maps"></a>DHTML 編輯命令對應

以下宏可用於映射[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)派生類中的 DHTML 編輯命令。 關於它們的使用範例,請參考[HTMLEdit 範例](../../overview/visual-cpp-samples.md)。

### <a name="dhtml-editing-command-map-macros"></a>DHTML 編輯命令對應巨集

|||
|-|-|
|[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)|在類中聲明 DHTML 編輯命令映射。|
|[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)|在類中啟動 DHTML 編輯命令映射的定義。|
|[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)|標記 DHTML 編輯命令對應的末尾。|
|[DHTMLEDITING_CMD_ENTRY](#dhtmlediting_cmd_entry)|將指令 ID 映射到 HTML 編輯命令。|
|[DHTMLEDITING_CMD_ENTRY_FUNC](#dhtmlediting_cmd_entry_func)|將命令 ID 映射到 HTML 編輯命令和訊息處理程式。|
|[DHTMLEDITING_CMD_ENTRY_TYPE](#dhtmlediting_cmd_entry_type)|將指令 ID 映射到 HTML 編輯命令和使用者介面元素。|
|[DHTMLEDITING_CMD_ENTRY_FUNC_TYPE](#dhtmlediting_cmd_entry_func_type)|將命令 ID 對應至 HTML 編輯命令、訊息處理常式和使用者介面項目。|

## <a name="declare_dhtmlediting_cmdmap"></a><a name="declare_dhtmlediting_cmdmap"></a>DECLARE_DHTMLEDITING_CMDMAP

在類中聲明 DHTML 編輯命令映射。

```
DECLARE_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
類別的名稱。

### <a name="remarks"></a>備註

此宏將用於[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)派生類的定義。

使用[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)實現映射。

### <a name="example"></a>範例

請參考[HTML 編輯範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **頭**afxhtml.h

## <a name="begin_dhtmlediting_cmdmap"></a><a name="begin_dhtmlediting_cmdmap"></a>BEGIN_DHTMLEDITING_CMDMAP

在類中啟動 DHTML 編輯命令映射的定義。

```
BEGIN_DHTMLEDITING_CMDMAP(className)
```

### <a name="parameters"></a>參數

*類別名稱*<br/>
包含 DHTML 編輯命令對應的類別名稱。 此類應直接或間接地派生自[CHtmlEditView,](../../mfc/reference/chtmleditview-class.md)並在其類定義中包括[DECLARE_DHTMLEDITING_CMDMAP](#declare_dhtmlediting_cmdmap)宏。

### <a name="remarks"></a>備註

加入 DHTML 編輯命令映射,將使用者介面命令映射到 HTML 編輯命令。

將BEGIN_DHTMLEDITING_CMDMAP宏放在類的實現 (.cpp)[檔中,然後](#dhtmlediting_cmd_entry)DHTMLEDITING_CMD_ENTRY宏,用於類要映射的命令(例如,從ID_EDIT_CUT到IDM_CUT)。 使用[END_DHTMLEDITING_CMDMAP](#end_dhtmlediting_cmdmap)宏標記事件映射的結尾。

### <a name="requirements"></a>需求

  **頭**afxhtml.h

## <a name="end_dhtmlediting_cmdmap"></a><a name="end_dhtmlediting_cmdmap"></a>END_DHTMLEDITING_CMDMAP

標記 DHTML 編輯命令對應的末尾。

```
END_DHTMLEDITING_CMDMAP()
```

### <a name="remarks"></a>備註

與[BEGIN_DHTMLEDITING_CMDMAP](#begin_dhtmlediting_cmdmap)一起使用。

### <a name="example"></a>範例

請參考[HTML 編輯範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **頭**afxhtml.h

## <a name="dhtmlediting_cmd_entry"></a><a name="dhtmlediting_cmd_entry"></a>DHTMLEDITING_CMD_ENTRY

將指令 ID 映射到 HTML 編輯命令。

```
DHTMLEDITING_CMD_ENTRY(cmdID,  dhtmlcmdID)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID (例如 ID_EDIT_COPY)。

*dhtmlcmdID*<br/>
CMdID 對應到哪個*cmdID*的 HTML 編輯命令(如IDM_COPY)。

### <a name="example"></a>範例

請參考[HTML 編輯範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **頭**afxhtml.h

## <a name="dhtmlediting_cmd_entry_func"></a><a name="dhtmlediting_cmd_entry_func"></a>DHTMLEDITING_CMD_ENTRY_FUNC

將命令 ID 映射到 HTML 編輯命令和訊息處理程式。

```
DHTMLEDITING_CMD_ENTRY_FUNC(cmdID, dhtmlcmdID,  member_func_name)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID (例如 ID_EDIT_COPY)。

*dhtmlcmdID*<br/>
CMdID 對應到哪個*cmdID*的 HTML 編輯命令(如IDM_COPY)。

*member_func_name*<br/>
命令對應的訊息處理函式名稱。

### <a name="example"></a>範例

請參考[HTML 編輯範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **頭**afxhtml.h

## <a name="dhtmlediting_cmd_entry_type"></a><a name="dhtmlediting_cmd_entry_type"></a>DHTMLEDITING_CMD_ENTRY_TYPE

將指令 ID 映射到 HTML 編輯命令和使用者介面元素。

```
DHTMLEDITING_CMD_ENTRY_TYPE(cmdID  ,   dhtmlcmdID  ,    elemType)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID (例如 ID_EDIT_COPY)。

*dhtmlcmdID*<br/>
CMdID 對應到哪個*cmdID*的 HTML 編輯命令(如IDM_COPY)。

*埃萊姆類型*<br/>
使用者介面項目類型；AFX_UI_ELEMTYPE_NORMAL、AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO 中的其中一項。

### <a name="example"></a>範例

請參考[HTML 編輯範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **頭**afxhtml.h

## <a name="dhtmlediting_cmd_entry_func_type"></a><a name="dhtmlediting_cmd_entry_func_type"></a>DHTMLEDITING_CMD_ENTRY_FUNC_TYPE

將命令 ID 對應至 HTML 編輯命令、訊息處理常式和使用者介面項目。

```
DHTMLEDITING_CMD_ENTRY_FUNC_TYPE(cmdID, dhtmlcmdID, member_func_name,  elemType)
```

### <a name="parameters"></a>參數

*cmdID*<br/>
命令 ID (例如 ID_EDIT_COPY)。

*dhtmlcmdID*<br/>
CMdID 對應到哪個*cmdID*的 HTML 編輯命令(如IDM_COPY)。

*member_func_name*<br/>
命令對應的訊息處理函式名稱。

*埃萊姆類型*<br/>
使用者介面項目類型；AFX_UI_ELEMTYPE_NORMAL、AFX_UI_ELEMTYPE_CHECKBOX 或 AFX_UI_ELEMTYPE_RADIO 中的其中一項。

### <a name="example"></a>範例

請參考[HTML 編輯範例](../../overview/visual-cpp-samples.md)。

### <a name="requirements"></a>需求

  **頭**afxhtml.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)

---
title: CUserTool 類別
ms.date: 11/04/2016
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
ms.openlocfilehash: b73cb3d3c6e244a9aa41a91a3ee9ff1efa98d496
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502249"
---
# <a name="cusertool-class"></a>CUserTool 類別

使用者工具是執行外部應用程式的功能表項目。 [**自訂**] 對話方塊 ( [CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) 的 [**工具**] 索引標籤可讓使用者加入使用者工具, 以及指定每個使用者工具的名稱、命令、引數和初始目錄。

## <a name="syntax"></a>語法

```
class CUserTool : public CObject
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::DrawToolIcon](#drawtoolicon)|在指定的矩形中繪製使用者工具圖示。|
|[CUserTool::GetCommand](#getcommand)|傳回字串, 其中包含與使用者工具相關聯的命令文字。|
|[CUserTool::GetCommandId](#getcommandid)|傳回使用者工具功能表項目的命令識別碼。|
|[CUserTool::Invoke](#invoke)|執行與使用者工具相關聯的命令。|
|[CUserTool::Serialize](#serialize)|從封存中讀取或寫入此物件。 (覆寫 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。)|
|[CUserTool::SetCommand](#setcommand)|設定與使用者工具相關聯的命令。|
|[CUserTool::SetToolIcon](#settoolicon)|從與工具相關聯的應用程式載入使用者工具的圖示。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|載入使用者工具的預設圖示。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|使用者工具的命令列引數。|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|使用者工具的初始目錄。|
|[CUserTool::m_strLabel](#m_strlabel)|工具的功能表項目中顯示的工具名稱。|

## <a name="remarks"></a>備註

如需如何在您的應用程式中啟用使用者工具的詳細資訊, 請參閱[CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)。

## <a name="example"></a>範例

下列範例示範如何從`CUserToolsManager`物件建立工具、 `m_strLabel`設定成員變數, 以及設定使用者工具執行的應用程式。 此程式碼片段是[Visual Studio 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>需求

**標頭:** afxusertool。h

##  <a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard

如需詳細資訊, 請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="drawtoolicon"></a>CUserTool::D rawToolIcon

在指定矩形的中央繪製使用者工具圖示。

```
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

*rectImage*<br/>
在指定要顯示圖示之區域的座標。

##  <a name="getcommand"></a>CUserTool:: Iclientvirtualdevice

傳回字串, 其中包含與使用者工具相關聯的命令文字。

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>傳回值

`CString`物件的參考, 其中包含與使用者工具相關聯的命令文字。

##  <a name="getcommandid"></a>CUserTool::GetCommandId

傳回使用者工具的命令識別碼。

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>傳回值

此使用者工具的命令識別碼。

##  <a name="invoke"></a>CUserTool:: Invoke

執行與使用者工具相關聯的命令。

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>傳回值

如果命令執行成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

呼叫[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)來執行與使用者工具相關聯的命令。 如果命令是空的或[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)失敗, 則函式會失敗。

##  <a name="loaddefaulticon"></a>CUserTool::LoadDefaultIcon

載入使用者工具的預設圖示。

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>傳回值

載入圖示的控制碼 (HICON), 如果無法載入預設圖示, 則為 Null。

### <a name="remarks"></a>備註

當此架構無法從工具的可執行檔載入使用者定義工具的圖示時, 會呼叫這個方法。

覆寫此方法, 以提供您自己的預設工具圖示。

##  <a name="m_strarguments"></a>CUserTool::m_strArguments

使用者工具的命令列引數。

```
CString m_strArguments;
```

### <a name="remarks"></a>備註

當您呼叫[CUserTool:: Invoke](#invoke)時, 或當使用者按一下與此工具相關聯的命令時, 這個字串會傳遞至工具。

##  <a name="m_strinitialdirectory"></a>CUserTool::m_strInitialDirectory

指定使用者工具的初始目錄。

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>備註

當您呼叫[CUserTool:: Invoke](#invoke)時, 或當使用者按一下與此工具相關聯的命令時, 這個變數會指定工具在中執行的初始目錄。

##  <a name="m_strlabel"></a>CUserTool::m_strLabel

顯示在工具的功能表項目中的標籤。

```
CString m_strLabel;
```

##  <a name="serialize"></a>CUserTool:: 序列化

如需詳細資訊, 請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

[in] *ar*<br/>

### <a name="remarks"></a>備註

##  <a name="setcommand"></a>CUserTool::SetCommand

設定使用者工具執行的應用程式。

```
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>參數

*lpszCmd*<br/>
在指定要與使用者工具產生關聯的新應用程式。

### <a name="remarks"></a>備註

呼叫這個方法, 以設定使用者工具執行的新應用程式。 方法會終結舊的圖示, 並從指定的應用程式載入新的圖示。 如果它無法從應用程式載入圖示, 它會藉由呼叫[CUserTool:: LoadDefaultIcon](#loaddefaulticon)來載入使用者工具的預設圖示。

##  <a name="settoolicon"></a>CUserTool::SetToolIcon

從工具所使用的應用程式載入使用者工具的圖示。

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>傳回值

載入圖示的控制碼。

### <a name="remarks"></a>備註

呼叫這個方法, 載入要顯示在功能表項目上的圖示。 這個方法會搜尋工具所使用之可執行檔中的圖示。 如果沒有預設圖示, 則會改用[CUserTool:: LoadDefaultIcon](#loaddefaulticon)所提供的圖示。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)<br/>
[CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)

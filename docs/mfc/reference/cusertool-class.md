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
ms.openlocfilehash: 183b30961e4a7d3079fa0d035a4ddc38bc2eebac
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752026"
---
# <a name="cusertool-class"></a>CUserTool 類別

使用者工具是執行外部應用程式的功能表項目。 **「自訂」** 對話方塊的 **「工具**」選項卡 ( [CMFCToolBars 自訂對話方塊類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) 使用戶能夠添加使用者工具,並為每個使用者工具指定名稱、命令、參數和初始目錄。

## <a name="syntax"></a>語法

```
class CUserTool : public CObject
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[使用者工具::複製圖示到剪貼簿](#copyicontoclipboard)||
|[使用者工具::D原始工具圖示](#drawtoolicon)|在指定的矩形中繪製使用者工具圖示。|
|[使用者工具::抓取指令](#getcommand)|傳回包含與使用者工具關聯的命令文本的字串。|
|[使用者工具::取得指令 Id](#getcommandid)|返回使用者工具的功能表項的命令 ID。|
|[使用者工具::呼叫](#invoke)|執行與使用者工具關聯的命令。|
|[使用者工具::序列化](#serialize)|從封存中讀取或寫入此物件。 (覆寫 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。)|
|[使用者工具::設定命令](#setcommand)|設置與使用者工具關聯的命令。|
|[使用者工具::設定工具圖示](#settoolicon)|從與該工具關聯的應用程式載入使用者工具的圖示。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[使用者工具::載入預設圖示](#loaddefaulticon)|載入使用者工具的預設圖示。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[使用者工具::m_strArguments](#m_strarguments)|使用者工具的命令列參數。|
|[使用者工具::m_strInitialDirectory](#m_strinitialdirectory)|使用者工具的初始目錄。|
|[使用者工具::m_strLabel](#m_strlabel)|工具選單項目中顯示的工具名稱。|

## <a name="remarks"></a>備註

有關如何在應用程式中啟用使用者工具的詳細資訊,請參閱[CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)。

## <a name="example"></a>範例

下面的範例展示如何從`CUserToolsManager`物件創建工具、設置`m_strLabel`成員變數以及設置使用者工具運行的應用程式。 此代碼段是[可視化工作室演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>需求

**標題:** afxusertool.h

## <a name="cusertoolcopyicontoclipboard"></a><a name="copyicontoclipboard"></a>使用者工具::複製圖示到剪貼簿

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cusertooldrawtoolicon"></a><a name="drawtoolicon"></a>使用者工具::D原始工具圖示

在指定矩形的中心繪製使用者工具圖示。

```cpp
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*rectImage*<br/>
[在]指定要顯示圖示的區域的座標。

## <a name="cusertoolgetcommand"></a><a name="getcommand"></a>使用者工具::抓取指令

傳回包含與使用者工具關聯的命令文本的字串。

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>傳回值

對`CString`包含與使用者工具關聯的命令文本的物件的引用。

## <a name="cusertoolgetcommandid"></a><a name="getcommandid"></a>使用者工具::取得指令 Id

返回使用者工具的命令 ID。

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>傳回值

此使用者工具的命令 ID。

## <a name="cusertoolinvoke"></a><a name="invoke"></a>使用者工具::呼叫

執行與使用者工具關聯的命令。

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>傳回值

如果命令成功執行,則非零;否則 0。

### <a name="remarks"></a>備註

呼叫[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)以執行與使用者工具關聯的命令。 如果命令為空或[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew)失敗,則函數將失敗。

## <a name="cusertoolloaddefaulticon"></a><a name="loaddefaulticon"></a>使用者工具::載入預設圖示

載入使用者工具的預設圖示。

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>傳回值

如果無法載入預設圖示,則對載入的圖示 (HICON) 或 NULL 的句柄。

### <a name="remarks"></a>備註

當框架無法從該工具的可執行檔載入使用者定義工具的圖示時,該框架將呼叫此方法。

重寫此方法以提供您自己的預設工具圖示。

## <a name="cusertoolm_strarguments"></a><a name="m_strarguments"></a>使用者工具::m_strArguments

使用者工具的命令列參數。

```
CString m_strArguments;
```

### <a name="remarks"></a>備註

當您調用[CUserTool:::Invoke](#invoke)或當使用者單擊與此工具關聯的命令時,此字串將傳遞給該工具。

## <a name="cusertoolm_strinitialdirectory"></a><a name="m_strinitialdirectory"></a>使用者工具::m_strInitialDirectory

指定使用者工具的初始目錄。

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>備註

此變數指定工具在調用[CUserTool::Invoke](#invoke)或當用戶按一下與此工具關聯的命令時執行的初始目錄。

## <a name="cusertoolm_strlabel"></a><a name="m_strlabel"></a>使用者工具::m_strLabel

工具的功能表項中顯示的標籤。

```
CString m_strLabel;
```

## <a name="cusertoolserialize"></a><a name="serialize"></a>使用者工具::序列化

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>參數

[在]*阿爾*<br/>

### <a name="remarks"></a>備註

## <a name="cusertoolsetcommand"></a><a name="setcommand"></a>使用者工具::設定命令

設置使用者工具運行的應用程式。

```cpp
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>參數

*lpszCmd*<br/>
[在]指定要與使用者工具關聯的新應用程式。

### <a name="remarks"></a>備註

呼叫此方法以設置使用者工具運行的新應用程式。 該方法將銷毀舊圖示並載入給定應用程式的新圖示。 如果無法從應用程式載入圖示,則透過調用[CUserTool::LoadDefaultIcon](#loaddefaulticon)來載入使用者工具的預設圖示。

## <a name="cusertoolsettoolicon"></a><a name="settoolicon"></a>使用者工具::設定工具圖示

從該工具使用的應用程式載入使用者工具的圖示。

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>傳回值

載入圖示的句柄。

### <a name="remarks"></a>備註

調用此方法以載入要顯示在功能表項上的圖示。 此方法搜索該工具使用的可執行檔中的圖示。 如果沒有預設圖示,則使用[CUserTool::LoadDefaultIcon](#loaddefaulticon)提供的圖示。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)<br/>
[CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)

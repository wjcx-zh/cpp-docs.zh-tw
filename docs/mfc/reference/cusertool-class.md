---
title: CUserTool 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90972e39bbad812f820452816ff3df982174539f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202972"
---
# <a name="cusertool-class"></a>CUserTool 類別
使用者工具是執行外部應用程式的功能表項目。 **工具**索引標籤**自訂** 對話方塊 ( [CMFCToolBarsCustomizeDialog 類別](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) 可讓使用者加入使用者工具，並指定名稱、 命令、 引數，以及每個使用者工具的初始目錄。  
  
## <a name="syntax"></a>語法  
  
```  
class CUserTool : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||  
|[CUserTool::DrawToolIcon](#drawtoolicon)|指定的矩形中繪製使用者工具圖示。|  
|[CUserTool::GetCommand](#getcommand)|傳回字串，包含與使用者工具相關聯的命令文字。|  
|[CUserTool::GetCommandId](#getcommandid)|傳回的命令識別碼的使用者工具的功能表項目。|  
|[CUserTool::Invoke](#invoke)|執行與使用者工具相關聯的命令。|  
|[CUserTool::Serialize](#serialize)|從封存中讀取或寫入此物件。 (覆寫 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。)|  
|[CUserTool::SetCommand](#setcommand)|設定使用者工具相關聯的命令。|  
|[CUserTool::SetToolIcon](#settoolicon)|從工具相關聯的應用程式載入使用者工具圖示。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|載入使用者工具的預設圖示。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CUserTool::m_strArguments](#m_strarguments)|[使用者] 工具命令列引數。|  
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|使用者工具的初始目錄。|  
|[CUserTool::m_strLabel](#m_strlabel)|工具名稱，會顯示在工具功能表項目。|  
  
## <a name="remarks"></a>備註  
 如需如何啟用您的應用程式中的使用者工具的詳細資訊，請參閱[CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立提供的工具`CUserToolsManager`物件，設定`m_strLabel`成員變數，並設定使用者工具執行的應用程式。 此程式碼片段是一部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserTool](../../mfc/reference/cusertool-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxusertool.h  
  
##  <a name="copyicontoclipboard"></a>  CUserTool::CopyIconToClipboard  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
BOOL CopyIconToClipboard();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="drawtoolicon"></a>  CUserTool::DrawToolIcon  
 繪製指定矩形的中心的使用者工具圖示。  
  
```  
void DrawToolIcon(
    CDC* pDC,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>參數  
 [in]*pDC*  
 裝置內容的指標。  
  
 [in]*rectImage*  
 指定區域的座標，要顯示的圖示。  
  
##  <a name="getcommand"></a>  CUserTool::GetCommand  
 傳回字串，包含與使用者工具相關聯的命令文字。  
  
```  
const CString& GetCommand() const;  
```  
  
### <a name="return-value"></a>傳回值  
 參考`CString`物件，其中包含與使用者工具相關聯的命令文字。  
  
##  <a name="getcommandid"></a>  CUserTool::GetCommandId  
 傳回使用者工具的命令識別碼。  
  
```  
UINT GetCommandId() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此使用者工具的命令識別碼。  
  
##  <a name="invoke"></a>  CUserTool::Invoke  
 執行與使用者工具相關聯的命令。  
  
```  
virtual BOOL Invoke();
```  
  
### <a name="return-value"></a>傳回值  
 命令執行成功; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 呼叫[ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea)執行與使用者工具相關聯的命令。 函式失敗，如果是空的命令，或如果[ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea)失敗。  
  
##  <a name="loaddefaulticon"></a>  CUserTool::LoadDefaultIcon  
 載入使用者工具的預設圖示。  
  
```  
virtual HICON LoadDefaultIcon();
```  
  
### <a name="return-value"></a>傳回值  
 載入的圖示 (HICON) 或為 NULL，如果無法載入預設圖示控制代碼。  
  
### <a name="remarks"></a>備註  
 無法載入此工具可執行檔的使用者定義的工具的圖示時，架構會呼叫這個方法。  
  
 覆寫這個方法，以提供您自己的預設工具圖示。  
  
##  <a name="m_strarguments"></a>  CUserTool::m_strArguments  
 [使用者] 工具命令列引數。  
  
```  
CString m_strArguments;  
```  
  
### <a name="remarks"></a>備註  
 這個字串會傳遞至工具，當您呼叫[CUserTool::Invoke](#invoke)或當使用者按一下此工具相關聯的命令。  
  
##  <a name="m_strinitialdirectory"></a>  CUserTool::m_strInitialDirectory  
 指定使用者工具的初始目錄。  
  
```  
CString m_strInitialDirectory;  
```  
  
### <a name="remarks"></a>備註  
 此變數會指定當您呼叫中執行此工具的初始目錄[CUserTool::Invoke](#invoke)或當使用者按一下此工具相關聯的命令。  
  
##  <a name="m_strlabel"></a>  CUserTool::m_strLabel  
 此工具的功能表項目中顯示的標籤。  
  
```  
CString m_strLabel;  
```  
  
##  <a name="serialize"></a>  CUserTool::Serialize  
 如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 [in]*ar*  
  
### <a name="remarks"></a>備註  
  
##  <a name="setcommand"></a>  CUserTool::SetCommand  
 設定使用者工具執行的應用程式。  
  
```  
void SetCommand(LPCTSTR lpszCmd);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszCmd*  
 指定新的應用程式與使用者工具相關聯。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以設定使用者工具執行的新應用程式。 方法會終結舊的圖示，並從指定的應用程式載入新的圖示。 如果它無法載入圖示，從應用程式，它會藉由呼叫載入使用者工具的預設圖示[CUserTool::LoadDefaultIcon](#loaddefaulticon)。  
  
##  <a name="settoolicon"></a>  CUserTool::SetToolIcon  
 從使用此工具的應用程式中載入使用者工具圖示。  
  
```  
virtual HICON SetToolIcon();
```  
  
### <a name="return-value"></a>傳回值  
 載入圖示控制代碼。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來載入功能表項目要顯示的圖示。 這個方法會搜尋此工具會使用可執行檔中的圖示。 如果它沒有預設的圖示，所提供的圖示[CUserTool::LoadDefaultIcon](#loaddefaulticon)改為使用。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)   
 [CUserToolsManager 類別](../../mfc/reference/cusertoolsmanager-class.md)

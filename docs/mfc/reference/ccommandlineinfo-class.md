---
title: CCommandLineInfo 類別
ms.date: 11/04/2016
f1_keywords:
- CCommandLineInfo
- AFXWIN/CCommandLineInfo
- AFXWIN/CCommandLineInfo::CCommandLineInfo
- AFXWIN/CCommandLineInfo::ParseParam
- AFXWIN/CCommandLineInfo::m_bRunAutomated
- AFXWIN/CCommandLineInfo::m_bRunEmbedded
- AFXWIN/CCommandLineInfo::m_bShowSplash
- AFXWIN/CCommandLineInfo::m_nShellCommand
- AFXWIN/CCommandLineInfo::m_strDriverName
- AFXWIN/CCommandLineInfo::m_strFileName
- AFXWIN/CCommandLineInfo::m_strPortName
- AFXWIN/CCommandLineInfo::m_strPrinterName
- AFXWIN/CCommandLineInfo::m_strRestartIdentifier
helpviewer_keywords:
- CCommandLineInfo [MFC], CCommandLineInfo
- CCommandLineInfo [MFC], ParseParam
- CCommandLineInfo [MFC], m_bRunAutomated
- CCommandLineInfo [MFC], m_bRunEmbedded
- CCommandLineInfo [MFC], m_bShowSplash
- CCommandLineInfo [MFC], m_nShellCommand
- CCommandLineInfo [MFC], m_strDriverName
- CCommandLineInfo [MFC], m_strFileName
- CCommandLineInfo [MFC], m_strPortName
- CCommandLineInfo [MFC], m_strPrinterName
- CCommandLineInfo [MFC], m_strRestartIdentifier
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
ms.openlocfilehash: 0b4d5e5d253f2eb10388a69286d21e2190826eba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369452"
---
# <a name="ccommandlineinfo-class"></a>CCommandLineInfo 類別

協助應用程式啟動時剖析命令列。

## <a name="syntax"></a>語法

```
class CCommandLineInfo : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCommandLine資訊:CCommandLineinfo](#ccommandlineinfo)|構造預設`CCommandLineInfo`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|重寫此回調以分析單個參數。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCommandLine資訊:m_bRunAutomated](#m_brunautomated)|指示找到命令列`/Automation`選項。|
|[CCommandLine資訊::m_bRunEmbedded](#m_brunembedded)|指示找到命令列`/Embedding`選項。|
|[CCommandLine資訊:m_bShowSplash](#m_bshowsplash)|指示是否應顯示初始螢幕。|
|[CCommandLine資訊:m_nShellCommand](#m_nshellcommand)|指示要處理的 shell 命令。|
|[CCommandLine資訊::m_strDriverName](#m_strdrivername)|如果 shell 命令為「列印到」,則指示驅動程式名稱;否則為空。|
|[CCommandLine資訊::m_strFileName](#m_strfilename)|指示要打開或列印的檔名;如果 shell 命令為"新建" 或"DDE" 則為空。|
|[CCommandLine資訊::m_strPortName](#m_strportname)|如果 shell 命令是「列印到」,則指示埠名稱;否則為空。|
|[CCommandLine資訊:m_strPrinterName](#m_strprintername)|如果 shell 命令為「列印到」,則指示印表機名稱;否則為空。|
|[CCommandLine資訊:m_strRestartIdentifier](#m_strrestartidentifier)|指示重新啟動管理器重新啟動應用程式時重新啟動管理員的唯一重新啟動標識符。|

## <a name="remarks"></a>備註

MFC 應用程式通常會在其應用程式物件的[InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)函數中創建此類的本地實例。 然後,此物件將傳遞給[CWinApp::ParseCommandLine,該命令線](../../mfc/reference/cwinapp-class.md#parsecommandline)重複調用[ParseParam](#parseparam)來填充`CCommandLineInfo`該物件。 然後`CCommandLineInfo`,該物件將傳遞給[CWinApp::ProcessShellCommand,](../../mfc/reference/cwinapp-class.md#processshellcommand)以處理命令行參數和標誌。

可以使用此物件封裝以下命令列選項與參數:

|命令列引數|命令已執行|
|----------------------------|----------------------|
|*app*|新檔。|
|*套用*檔案名稱|打開檔。|
|*套用*`/p`檔案名稱|將檔案列印到預設印表機。|
|*應用程式*`/pt`檔案名稱印表機驅動程式連接埠|將檔案列印到指定的印表機。|
|*app* `/dde`|啟動並等待 DDE 命令。|
|*app* `/Automation`|啟動為 OLE 自動化伺服器。|
|*app* `/Embedding`|啟動以編輯嵌入的 OLE 專案。|
|*app* `/Register`<br /><br /> *app* `/Regserver`|通知應用程式執行任何註冊任務。|
|*app* `/Unregister`<br /><br /> *app* `/Unregserver`|通知應用程式執行任何取消註冊任務。|

派生新`CCommandLineInfo`類以處理其他標誌和參數值。 覆蓋[ParseParam](#parseparam)以處理新標誌。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="ccommandlineinfoccommandlineinfo"></a><a name="ccommandlineinfo"></a>CCommandLine資訊:CCommandLineinfo

此建構函數創建具有`CCommandLineInfo`預設值的物件。

```
CCommandLineInfo();
```

### <a name="remarks"></a>備註

預設值是顯示初始螢幕`m_bShowSplash=TRUE`( ), 並在「檔」`m_nShellCommand`選單 ( **#NewFile**) 上執行「 新建」 命令。

應用程式框架調用[ParseParam](#parseparam)來填充此物件的數據成員。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

## <a name="ccommandlineinfom_brunautomated"></a><a name="m_brunautomated"></a>CCommandLine資訊:m_bRunAutomated

指示在`/Automation`命令行上找到標誌。

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>備註

如果為 TRUE,則意味著啟動為 OLE 自動化伺服器。

## <a name="ccommandlineinfom_brunembedded"></a><a name="m_brunembedded"></a>CCommandLine資訊::m_bRunEmbedded

指示在`/Embedding`命令行上找到標誌。

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>備註

如果為 TRUE,則意味著啟動以編輯嵌入的 OLE 專案。

## <a name="ccommandlineinfom_bshowsplash"></a><a name="m_bshowsplash"></a>CCommandLine資訊:m_bShowSplash

指示應顯示初始螢幕。

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>備註

如果為 TRUE,則意味著此應用程式的初始螢幕應在啟動期間顯示。 如果[m_nShellCommand](#m_nshellcommand)`CCommandLineInfo::FileNew`等於 ,[則 ParseParam](#parseparam)的預設實現將此資料成員設定為 TRUE。

## <a name="ccommandlineinfom_nshellcommand"></a><a name="m_nshellcommand"></a>CCommandLine資訊:m_nShellCommand

指示應用程式此實例的 shell 命令。

```
m_nShellCommand;
```

### <a name="remarks"></a>備註

此數據成員的類型為以下枚舉類型,該類型在類中`CCommandLineInfo`定義。

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE,
    AppRegister,
    AppUnregister,
    RestartByRestartManager,
    FileNothing = -1
    };
```

有關這些值的簡要說明,請參閱以下清單。

- `CCommandLineInfo::FileNew`指示在命令行上未找到檔名。

- `CCommandLineInfo::FileOpen`指示在命令列上找到檔案名,並且在命令列上找不到以下標誌: `/p`, `/pt` `/dde`。

- `CCommandLineInfo::FilePrint`指示在`/p`命令行上找到標誌。

- `CCommandLineInfo::FilePrintTo`指示在`/pt`命令行上找到標誌。

- `CCommandLineInfo::FileDDE`指示在`/dde`命令行上找到標誌。

- `CCommandLineInfo::AppRegister`指示在`/Register`命令`/Regserver`列 上找到 或標誌,並要求應用程式註冊。

- `CCommandLineInfo::AppUnregister`指示已要求`/Unregister``/Unregserver`或應用程式取消註冊。

- `CCommandLineInfo::RestartByRestartManager`指示重新啟動管理器重新啟動應用程式。

- `CCommandLineInfo::FileNothing`在啟動時關閉新 MDI 子視窗的顯示。 根據設計,應用程式精靈生成的 MDI 應用程式在啟動時顯示一個新的子視窗。 要關閉此功能,應用程式在調用`CCommandLineInfo::FileNothing`[ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)時可以使用它作為 shell 命令。 `ProcessShellCommand`由所有`CWinApp`派`InitInstance( )`生類的調用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

## <a name="ccommandlineinfom_strdrivername"></a><a name="m_strdrivername"></a>CCommandLine資訊::m_strDriverName

將第三個非標誌參數的值存儲在命令行上。

```
CString m_strDriverName;
```

### <a name="remarks"></a>備註

此參數通常是列印到 shell 命令的印表機驅動程式的名稱。 僅當在命令列上找到標誌時[,ParseParam](#parseparam)`/pt`的預設實現才會設置此數據成員。

## <a name="ccommandlineinfom_strfilename"></a><a name="m_strfilename"></a>CCommandLine資訊::m_strFileName

將第一個非標誌參數的值存儲在命令行上。

```
CString m_strFileName;
```

### <a name="remarks"></a>備註

此參數通常是要打開的文件的名稱。

## <a name="ccommandlineinfom_strportname"></a><a name="m_strportname"></a>CCommandLine資訊::m_strPortName

將第四個非標誌參數的值存儲在命令行上。

```
CString m_strPortName;
```

### <a name="remarks"></a>備註

此參數通常是列印到 shell 命令的印表機埠的名稱。 僅當在命令列上找到標誌時[,ParseParam](#parseparam)`/pt`的預設實現才會設置此數據成員。

## <a name="ccommandlineinfom_strprintername"></a><a name="m_strprintername"></a>CCommandLine資訊:m_strPrinterName

將第二個非標誌參數的值存儲在命令行上。

```
CString m_strPrinterName;
```

### <a name="remarks"></a>備註

此參數通常是列印到 shell 命令的印表機名稱。 僅當在命令列上找到標誌時[,ParseParam](#parseparam)`/pt`的預設實現才會設置此數據成員。

## <a name="ccommandlineinfom_strrestartidentifier"></a><a name="m_strrestartidentifier"></a>CCommandLine資訊:m_strRestartIdentifier

命令列上的唯一重新啟動標識符。

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>備註

重新啟動標識符對於應用程式的每個實例都是唯一的。

如果重新啟動管理器退出應用程式並設定為重新啟動應用程式,重新啟動管理器將從命令列執行應用程式,並將重新啟動標識符作為可選參數。 當重新啟動管理器使用重新啟動標識符時,應用程式可以重新打開以前打開的文檔並恢復自動儲存的檔。

## <a name="ccommandlineinfoparseparam"></a><a name="parseparam"></a>CCommandLine資訊::P

框架呼叫此函數來分析/解釋命令列中的單個參數。 第二個版本與 Unicode 專案中的第一個版本不同。

```
virtual void ParseParam(
    const char* pszParam,
    BOOL bFlag,
    BOOL bLast);

virtual void ParseParam(
    const TCHAR* pszParam,
    BOOL bFlag,
    BOOL bLast);
```

### <a name="parameters"></a>參數

*pszParam*<br/>
參數或標誌。

*bFlag*<br/>
指示*pszParam*是參數還是標誌。

*爆炸*<br/>
指示這是命令行上的最後一個參數或標誌。

### <a name="remarks"></a>備註

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)`ParseParam`為 指令列中的每個參數或標誌呼叫一次,將參數傳遞給*pszParam*。 如果參數的第一個字元是''**-** 或'',**/** 則刪除它並將*bFlag*設置為 TRUE。 分析最終參數時 *,bLast*設置為 TRUE。

此函數的預設實現可識別以下`/p`標誌: `/pt` `/dde` `/Automation`、`/Embedding`、 、 和, 如下表所示:

|命令列引數|命令已執行|
|----------------------------|----------------------|
|*app*|新檔。|
|*套用*檔案名稱|打開檔。|
|*套用*`/p`檔案名稱|將檔案列印到預設印表機。|
|*應用程式*`/pt`檔案名稱印表機驅動程式連接埠|將檔案列印到指定的印表機。|
|*app* `/dde`|啟動並等待 DDE 命令。|
|*app* `/Automation`|啟動為 OLE 自動化伺服器。|
|*app* `/Embedding`|啟動以編輯嵌入的 OLE 專案。|
|*app* `/Register`<br /><br /> *app* `/Regserver`|通知應用程式執行任何註冊任務。|
|*app* `/Unregister`<br /><br /> *app* `/Unregserver`|通知應用程式執行任何取消註冊任務。|

此資訊存儲在[m_bRunAutomated、m_bRunEmbedded](#m_brunautomated)和[m_bRunEmbedded](#m_brunembedded)[m_nShellCommand](#m_nshellcommand)中。 標誌用前斜杠'**/** 或連字元'標記**-**。

預設實現第一個非旗標參數放入[m_strFileName](#m_strfilename)。 在`/pt`標誌的情況下,默認實現將第二個、第三個和第四個非標誌參數分別放入[m_strPrinterName、m_strDriverName](#m_strprintername)和[m_strDriverName](#m_strdrivername)[m_strPortName。](#m_strportname)

預設實現還僅在新文件的情況下[將m_bShowSplash](#m_bshowsplash)設定為 TRUE。 在新文件的情況下,使用者已執行涉及應用程式本身的操作。 在任何其他情況下,包括使用 shell 打開現有檔案,使用者操作將直接涉及該檔。 在以文件為中心的立場中,初始螢幕不需要宣佈應用程式啟動。

重寫派生類中的此函數以處理其他標誌和參數值。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::P](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::P羅塞斯舍爾命令](../../mfc/reference/cwinapp-class.md#processshellcommand)

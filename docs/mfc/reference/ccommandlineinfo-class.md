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
ms.openlocfilehash: 60c0ae66234d5fb3be61d9249cf61ee77dff41ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481467"
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
|[CCommandLineInfo::CCommandLineInfo](#ccommandlineinfo)|建構預設`CCommandLineInfo`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCommandLineInfo::ParseParam](#parseparam)|覆寫此剖析個別參數的回呼。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCommandLineInfo::m_bRunAutomated](#m_brunautomated)|表示命令列`/Automation`找不到選項。|
|[CCommandLineInfo::m_bRunEmbedded](#m_brunembedded)|表示命令列`/Embedding`找不到選項。|
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|指出是否應該顯示啟動顯示畫面。|
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|表示要處理的 shell 命令。|
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|表示驅動程式名稱如果 shell 命令會列印到;為空的。|
|[CCommandLineInfo::m_strFileName](#m_strfilename)|指出要開啟或列印; 的檔案名稱新增] 或 [DDE shell 命令是否空白。|
|[CCommandLineInfo::m_strPortName](#m_strportname)|指出的連接埠名稱如果 shell 命令會列印到;為空的。|
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|表示印表機名稱如果 shell 命令會列印到;為空的。|
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|如果重新啟動管理員重新啟動應用程式，請重新啟動管理員指出唯一的重新啟動識別項。|

## <a name="remarks"></a>備註

MFC 應用程式通常會建立這個類別中的本機執行個體[InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)其應用程式物件的函式。 這個物件接著傳遞給[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)，重複呼叫[ParseParam](#parseparam)填滿`CCommandLineInfo`物件。 `CCommandLineInfo`物件會傳遞至[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)來處理命令列引數和旗標。

您可以使用這個物件封裝的下列命令列選項和參數：

|命令列引數|執行命令|
|----------------------------|----------------------|
|*app*|新的檔案。|
|*應用程式*檔名|開啟檔案。|
|*應用程式*`/p`檔名|列印到預設印表機的檔案。|
|*應用程式* `/pt` filename 印表機驅動程式連接埠|指定的印表機來列印檔案。|
|*應用程式* `/dde`|啟動，並等候 DDE 命令。|
|*應用程式* `/Automation`|為 OLE automation 伺服器啟動。|
|*應用程式* `/Embedding`|啟動編輯內嵌的 OLE 項目。|
|*應用程式* `/Register`<br /><br /> *應用程式* `/Regserver`|會通知應用程式執行任何註冊的工作。|
|*應用程式* `/Unregister`<br /><br /> *應用程式* `/Unregserver`|會通知應用程式執行任何取消註冊的工作。|

衍生新類別從`CCommandLineInfo`來處理其他旗標和參數值。 覆寫[ParseParam](#parseparam)來處理新的旗標。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CCommandLineInfo`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="ccommandlineinfo"></a>  CCommandLineInfo::CCommandLineInfo

這個建構函式會建立`CCommandLineInfo`物件使用預設值。

```
CCommandLineInfo();
```

### <a name="remarks"></a>備註

預設值是要說明啟動顯示畫面 ( `m_bShowSplash=TRUE`)，並在 [檔案] 功能表上執行新的命令 ( `m_nShellCommand` **= NewFile**)。

這個應用程式架構會呼叫[ParseParam](#parseparam)來填滿這個物件的資料成員。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#54](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]

##  <a name="m_brunautomated"></a>  CCommandLineInfo::m_bRunAutomated

表示`/Automation`命令列上找不到旗標。

```
BOOL m_bRunAutomated;
```

### <a name="remarks"></a>備註

如果為 TRUE，這表示為 OLE automation 伺服器啟動。

##  <a name="m_brunembedded"></a>  CCommandLineInfo::m_bRunEmbedded

表示`/Embedding`命令列上找不到旗標。

```
BOOL m_bRunEmbedded;
```

### <a name="remarks"></a>備註

如果為 TRUE，這表示啟動編輯內嵌的 OLE 項目。

##  <a name="m_bshowsplash"></a>  CCommandLineInfo::m_bShowSplash

表示應該顯示啟動顯示畫面。

```
BOOL m_bShowSplash;
```

### <a name="remarks"></a>備註

如果為 TRUE，這表示應該在啟動時顯示此應用程式啟動顯示畫面。 預設實作[ParseParam](#parseparam)設定為 TRUE 的這個資料成員[m_nShellCommand](#m_nshellcommand)等於`CCommandLineInfo::FileNew`。

##  <a name="m_nshellcommand"></a>  CCommandLineInfo::m_nShellCommand

指出這個執行個體的應用程式的殼層命令。

```
m_nShellCommand;
```

### <a name="remarks"></a>備註

此資料成員的類型是下列的列舉的類型，其定義於`CCommandLineInfo`類別。

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

這些值的簡短描述，請參閱下列的清單。

- `CCommandLineInfo::FileNew` 指出在命令列上，找到任何檔案名稱。

- `CCommandLineInfo::FileOpen` 表示命令列上，找到的檔案名稱，而且，任何下列旗標上找不到命令列： `/p`， `/pt`， `/dde`。

- `CCommandLineInfo::FilePrint` 表示`/p`命令列上找不到旗標。

- `CCommandLineInfo::FilePrintTo` 表示`/pt`命令列上找不到旗標。

- `CCommandLineInfo::FileDDE` 表示`/dde`命令列上找不到旗標。

- `CCommandLineInfo::AppRegister` 指出`/Register`或`/Regserver`命令列上找不到旗標和應用程式已要求註冊。

- `CCommandLineInfo::AppUnregister` 指出`/Unregister`或`/Unregserver`應用程式已要求取消註冊。

- `CCommandLineInfo::RestartByRestartManager` 指出重新啟動管理員已重新啟動應用程式。

- `CCommandLineInfo::FileNothing` 關閉在啟動新的 MDI 子視窗的顯示。 根據設計，應用程式精靈產生的 MDI 應用程式會顯示在啟動新的子視窗。 若要關閉這項功能，可以使用應用程式`CCommandLineInfo::FileNothing`shell 命令呼叫時作為[會發生於 ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)。 `ProcessShellCommand` 會呼叫`InitInstance( )`所有`CWinApp`衍生的類別。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#55](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]

##  <a name="m_strdrivername"></a>  CCommandLineInfo::m_strDriverName

在命令列上，會儲存第三個非旗標參數的值。

```
CString m_strDriverName;
```

### <a name="remarks"></a>備註

此參數通常是印表機驅動程式的名稱列印至殼層命令。 預設實作[ParseParam](#parseparam)設定這個資料成員只有當`/pt`命令列上找不到旗標。

##  <a name="m_strfilename"></a>  CCommandLineInfo::m_strFileName

在命令列上，會儲存第一個非旗標參數的值。

```
CString m_strFileName;
```

### <a name="remarks"></a>備註

此參數通常是要開啟之檔案的名稱。

##  <a name="m_strportname"></a>  CCommandLineInfo::m_strPortName

在命令列上，會儲存第四個非旗標參數的值。

```
CString m_strPortName;
```

### <a name="remarks"></a>備註

此參數通常是列印至殼層命令的印表機連接埠的名稱。 預設實作[ParseParam](#parseparam)設定這個資料成員只有當`/pt`命令列上找不到旗標。

##  <a name="m_strprintername"></a>  CCommandLineInfo::m_strPrinterName

在命令列上，會儲存第二個非旗標參數的值。

```
CString m_strPrinterName;
```

### <a name="remarks"></a>備註

此參數通常是印表機的名稱列印至殼層命令。 預設實作[ParseParam](#parseparam)設定這個資料成員只有當`/pt`命令列上找不到旗標。

##  <a name="m_strrestartidentifier"></a>  CCommandLineInfo::m_strRestartIdentifier

唯一的重新啟動命令列上的識別項。

```
CString m_strRestartIdentifier;
```

### <a name="remarks"></a>備註

重新啟動識別碼是唯一的應用程式的每個執行個體。

如果重新啟動管理員會結束應用程式，而且已設定成將它重新啟動，則重新啟動管理員會執行重新啟動識別碼為命令列的應用程式作為選擇性參數。 當重新啟動管理員會使用重新啟動識別項時，應用程式可以重新開啟先前開啟的文件，並復原會檔案。

##  <a name="parseparam"></a>  CCommandLineInfo::ParseParam

架構會呼叫此函式來剖析/解譯個別的參數，從命令列。 第二個版本不同於第一個只在 Unicode 專案中。

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
參數的旗標。

*bFlag*<br/>
指出是否*pszParam*參數或是的旗標。

*我*<br/>
指出這是否為最後一個參數或命令列上的旗標。

### <a name="remarks"></a>備註

[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)呼叫`ParseParam`一次針對每個參數或命令列上的旗標，並傳遞的引數*pszParam*。 如果參數的第一個字元是 ' **-**' **/**'，則會移除它並*bFlag*設為 TRUE。 當剖析的最後一個參數*bLast*設為 TRUE。

此函式的預設實作會辨識下列旗標： `/p`， `/pt`， `/dde`， `/Automation`，和`/Embedding`下, 表所示：

|命令列引數|執行命令|
|----------------------------|----------------------|
|*app*|新的檔案。|
|*應用程式*檔名|開啟檔案。|
|*應用程式*`/p`檔名|列印到預設印表機的檔案。|
|*應用程式* `/pt` filename 印表機驅動程式連接埠|指定的印表機來列印檔案。|
|*應用程式* `/dde`|啟動，並等候 DDE 命令。|
|*應用程式* `/Automation`|為 OLE automation 伺服器啟動。|
|*應用程式* `/Embedding`|啟動編輯內嵌的 OLE 項目。|
|*應用程式* `/Register`<br /><br /> *應用程式* `/Regserver`|會通知應用程式執行任何註冊的工作。|
|*應用程式* `/Unregister`<br /><br /> *應用程式* `/Unregserver`|會通知應用程式執行任何取消註冊的工作。|

這項資訊會儲存在[m_bRunAutomated](#m_brunautomated)， [m_bRunEmbedded](#m_brunembedded)，並[m_nShellCommand](#m_nshellcommand)。 正斜線標記旗標的其中一個 ' **/**'或連字號' **-**'。

預設實作會將第一個非旗標參數插入[m_strFileName](#m_strfilename)。 若是`/pt`旗標的預設實作會將第二個，第三和第四個非旗標參數[m_strPrinterName](#m_strprintername)， [m_strDriverName](#m_strdrivername)，和[m_strPortName](#m_strportname)分別。

預設實作也會設定[m_bShowSplash](#m_bshowsplash)到只在新檔案的情況下，則為 TRUE。 新的檔案，在使用者採取動作牽涉到應用程式本身。 在任何其他案例，包括開啟現有的檔案使用的殼層中的使用者動作直接涉及檔案。 在 文件中心的觀點來看，啟動顯示畫面不會不需要宣布啟動應用程式。

在衍生類別處理其他旗標和參數值中的此函式會覆寫。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)<br/>
[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)


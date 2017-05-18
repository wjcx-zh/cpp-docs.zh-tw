---
title: "CCommandLineInfo 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CCommandLineInfo class
- command line, parsing
- parsing, command-line arguments
- argv argument
- startup code, parsing command-line arguments
- application flags [C++]
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e63f47a8df69b52a6a12688e84602981d20dae
ms.openlocfilehash: a5b104e4ad0a0b9ce1933e7d8057f4d0fae46b77
ms.contentlocale: zh-tw
ms.lasthandoff: 03/21/2017

---
# <a name="ccommandlineinfo-class"></a>CCommandLineInfo 類別
協助應用程式啟動時剖析命令列。  
  
## <a name="syntax"></a>語法  
  
```  
class CCommandLineInfo : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
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
|[CCommandLineInfo::m_bShowSplash](#m_bshowsplash)|指出是否應該顯示開頭顯示畫面。|  
|[CCommandLineInfo::m_nShellCommand](#m_nshellcommand)|表示要處理的 shell 命令。|  
|[CCommandLineInfo::m_strDriverName](#m_strdrivername)|指出驅動程式名稱如果 shell 命令是列印;否則為空的。|  
|[CCommandLineInfo::m_strFileName](#m_strfilename)|指出檔案名稱來開啟或列印。新增或 DDE shell 命令是否空白。|  
|[CCommandLineInfo::m_strPortName](#m_strportname)|指出的連接埠名稱 shell 命令為列印;否則為空的。|  
|[CCommandLineInfo::m_strPrinterName](#m_strprintername)|指出的印表機名稱是否 shell 命令列印;否則為空的。|  
|[CCommandLineInfo::m_strRestartIdentifier](#m_strrestartidentifier)|如果重新啟動管理員重新啟動應用程式重新啟動管理員指示重新啟動唯一識別項。|  
  
## <a name="remarks"></a>備註  
 MFC 應用程式通常會建立這個類別中的本機執行個體[InitInstance](../../mfc/reference/cwinapp-class.md#initinstance)其應用程式物件的函式。 將此物件傳遞至[CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)，重複呼叫[ParseParam](#parseparam)來填滿`CCommandLineInfo`物件。 `CCommandLineInfo`將物件傳遞至[CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)處理命令列引數和旗標。  
  
 您可以使用此物件來封裝的下列命令列選項和參數︰  
  
|命令列引數|執行命令|  
|----------------------------|----------------------|  
|*app*|新檔案。|  
|*應用程式*檔名|開啟檔案。|  
|*應用程式*`/p`檔名|列印到預設印表機的檔案。|  
|*應用程式* `/pt` filename 印表機驅動程式連接埠|指定的印表機來列印檔案。|  
|*app*`/dde`|啟動並等候 DDE 命令。|  
|*app*`/Automation`|啟動為 OLE automation 伺服器。|  
|*app*`/Embedding`|若要編輯內嵌的 OLE 項目啟動時。|  
|*app*`/Register`<br /><br /> *app*`/Regserver`|會通知應用程式執行任何註冊的工作。|  
|*app*`/Unregister`<br /><br /> *app*`/Unregserver`|會通知應用程式執行任何取消註冊的工作。|  
  
 衍生新類別從`CCommandLineInfo`來處理其他旗標和參數值。 覆寫[ParseParam](#parseparam)來處理新的旗標。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCommandLineInfo`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="ccommandlineinfo"></a>CCommandLineInfo::CCommandLineInfo  
 這個建構函式會建立`CCommandLineInfo`物件使用預設值。  
  
```  
CCommandLineInfo();
```  
  
### <a name="remarks"></a>備註  
 預設會顯示啟動顯示畫面 ( `m_bShowSplash=TRUE`)，並在 [檔案] 功能表上執行新的命令 ( `m_nShellCommand` **= NewFile**)。  
  
 這個應用程式架構會呼叫[ParseParam](#parseparam)來填滿此物件的資料成員。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&54;](../../mfc/codesnippet/cpp/ccommandlineinfo-class_1.cpp)]  
  
##  <a name="m_brunautomated"></a>CCommandLineInfo::m_bRunAutomated  
 表示`/Automation`命令列上找不到旗標。  
  
```  
BOOL m_bRunAutomated;  
```  
  
### <a name="remarks"></a>備註  
 如果`TRUE`，這表示為 OLE automation 伺服器啟動。  
  
##  <a name="m_brunembedded"></a>CCommandLineInfo::m_bRunEmbedded  
 表示`/Embedding`命令列上找不到旗標。  
  
```  
BOOL m_bRunEmbedded;  
```  
  
### <a name="remarks"></a>備註  
 如果`TRUE`，這表示啟動編輯內嵌的 OLE 項目。  
  
##  <a name="m_bshowsplash"></a>CCommandLineInfo::m_bShowSplash  
 表示應該顯示開頭顯示畫面。  
  
```  
BOOL m_bShowSplash;  
```  
  
### <a name="remarks"></a>備註  
 如果`TRUE`，這表示此應用程式應該顯示在啟動時的啟動顯示畫面。 預設實作[ParseParam](#parseparam)將此資料成員設定為`TRUE`如果[m_nShellCommand](#m_nshellcommand)等於`CCommandLineInfo::FileNew`。  
  
##  <a name="m_nshellcommand"></a>CCommandLineInfo::m_nShellCommand  
 指出此執行個體的應用程式 shell 命令。  
  
```  
m_nShellCommand;  
```  
  
### <a name="remarks"></a>備註  
 此資料成員的類型是下列的列舉的類型，其定義在`CCommandLineInfo`類別。  
  
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
  
- `CCommandLineInfo::FileNew`表示沒有任何檔案名稱已在命令列上找到。  
  
- `CCommandLineInfo::FileOpen`表示命令列上發現到的檔案名稱，而且，下列旗標找不到任何命令列上︰ `/p`， `/pt`， `/dde`。  
  
- `CCommandLineInfo::FilePrint`表示`/p`命令列上找不到旗標。  
  
- `CCommandLineInfo::FilePrintTo`表示`/pt`命令列上找不到旗標。  
  
- `CCommandLineInfo::FileDDE`表示`/dde`命令列上找不到旗標。  
  
- `CCommandLineInfo::AppRegister`表示`/Register`或`/Regserver`命令列上找不到旗標和應用程式要求註冊。  
  
- `CCommandLineInfo::AppUnregister`表示`/Unregister`或`/Unregserver`應用程式被要求取消註冊。  
  
- `CCommandLineInfo::RestartByRestartManager`表示重新啟動管理員已重新啟動應用程式。  
  
- `CCommandLineInfo::FileNothing`關閉新的 MDI 子視窗在啟動時顯示。 根據設計，應用程式精靈產生的 MDI 應用程式會顯示在啟動新的子視窗。 若要關閉這項功能，可供應用程式`CCommandLineInfo::FileNothing`與殼層命令呼叫時，如果[ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)。 `ProcessShellCommand`會呼叫`InitInstance( )`所有`CWinApp`衍生的類別。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&55;](../../mfc/codesnippet/cpp/ccommandlineinfo-class_2.cpp)]  
  
##  <a name="m_strdrivername"></a>CCommandLineInfo::m_strDriverName  
 第三個非旗標參數的值儲存在命令列上。  
  
```  
CString m_strDriverName;  
```  
  
### <a name="remarks"></a>備註  
 這個參數通常是列印至殼層命令的印表機驅動程式的名稱。 預設實作[ParseParam](#parseparam)設定此資料成員只有當`/pt`命令列上找不到旗標。  
  
##  <a name="m_strfilename"></a>CCommandLineInfo::m_strFileName  
 在命令列會儲存第一個非旗標參數的值。  
  
```  
CString m_strFileName;  
```  
  
### <a name="remarks"></a>備註  
 這個參數通常是檔案的要開啟名稱。  
  
##  <a name="m_strportname"></a>CCommandLineInfo::m_strPortName  
 第四個非旗標參數的值儲存在命令列上。  
  
```  
CString m_strPortName;  
```  
  
### <a name="remarks"></a>備註  
 這個參數通常是列印至殼層命令的印表機連接埠的名稱。 預設實作[ParseParam](#parseparam)設定此資料成員只有當`/pt`命令列上找不到旗標。  
  
##  <a name="m_strprintername"></a>CCommandLineInfo::m_strPrinterName  
 第二個非旗標參數的值儲存在命令列上。  
  
```  
CString m_strPrinterName;  
```  
  
### <a name="remarks"></a>備註  
 這個參數通常是列印至殼層命令印表機的名稱。 預設實作[ParseParam](#parseparam)設定此資料成員只有當`/pt`命令列上找不到旗標。  
  
##  <a name="m_strrestartidentifier"></a>CCommandLineInfo::m_strRestartIdentifier  
 在命令列上的識別項重新啟動的唯一性。  
  
```  
CString m_strRestartIdentifier;  
```  
  
### <a name="remarks"></a>備註  
 重新啟動識別項是唯一的應用程式的每個執行個體。  
  
 如果重新啟動管理員結束應用程式，並設定成重新啟動它，則重新啟動管理員會執行重新啟動識別項使用的命令列的應用程式做為選擇性參數。 當重新啟動管理員使用的重新啟動識別項時，應用程式可以重新開啟先前開啟的文件，並復原 autosaved 檔案。  
  
##  <a name="parseparam"></a>CCommandLineInfo::ParseParam  
 架構會呼叫此函式可剖析/解譯個別的參數，從命令列。 第二個版本不同於第一個只能在 Unicode 專案中。  
  
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
 `pszParam`  
 參數或旗標。  
  
 *bFlag*  
 指出是否`pszParam`參數或是的旗標。  
  
 `bLast`  
 指出這是最後一個參數或命令列上的旗標。  
  
### <a name="remarks"></a>備註  
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)呼叫`ParseParam`一次針對每個參數或在命令列上的旗標，將引數傳遞至`pszParam`。 如果參數的第一個字元是 ' **-**'或' **/**'，則它也會移除和*bFlag*設為`TRUE`。 最後一個參數在剖析時`bLast`設為`TRUE`。  
  
 此函式的預設實作會辨識下列旗標︰ `/p`， `/pt`， `/dde`， `/Automation`，和`/Embedding`，如下表所示︰  
  
|命令列引數|執行命令|  
|----------------------------|----------------------|  
|*app*|新檔案。|  
|*應用程式*檔名|開啟檔案。|  
|*應用程式*`/p`檔名|列印到預設印表機的檔案。|  
|*應用程式* `/pt` filename 印表機驅動程式連接埠|指定的印表機來列印檔案。|  
|*app*`/dde`|啟動並等候 DDE 命令。|  
|*app*`/Automation`|啟動為 OLE automation 伺服器。|  
|*app*`/Embedding`|若要編輯內嵌的 OLE 項目啟動時。|  
|*app*`/Register`<br /><br /> *app*`/Regserver`|會通知應用程式執行任何註冊的工作。|  
|*app*`/Unregister`<br /><br /> *app*`/Unregserver`|會通知應用程式執行任何取消註冊的工作。|  
  
 這項資訊會儲存在[m_bRunAutomated](#m_brunautomated)， [m_bRunEmbedded](#m_brunembedded)，和[m_nShellCommand](#m_nshellcommand)。 旗標標示是正斜線 ' **/**'或連字號' **-**'。  
  
 預設實作會將第一個非旗標參數插入[m_strFileName](#m_strfilename)。 如果是`/pt`旗標，預設實作會將第二、 第三和第四個非旗標參數[m_strPrinterName](#m_strprintername)， [m_strDriverName](#m_strdrivername)，和[m_strPortName](#m_strportname)分別。  
  
 預設實作也會設定[m_bShowSplash](#m_bshowsplash)至`TRUE`僅在使用新的檔案。 如果是新的檔案，使用者採取動作牽涉到應用程式本身。 在任何其他案例，包括開啟現有的檔案使用 shell 的使用者動作牽涉到直接檔案。 文件為中心的觀點來看，在啟動顯示畫面不會不需要宣布啟動應用程式。  
  
 覆寫這個函式在衍生類別中處理其他旗標和參數的值。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWinApp::ParseCommandLine](../../mfc/reference/cwinapp-class.md#parsecommandline)   
 [CWinApp::ProcessShellCommand](../../mfc/reference/cwinapp-class.md#processshellcommand)



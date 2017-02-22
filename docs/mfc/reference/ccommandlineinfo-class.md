---
title: "CCommandLineInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCommandLineInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "application flags [C++]"
  - "argv argument"
  - "CCommandLineInfo class"
  - "命令列, 剖析"
  - "剖析, 命令列引數"
  - "啟始程式碼, parsing command-line arguments"
ms.assetid: 3e313ddb-0a82-4991-87ac-a27feff4668c
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CCommandLineInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在剖析命令列的協助在應用程式啟動。  
  
## 語法  
  
```  
class CCommandLineInfo : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CCommandLineInfo::CCommandLineInfo](../Topic/CCommandLineInfo::CCommandLineInfo.md)|預設建構 `CCommandLineInfo` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CCommandLineInfo::ParseParam](../Topic/CCommandLineInfo::ParseParam.md)|覆寫這個回呼剖析個別參數。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CCommandLineInfo::m\_bRunAutomated](../Topic/CCommandLineInfo::m_bRunAutomated.md)|表示找到 **\/Automation** 命令列選項。|  
|[CCommandLineInfo::m\_bRunEmbedded](../Topic/CCommandLineInfo::m_bRunEmbedded.md)|表示找到 **\/Embedding** 命令列選項。|  
|[CCommandLineInfo::m\_bShowSplash](../Topic/CCommandLineInfo::m_bShowSplash.md)|指出啟動顯示畫面是否應該顯示。|  
|[CCommandLineInfo::m\_nShellCommand](../Topic/CCommandLineInfo::m_nShellCommand.md)|表示 Shell 命令處理。|  
|[CCommandLineInfo::m\_strDriverName](../Topic/CCommandLineInfo::m_strDriverName.md)|如果 Shell 命令是列印，指示驅動程式名稱;則為 null。|  
|[CCommandLineInfo::m\_strFileName](../Topic/CCommandLineInfo::m_strFileName.md)|指示要開啟或列印的檔案名稱;，如果 Shell 命令是新的或是 DDE，則會是空白的。|  
|[CCommandLineInfo::m\_strPortName](../Topic/CCommandLineInfo::m_strPortName.md)|如果 Shell 命令是列印，表示連接埠名稱;則為 null。|  
|[CCommandLineInfo::m\_strPrinterName](../Topic/CCommandLineInfo::m_strPrinterName.md)|如果 Shell 命令是列印，表示印表機名稱;則為 null。|  
|[CCommandLineInfo::m\_strRestartIdentifier](../Topic/CCommandLineInfo::m_strRestartIdentifier.md)|如果重新啟動管理員已重新啟動應用程式，指出重新啟動管理員的唯一的重新啟動的識別項。|  
  
## 備註  
 MFC 應用程式通常會建立這個類別的本機執行個體在自己的應用程式物件的 [InitInstance](../Topic/CWinApp::InitInstance.md) 函式的。  這個物件傳遞至 [CWinApp::ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)，重複呼叫 [ParseParam](../Topic/CCommandLineInfo::ParseParam.md) 填滿 `CCommandLineInfo` 物件。  `CCommandLineInfo` 物件傳遞至 [CWinApp::ProcessShellCommand](../Topic/CWinApp::ProcessShellCommand.md) 處理命令列引數和旗標。  
  
 您可以使用這個物件封裝下列命令列選項和參數:  
  
|命令列引數。|執行的命令。|  
|------------|------------|  
|*應用程式*|新的檔案。|  
|*應用程式* 檔案名稱|開啟檔案。|  
|*應用程式* **\/p** filename|對預設印表機的列印文件。|  
|*應用程式* **\/pt** 檔名印表機驅動程式通訊埠|對指定的印表機上列印文件。|  
|*應用程式* **\/dde**|啟動並等待 DDE 命令。|  
|*應用程式* **\/Automation**|啟動當做 OLE Automation 伺服程式。|  
|*應用程式* **\/Embedding**|啟動由編譯決策內嵌 OLE 項目。|  
|*應用程式* **\/Register**<br /><br /> *應用程式* **\/Regserver**|向應用程式註冊執行任何工作。|  
|*應用程式* **\/Unregister**<br /><br /> *應用程式* **\/Unregserver**|通知應用程式執行任何非登入工作。|  
  
 從 `CCommandLineInfo` 衍生新類別處理其他旗標和參數值。  覆寫處理新的旗標 [ParseParam](../Topic/CCommandLineInfo::ParseParam.md) 。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCommandLineInfo`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWinApp::ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)   
 [CWinApp::ProcessShellCommand](../Topic/CWinApp::ProcessShellCommand.md)
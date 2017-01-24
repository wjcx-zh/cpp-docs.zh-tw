---
title: "GetCodeForInitInstance | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetCodeForInitInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForInitInstance 方法"
ms.assetid: cfa4cb9f-d1cc-4be6-8db9-c253655b57e4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetCodeForInitInstance
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得 [InitInstance](../Topic/CWinApp::InitInstance.md) 的指定程式碼。  
  
## 語法  
  
```  
  
      function GetCodeForInitInstance(   
   nLineStart,   
   nLineEnd    
);  
```  
  
#### 參數  
 `nLineStart`  
 函式開頭之以零起始的行號。  
  
 `nLineEnd`  
 函式結尾之以零起始的行號。  
  
## 傳回值  
 包含初始化精靈執行個體程式碼的字串。  
  
## 備註  
 呼叫此成員函式以取得初始化精靈執行個體的正確程式碼。  行號如下所示：  
  
|行號|InitInstance 程式碼|  
|--------|----------------------|  
|0|`CWinApp::InitInstance();`|  
|1|`return TRUE;`|  
|2|`AfxOleInit();`|  
|3|`// Parse command line for standard shell commands, DDE, file open`|  
|4|`CCommandLineInfo cmdInfo;`|  
|5|`ParseCommandLine(cmdInfo);`|  
|6|`// App was launched with /Embedding or /Automation switch.`|  
|7|`// Run app as automation server.`|  
|8|`if (cmdInfo.m_bRunEmbedded &#124;&#124; cmdInfo.m_bRunAutomated)`|  
|9|`{`|  
|10|`\t// Register class factories via CoRegisterClassObject().`|  
|11|`\tif (FAILED(_AtlModule.RegisterClassObjects(CLSCTX_LOCAL_SERVER, REGCLS_MULTIPLEUSE)))`|  
|12|`\t\treturn FALSE;`|  
|13|`\t// Don't show the main window`|  
|14|`\treturn TRUE;`|  
|15|`}`|  
|16|`// App was launched with /Unregserver or /Unregister switch.`|  
|17|`if (cmdInfo.m_nShellCommand == CCommandLineInfo::AppUnregister)`|  
|18|`{`|  
|19|`\t_AtlModule.UpdateRegistryAppId(FALSE);`|  
|20|`\t_AtlModule.UnregisterServer(TRUE);`|  
|21|`\treturn FALSE;`|  
|22|`}`|  
|23|`// App was launched with /Register or /Regserver switch.`|  
|24|`if (cmdInfo.m_nShellCommand == CCommandLineInfo::AppRegister)`|  
|25|`{`|  
|26|`\t_AtlModule.UpdateRegistryAppId(TRUE);`|  
|27|`\t_AtlModule.RegisterServer(TRUE);`|  
|28|`\treturn FALSE;`|  
|29|`}`|  
  
 `GetCodeForInitInstance` 會在傳回的每一行加上前置定位鍵 \(`\t`\) 和結尾的 "CR\-LF" \(歸位換行\) 字元組 \(`\r\n`\)。  
  
## 範例  
  
```  
// Get the lines numbered 0 through 2 above  
GetCodeForInitInstance(0, 2)  
  
// returns the following string  
// "\tCWinApp::InitInstance();\r\n\treturn TRUE;\r\n\tAfxOleInit();\r\n"  
  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [GetCodeForExitInstance](../ide/getcodeforexitinstance.md)
---
title: "GetCodeForExitInstance | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetCodeForExitInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForExitInstance 方法"
ms.assetid: 41fe3d79-a1f4-4bb5-b3f5-7859e255b4e7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetCodeForExitInstance
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得 [ExitInstance](../Topic/CWinApp::ExitInstance.md) 程式碼來結束精靈。  
  
## <a name="syntax"></a>語法  
  
```  
  
      function GetCodeForExitInstance(   
   nLineStart,   
   nLineEnd    
)   
```  
  
#### <a name="parameters"></a>參數  
 `nLineStart`  
 函式開頭的以零為起始的行號。  
  
 `nLineEnd`  
 函式結尾的以零為起始的行號。  
  
## <a name="return-value"></a>傳回值  
 字串，包含結束精靈執行個體的程式碼。  
  
## <a name="remarks"></a>備註  
 呼叫此成員函式，以取得適當的程式碼結束此精靈的執行個體︰  
  
|行號|ExitInstance 程式碼|  
|-----------------|-----------------------|  
|0|_AtlModule.RevokeClassObjects();|  
|1|傳回 CWinApp::ExitInstance();|  
  
 每一條線傳回， `GetCodeForExitInstance` 加入開頭的索引標籤 (`\t`) 和尾端的"CR-LF 」 （歸位字元-換行字元） 字元配對 (`\r\n`)。  
  
## <a name="example"></a>範例  
  
```  
if (!oExitInstance)  
   {  
      oExitInstance = oCWinApp.AddFunction("ExitInstance",   
      vsCMFunctionFunction, "BOOL", vsCMAddPositionEnd, vsCMAccessPublic,   
      strProjectCPP);  
      oExitInstance.BodyText = GetCodeForExitInstance(0, 1);  
   }  
// returns the following string  
// "\t_AtlModule.RevokeClassObjects();\r\n  
// \treturn CWinApp::ExitInstance();\r\n"  
else  
   {  
   oExitInstance.StartPointOf(vsCMPartBody,   
   vsCMWhereDefinition).CreateEditPoint().Insert(GetCodeForExitInstance(0,   
   0));  
// returns the following string  
// "\t_AtlModule.RevokeClassObjects();\r\n  
      oCM.Synchronize();  
   }  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [自訂 c + + 精靈使用 Common JScript 函式](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C + + 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [GetCodeForDllCanUnloadNow](../ide/getcodefordllcanunloadnow.md)   
 [GetCodeForInitInstance](../ide/getcodeforinitinstance.md)
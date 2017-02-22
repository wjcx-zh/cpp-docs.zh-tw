---
title: "GetCodeForDllRegisterServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetCodeForDllRegisterServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForDllRegisterServer 方法"
ms.assetid: 2fe733ad-3f1e-4020-9ce3-68956da7d41d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetCodeForDllRegisterServer
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得適當的程式碼中註冊伺服器。  
  
## <a name="syntax"></a>語法  
  
```  
  
      function GetCodeForDllRegisterServer(   
   nLineStart,   
   nLineEnd    
);  
```  
  
#### <a name="parameters"></a>參數  
 `nLineStart`  
 函式開頭的以零為起始的行號。  
  
 `nLineEnd`  
 函式結尾的以零為起始的行號。  
  
## <a name="return-value"></a>傳回值  
 字串，其中包含註冊伺服器的程式碼  
  
## <a name="remarks"></a>備註  
 呼叫此成員函式擷取註冊伺服器的正確程式碼︰  
  
|行號|程式碼|  
|-----------------|----------|  
|0|AFX_MANAGE_STATE(AfxGetStaticModuleState());|  
|1|_AtlModule.UpdateRegistryAppId(TRUE);|  
|2|HRESULT hRes = _AtlModule.RegisterServer(TRUE);|  
|3|如果 (hRes ！ = S_OK)|  
|4|\treturn hRes;|  
|5|if （！。COleObjectFactory::UpdateRegistryAll(TRUE))|  
|6|\treturn ResultFromScode(SELFREG_E_CLASS);|  
|7|傳回 S_OK。|  
  
 每一條線傳回， `GetCodeForDllRegisterServer` 加入開頭的索引標籤 (`\t`) 和尾端的"CR-LF 」 （歸位字元-換行字元） 字元配對 (`\r\n`)。  
  
## <a name="example"></a>範例  
  
```  
// Get the lines numbered 2 and 3 above  
GetCodeForDllRegisterServer(2, 3)  
  
// returns the following string  
// "\tHRESULT hRes = _AtlModule.RegisterServer(TRUE);\r\n\tif (hRes != S_OK)\r\n"  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [自訂 c + + 精靈使用 Common JScript 函式](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C + + 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [GetCodeForDllUnregisterServer](../ide/getcodefordllunregisterserver.md)
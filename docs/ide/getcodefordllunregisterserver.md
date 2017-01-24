---
title: "GetCodeForDllUnregisterServer | Microsoft Docs"
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
  - "GetCodeForDllUnregisterServer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForDllUnregisterServer 方法"
ms.assetid: 6b152943-8c30-49f4-a55c-d0cba8d27a17
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetCodeForDllUnregisterServer
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得適當的程式碼取消註冊伺服器。  
  
## <a name="syntax"></a>語法  
  
```  
  
      function GetCodeForDllUnregisterServer(   
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
 字串，包含取消註冊伺服器的程式碼。  
  
## <a name="remarks"></a>備註  
 呼叫此成員函式，以取得適當的程式碼取消註冊伺服器︰  
  
|行號|程式碼|  
|-----------------|----------|  
|0|AFX_MANAGE_STATE(AfxGetStaticModuleState());|  
|1|_AtlModule.UpdateRegistryAppId(FALSE);|  
|2|HRESULT hRes = _AtlModule.UnregisterServer(TRUE);|  
|3|如果 (hRes ！ = S_OK)|  
|4|\treturn hRes;|  
|5|if （！。COleObjectFactory::UpdateRegistryAll(FALSE))|  
|6|\treturn ResultFromScode(SELFREG_E_CLASS);|  
|7|傳回 S_OK。|  
  
 每一條線傳回， `GetCodeForDllUnregisterServer` 加入開頭的索引標籤 (`\t`) 和尾端的"CR-LF 」 （歸位字元-換行字元） 字元配對 (`\r\n`)。  
  
## <a name="example"></a>範例  
  
```  
// Get the lines numbered 2 and 3 above  
GetCodeForDllUnregisterServer(2, 3)  
  
// returns the following string  
// "\tHRESULT hRes = _AtlModule.UnregisterServer(TRUE);\r\n\tif (hRes != S_OK)\r\n"  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [自訂 c + + 精靈使用 Common JScript 函式](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C + + 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [GetCodeForDllRegisterServer](../ide/getcodefordllregisterserver.md)
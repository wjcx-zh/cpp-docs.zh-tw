---
title: "GetCodeForDllGetClassObject | Microsoft Docs"
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
  - "GetCodeForDllGetClassObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForDllGetClassObject 方法"
ms.assetid: 67b61b3b-9784-494f-ba01-17bffa9941ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetCodeForDllGetClassObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取 DLL 類別物件的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
  
      function GetCodeForDllGetClassObject(   
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
 字串，包含取得此類別物件的程式碼。  
  
## <a name="remarks"></a>備註  
 呼叫此成員函式擷取類別物件的程式碼。 呼叫此函式來建立單一字串串連您指定的陣列元素。  
  
 下表顯示用來取得程式碼類別物件的程式碼︰  
  
|行號|程式碼|  
|-----------------|----------|  
|0|AFX_MANAGE_STATE(AfxGetStaticModuleState());|  
|1|如果 (S_OK _AtlModule.GetClassObject rclsid、 riid (ppv） = =)|  
|2|\treturn S_OK;|  
|3|傳回 AfxDllGetClassObject rclsid、 riid (ppv）;|  
  
 每一條線傳回， `GetCodeForDllGetClassObject` 加入開頭的索引標籤 (`\t`) 和尾端的"CR-LF 」 （歸位字元-換行字元） 字元配對 (`\r\n`)。  
  
## <a name="example"></a>範例  
  
```  
// Get the lines numbered 1 and 2 above  
GetCodeForDllGetClassObject(1, 2)  
  
// returns the following string  
// "\tif (S_OK == _AtlModule.GetClassObject(rclsid, riid, ppv))\r\n\t\treturn S_OK;\r\n"  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [自訂 c + + 精靈使用 Common JScript 函式](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C + + 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)
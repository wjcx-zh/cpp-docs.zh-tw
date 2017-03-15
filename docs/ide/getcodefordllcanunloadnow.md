---
title: "GetCodeForDllCanUnloadNow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetCodeForDllCanUnloadNow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCodeForDllCanUnloadNow 方法"
ms.assetid: 24ee3ef7-45be-4778-99e8-6df493f0782b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetCodeForDllCanUnloadNow
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得適當的程式碼卸載 DLL。  
  
## <a name="syntax"></a>語法  
  
```  
  
      function GetCodeForDllCanUnloadNow(   
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
 字串，包含卸載 DLL 的程式碼。  
  
## <a name="remarks"></a>備註  
 呼叫此成員函式，以取得適當的程式碼卸載 DLL。 呼叫此函式來建立單一字串串連您指定的陣列元素。  
  
 下表顯示卸載 DLL 的程式碼。  
  
|行號|程式碼|  
|-----------------|----------|  
|0|AFX_MANAGE_STATE(AfxGetStaticModuleState());|  
|1|如果 (_AtlModule.GetLockCount() > 0)|  
|2|\treturn S_FALSE。|  
|3|傳回 S_OK。|  
  
 每一條線傳回， `GetCodeForDllCanUnloadNow` 加入開頭的索引標籤 (`\t`) 和尾端的"CR-LF 」 （歸位字元-換行字元） 字元配對 (`\r\n`)。  
  
## <a name="example"></a>範例  
  
```  
// Get the lines numbered 1 and 2 above  
GetCodeForDllCanUnloadNow(1, 2)  
  
// returns the following string  
// "\tif (_AtlModule.GetLockCount() > 0)\r\n\t\treturn S_FALSE;\r\n"  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [自訂 c + + 精靈使用 Common JScript 函式](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C + + 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [GetCodeForDllGetClassObject](../ide/getcodefordllgetclassobject.md)   
 [GetCodeForExitInstance](../ide/getcodeforexitinstance.md)
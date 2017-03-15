---
title: "GetProjectFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetProjectFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProjectFile 方法"
ms.assetid: e5fdc468-755a-4b4e-81bd-e63881531bed
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# GetProjectFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

傳回指定類型的檔名。  
  
## 語法  
  
```  
  
      function GetProjectFile(   
   oProj,   
   strType,   
   bFullPath,   
   bMFC    
);  
```  
  
#### 參數  
 oProj  
 選取的專案。  
  
 `strType`  
 要擷取的檔案類型，例如 STDAFX、RC、IDL、CPP、H、ODL 或 DEF。  
  
 *bFullPath*  
 表示是否傳回完整路徑名稱的旗標。  
  
 *bMFC*  
 表示專案是否為 MFC 架構的專案。  如果 `strType` 是 .cpp 或 .h，則會視其為 MFC 架構。  如果不是，則將假設是 ATL 架構的專案。  
  
## 傳回值  
 每個專案檔案類型的檔名。  
  
## 備註  
 呼叫此函式來取得在指定專案中指定類型的檔名。  
  
## 範例  
  
```  
// The selected MFC project's CPP file is retrieved and   
// assigned to strFileName.  
var strFileName = GetProjectFile(selProj, "CPP", false, true);  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [GetProjectPath](../ide/getprojectpath.md)   
 [GetUniqueFileName](../ide/getuniquefilename.md)
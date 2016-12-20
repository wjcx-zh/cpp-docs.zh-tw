---
title: "SetCommonPchSettings | Microsoft Docs"
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
  - "SetCommonPchSettings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetCommonPchSettings 方法"
ms.assetid: 12f5524b-f654-4222-b979-8ee0d9f58c14
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SetCommonPchSettings
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立專案的先行編譯標頭設定。  
  
## 語法  
  
```  
  
      function SetCommonPchSettings(   
   oProj    
);  
```  
  
#### 參數  
 `oProj`  
 選取的專案。  
  
## 備註  
 呼叫此函式以建立專案的先行編譯標頭設定。  
  
 這個函式會將 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A> 屬性設為：  
  
-   **pchUseUsingSpecific**：使用 [\/Yu \(使用先行編譯標頭檔\)](../build/reference/yu-use-precompiled-header-file.md) 編譯器設定。  
  
-   **pchCreateUsingSpecific**：使用 [\/Yc \(建立先行編譯標頭檔\)](../build/reference/yc-create-precompiled-header-file.md) 編譯器設定。  
  
## 範例  
  
```  
if ((strAppType == "LIB" || ((strAppType == "CONSOLE") &&   
   wizard.FindSymbol(SUPPORT_MFC"))) && !Pch)  
   {  
      AddFilesToProject(selProj, strProjectName, InfFile);  
      SetNoCommonPchSettings(selProj);  
   }  
else  
   {  
      AddFilesToProject(selProj, strProjectName, InfFile);  
      SetcommonPchSettings(selProj);  
   }  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [SetNoPchSettings](../ide/setnopchsettings.md)   
 [AddCommonConfig](../ide/addcommonconfig.md)
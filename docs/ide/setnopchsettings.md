---
title: "SetNoPchSettings | Microsoft Docs"
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
  - "SetNoPchSettings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetNoPchSettings 方法"
ms.assetid: 52373c98-ad5e-4e9b-9e0f-9f58ddb2a636
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SetNoPchSettings
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

於未使用先行編譯標頭設定時，先設定專案組態屬性。  
  
## 語法  
  
```  
  
      function SetNoPchSettings(   
   oProj    
);  
```  
  
#### 參數  
 `oProj`  
 選取的專案。  
  
## 備註  
 在專案未使用先行標頭設定時，呼叫這個函式來設定專案。  
  
## 範例  
 請參閱 [SetCommonPchSettings](../ide/setcommonpchsettings.md)。  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [SetCommonPchSettings](../ide/setcommonpchsettings.md)   
 [AddCommonConfig](../ide/addcommonconfig.md)
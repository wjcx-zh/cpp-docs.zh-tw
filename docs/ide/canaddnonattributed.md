---
title: "CanAddNonAttributed | Microsoft Docs"
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
  - "CanAddNonAttributed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanAddNonAttributed 方法"
ms.assetid: a2b0143e-f84b-40f3-8f51-23a492f651f8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CanAddNonAttributed
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 ATL 專案支援非屬性化物件。  
  
## 語法  
  
```  
  
function CanAddNonAttributed( );  
  
```  
  
## 傳回值  
 如果專案支援非屬性化和屬性化 ATL 物件則為 **true**；如果專案只支援屬性化專案則為 **false**。  
  
## 備註  
 呼叫此函式來表示專案是否同時支援非屬性化和屬性化物件。  
  
## 範例  
  
```  
// Check if attributed project using CanAddNonAttributed  
window.external.Load(document);  
if (IsAttributedProject(window.external))  
{  
   ATTRIBUTED.checked = true;  
   if (!CanAddNonAttributed())  
      ATTRIBUTED.disabled = true;  
}  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [Concepts](../windows/attributed-programming-concepts.md)   
 [CanAddClass](../ide/canaddclass.md)
---
title: "如何：將原生 DLL 加入至全域組件快取 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], native"
  - "GAC (全域組件快取), 載入原生 DLL"
  - "原生 DLL [C++]"
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：將原生 DLL 加入至全域組件快取
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以將原生 \(Native\) DLL \(而非 COM\) 放入全域組件快取。  
  
## 範例  
 **\/ASSEMBLYLINKRESOURCE** 讓您可以將原生 DLL 內嵌至組件中。  
  
 如需詳細資訊，請參閱[\/ASSEMBLYLINKRESOURCE \(連結到 .NET Framework 資源\)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)。  
  
```  
/ASSEMBLYLINKRESOURCE:MyComponent.dll  
```  
  
## 請參閱  
 [使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
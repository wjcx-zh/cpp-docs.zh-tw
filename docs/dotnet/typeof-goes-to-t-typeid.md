---
title: "typeof 變成 T::typeid | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__typeof 關鍵字"
  - "typeid 關鍵字 [C++]"
  - "typeid 運算子"
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# typeof 變成 T::typeid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Managed Extensions for C\+\+ 中使用的 `typeof` 運算子，已由 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中的 `typeid` 關鍵字所取代。  
  
 在 Managed Extensions 中傳遞 Managed 型別名稱時，`__typeof()` 運算子會傳回相關的 `Type*` 物件。  例如：  
  
```  
// Creates and initializes a new Array instance.  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 在新語法中，`__typeof` 已由 `typeid` 的其他格式所取代，指定 Managed 型別時，則會傳回 `Type^`。  
  
```  
// Creates and initializes a new Array instance.  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
## 請參閱  
 [一般的語言變更](../dotnet/general-language-changes-cpp-cli.md)   
 [typeid](../windows/typeid-cpp-component-extensions.md)
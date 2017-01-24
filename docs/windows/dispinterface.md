---
title: "dispinterface | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.dispinterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dispinterface 屬性"
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# dispinterface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將介面放入 .idl 檔案中作為分派介面。  
  
## 語法  
  
```  
  
[dispinterface]  
  
```  
  
## 備註  
 **dispinterface** C\+\+ 屬性在介面前面時，會將介面放在所產生 .idl 檔案的程式庫區塊內。  
  
 除非您指定基底類別，否則分派介面將衍生自 `IDispatch`。 您必須指定分派介面成員的 [id](../windows/id.md)。  
  
 MIDL 文件中 [dispinterface](http://msdn.microsoft.com/library/windows/desktop/aa366802) 的用法範例：  
  
```  
dispinterface helloPro   
   { interface hello; };   
```  
  
 不適用於 **dispinterface** 屬性。  
  
## 範例  
 如需如何使用 **dispinterface** 的範例，請參閱 [bindable](../windows/bindable.md) 範例。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|`interface`|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|**dual**、**object**、**oleautomation**、`local`、**ms\_union**|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Attributes by Usage](../windows/attributes-by-usage.md)   
 [uuid](../windows/uuid-cpp-attributes.md)   
 [dual](../windows/dual.md)   
 [custom](../windows/custom-cpp.md)   
 [object](../windows/object-cpp.md)   
 [\_\_interface](../cpp/interface.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)
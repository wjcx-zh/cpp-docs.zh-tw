---
title: "uuid (C++) | Microsoft Docs"
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
  - "uuid"
  - "uuid_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], uuid"
  - "uuid __declspec 關鍵字"
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# uuid (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 編譯器會將 GUID 附加至使用 `uuid` 屬性宣告或定義 \(僅限完整 COM 物件定義\) 的類別或結構。  
  
## 語法  
  
```  
  
__declspec( uuid("  
ComObjectGUID  
") ) declarator  
```  
  
## 備註  
 `uuid` 屬性可接受字串做為其引數。  這個字串會以標準登錄格式 \(無論是否包含 **{ }** 分隔符號\) 為 GUID 命名。  例如：  
  
```  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;  
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;  
```  
  
 這個屬性可以在重新宣告中套用。  這樣就可讓系統標頭提供介面的定義 \(例如 **IUnknown**\)，並且在某些其他標頭 \(例如 COMDEF.H\) 中重新宣告以提供 GUID。  
  
 套用 [\_\_uuidof](../cpp/uuidof-operator.md) 關鍵字就可以擷取附加至使用者定義類型的常數 GUID。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)
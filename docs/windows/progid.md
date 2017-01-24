---
title: "progid | Microsoft Docs"
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
  - "vc-attr.progid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "progid attribute"
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# progid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 COM 物件的 ProgID。  
  
## 語法  
  
```  
  
      [ progid(  
   name  
) ];  
```  
  
#### 參數  
 *name*  
 代表物件的程式識別碼。  
  
 Progid 呈現用來識別 COM\/ActiveX 物件的類別識別項 \(CLSID\) 的人們可讀取版本。  
  
## 備註  
 **Progid** C\+\+ 屬性可讓您指定 COM 物件的 ProgID。  與 ProgID 有表單 *name1*。*name2*.*version*.  如果您未指定*版本*與 ProgID，預設版本是 1。  如果您未指定 *name1*。 *name2*，預設名稱是  *classname*。 *classname*。  如果您未指定 **progid** 而您指定 **vi\_progid**，  *name1*。 *name2* 取自 **vi\_progid** 和 \(下一個序號\) 會加入版本。  
  
 如果使用的屬性區塊 **progid** 也不使用`uuid`，編譯器會檢查是否已登錄`uuid`存在於指定的 **progid**。  如果 **progid** 未指定，則版本 \(和 coclass 名稱，如果建立 coclass\) 將用來產生 **progid**。  
  
 **progid** 表示 **coclass** 屬性，亦即，如果您指定 **progid**，它是相同的動作，以指定  **coclass** 和 **progid** 屬性。  
  
 **Progid** 屬性會造成自動註冊指定的名稱下的類別。  將不會顯示產生的.idl 檔 **progid** 的值。  
  
 使用 ATL 專案中使用這個屬性時，便會變更屬性的行為。  除了上述的行為，請使用這個屬性指定此資訊用在 **GetProgID** 函式，由插入 **coclass** 屬性。  如需詳細資訊，請參閱 [coclass](../windows/coclass.md) 屬性。  
  
## 範例  
 請參閱範例的 [coclass](../windows/coclass.md) 的範例使用 **progid**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**，`struct`|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [ProgID Key](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)
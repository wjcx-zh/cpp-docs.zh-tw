---
title: "vi_progid | Microsoft Docs"
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
  - "vc-attr.vi_progid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vi_progid attribute"
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vi_progid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定版本無關的形式的 ProgID。  
  
## 語法  
  
```  
  
      [ vi_progid(  
   name  
) ];  
```  
  
#### 參數  
 *name*  
 版本無關的 ProgID，代表物件。  
  
 Progid 呈現用來識別 COM\/ActiveX 物件的類別識別項 \(CLSID\) 的人們可讀取版本。  
  
## 備註  
 **Vi\_progid** C\+\+ 屬性可讓您指定 COM 物件與版本無關的 ProgID。  與 ProgID 有表單 *name1*。*name2*.*version*.  與版本無關的 ProgID 沒有*版本*。  可以同時指定兩者 **progid** 和 **vi\_progid** 上 coclass 屬性。  如果您未指定 **vi\_progid**、 版本無關的 ProgID 是所指定的數值  [progid](../windows/progid.md) 屬性。  
  
 **vi\_progid** 表示 **coclass** 屬性，亦即，如果您指定 **vi\_progid**，它是相同的動作，以指定  **coclass** 和 **vi\_progid** 屬性。  
  
 **Vi\_progid** 屬性會造成自動註冊指定的名稱下的類別。  產生的.idl 檔將不會顯示的 ProgID 的值。  
  
 在 ATL 專案中，如果 [coclass](../windows/coclass.md) 屬性也，則會使用指定的 ProgID  **GetVersionIndependentProgID** 函式 \(藉由插入 **coclass** 屬性\)。  
  
## 範例  
 請參閱 [coclass](../windows/coclass.md) 的範例用法的範例 **vi\_progid**。  
  
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
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [ProgID Key](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)
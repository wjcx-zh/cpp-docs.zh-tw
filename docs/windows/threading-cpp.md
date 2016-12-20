---
title: "threading (C++) | Microsoft Docs"
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
  - "vc-attr.threading"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "threading attribute"
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# threading (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定 COM 物件的執行緒模型。  
  
## 語法  
  
```  
  
      [ threading(  
   model=enumeration  
) ]  
```  
  
#### 參數  
 ***模型*** \(可省略\)  
 下列的執行緒模型其中一項：  
  
-   **公寓** \(apartment 執行緒\)  
  
-   **中性** \(。NET 架構元件，無使用者介面\)  
  
-   **單一** \(簡單的執行緒\)  
  
-   **免費** \(釋放執行緒處理\)  
  
-   **兩者都** \(apartment 和無限制執行緒\)  
  
 預設值是**公寓**。  
  
## 備註  
 **執行緒** C\+\+ 屬性未出現在產生的.idl 檔，但使用於您的 COM 物件的實作。  
  
 在 ATL 專案中，如果 [coclass](../windows/coclass.md) 屬性也會出現，所指定的執行緒模型*模型* 當做樣板參數來傳遞  [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) 類別，可以插入 **coclass** 屬性。  
  
 **執行緒** 屬性也會避免存取  [event\_source](../windows/event-source.md)。  
  
## 範例  
 請參閱[授權](../windows/licensed.md) 的範例用法的範例 **執行緒**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**，`struct`|  
|**可重複**|否|  
|**必要的屬性**|**coclass**|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [COM Attributes](../windows/com-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [舊版程式碼的多執行緒支援 \(Visual C\+\+\)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [Neutral Apartments](http://msdn.microsoft.com/library/windows/desktop/ms681813)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)
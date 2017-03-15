---
title: "support_error_info | Microsoft Docs"
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
  - "vc-attr.support_error_info"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "support_error_info 屬性"
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# support_error_info
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

實作傳回詳細錯誤的支援。  
  
## 語法  
  
```  
  
[ support_error_info(  
   error_interface=  
uuid  
) ]  
  
```  
  
#### 參數  
 **error\_interface**  
 實作 **IErrorInfo** 之介面的識別碼。  
  
## 備註  
 **support\_error\_info** C\+\+ 屬性支援將目標物件所遇到的詳細內容錯誤傳回給用戶端。 針對支援錯誤的物件，物件必須實作 **IErrorInfo** 介面的方法。 如需詳細資訊，請參閱[支援 IDispatch 和 IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)。  
  
 此屬性會將 [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) 類別當成基底類別新增至目標物件。 這會導致 **ISupportErrorInfo** 的預設實作，而且可以在單一介面產生物件錯誤時使用。  
  
## 範例  
 下列程式碼會將 **ISupportErrorInfo** 介面的預設支援新增至 `CMyClass` 物件。  
  
```  
// cpp_attr_ref_support_error_info.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="mymod")];  
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]  
__interface IMyErrors  
{  
};  
  
[ coclass, support_error_info("IMyErrors"),  
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]  
class CMyClass  
{  
};  
```  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**Class \- 類別**|  
|**可重複**|是|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [COM Attributes](../windows/com-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)
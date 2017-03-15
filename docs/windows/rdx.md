---
title: "rdx | Microsoft Docs"
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
  - "vc-attr.rdx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rdx attribute"
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# rdx
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立登錄機碼或修改現有的登錄機碼。  
  
## 語法  
  
```  
  
      [ rdx(   
   key,   
   valuename=NULL,   
   regtype   
) ]  
```  
  
#### 參數  
 `key`  
 若要建立或開啟機碼名稱。  
  
 `valuename`\(選擇性\)  
 指定要設定的 \[值\] 欄位。  如果機碼中已經存在同名的值\] 欄位，會將它加入。  
  
 *regtype*  
 要加入的登錄機碼的型別。  可以是下列其中一項： **文字**，  **dword**， **二進位**，或`CString`。  
  
## 備註  
 **Rdx** C\+\+ 屬性會建立或修改現有的登錄機碼 COM 元件。  這個屬性會將 BEGIN\_RDX\_MAP 巨集加入至實作目標成員的物件。  `RegistryDataExchange`可能是 BEGIN\_RDX\_MAP 巨集\]，插入的函式可以用來登錄\] 和 \[資料成員之間傳輸資料  
  
 這個屬性可以用於搭配 [coclass](../windows/coclass.md)，  [progid](../windows/progid.md)，或  [vi\_progid](../windows/vi-progid.md) 屬性或表示其中一種其他屬性。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**或`struct`成員|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需有關屬性內容的詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 範例  
 下列程式碼加入至描述 CMyClass COM 元件的系統稱為 MyValue 的登錄機碼。  
  
```  
// cpp_attr_ref_rdx.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
  
[module (name="MyLib")];  
  
class CMyClass {  
public:  
   CMyClass() {  
      strcpy_s(m_sz, "SomeValue");  
   }  
  
   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]   
   char m_sz[256];  
};  
```  
  
## 請參閱  
 [COM Attributes](../windows/com-attributes.md)   
 [registration\_script](../windows/registration-script.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)
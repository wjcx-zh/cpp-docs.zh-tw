---
title: "default (C++) | Microsoft Docs"
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
  - "vc-attr.default"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "default 屬性"
  - "屬性 [C#], default 屬性"
  - "default, default 屬性"
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# default (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。  
  
## 語法  
  
```  
  
[ default(  
interface1  
,  
   interface2  
) ]  
  
```  
  
#### 參數  
 *interface1*  
 可讓指令碼環境使用的預設介面，會根據使用 **default** 屬性定義的類別來建立物件。  
  
 如果未指定預設介面，預設會使用第一個出現的非來源介面。  
  
 *interface2* \(選擇性\)  
 預設來源介面。 您也必須使用 [source](../windows/source-cpp.md) 屬性來指定此介面。  
  
 如果未指定預設來源介面，預設會使用第一個來源介面。  
  
## 備註  
 **default** C\+\+ 屬性具有與 [default](http://msdn.microsoft.com/library/windows/desktop/aa366787) MIDL 屬性相同的功能。**default** 屬性也可搭配 [case](../windows/case-cpp.md) 屬性使用。  
  
## 範例  
 下列程式碼示範如何在 coclass 的定義中使用 **default**，以將 **ICustomDispatch** 指定為預設可程式性介面︰  
  
```  
// cpp_attr_ref_default.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
};  
  
[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]   
__interface IDual {  
   HRESULT Dual([in] long l, [out, retval] long *pLong);  
};  
  
[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustomDispatch : public IDispatch {  
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);  
};  
  
[   coclass,  
   default(ICustomDispatch),   
   source(IDual),  
   uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")  
]  
class CClass : public ICustom, public IDual, public ICustomDispatch {  
   HRESULT Custom(long l, long *pLong) { return(S_OK); }  
   HRESULT Dual(long l, long *pLong) { return(S_OK); }  
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }  
};  
  
int main() {  
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch  
   CClass *pClass = new CClass;  
  
   long llong;  
  
   pClass->custom(1, &llong);  
   pClass->dual(1, &llong);  
   pClass->dispinterface(1, &llong);  
   pClass->dispatch(1, &llong);  
  
   delete pClass;  
#endif  
   return(0);  
}  
```  
  
 [source](../windows/source-cpp.md) 屬性也會示範如何使用 **default**。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、`struct`、資料成員|  
|**可重複**|否|  
|**必要屬性**|**coclass** \(套用至 **class** 或 `struct` 時\)|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [coclass](../windows/coclass.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)
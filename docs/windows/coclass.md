---
title: "coclass | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.coclass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "coclass attribute"
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# coclass
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立可實作 COM 介面的 COM 物件。  
  
## 語法  
  
```  
  
[coclass]  
  
```  
  
## 備註  
 **Coclass** C\+\+ 屬性將產生的.idl 檔內的 coclass 建構。  
  
 在定義到 coclass，您也可以指定 [uuid](../windows/uuid-cpp-attributes.md)， [版本](../windows/version-cpp.md)， [執行緒](../windows/threading-cpp.md)，  [vi\_progid](../windows/vi-progid.md)，以及  [progid](../windows/progid.md) 屬性。  如果未指定其中任何一個，它就會產生。  
  
 如果兩個標頭檔包含具有類別 **coclass** 屬性並不會指定一個 GUID，編譯器會針對這兩個類別中，將相同的 GUID 及 MIDL 錯誤將導致。  因此，您應該使用`uuid`屬性，當您使用 **coclass**。  
  
 **ATL 專案**  
  
 當這個屬性會在類別或結構定義之前在 ATL 專案中，它：  
  
-   插入程式碼或資料以支援自動註冊物件。  
  
-   插入程式碼或資料以支援 COM 類別工廠物件。  
  
-   插入程式碼或資料來實作 **IUnknown** ，並讓物件可建立 COM 物件。  
  
 明確地說，下列的基底類別會加入至目標物件：  
  
-   [CComCoClass 類別](../atl/reference/ccomcoclass-class.md)提供物件的預設類別工廠和彙總模型。  
  
-   [CComObjectRootEx 類別](../atl/reference/ccomobjectrootex-class.md) 使用指定的執行緒模型類別為基礎的範本 [執行緒](../windows/threading-cpp.md)屬性。  如果**執行緒**屬性沒有指定，則預設值的執行緒模型是公寓模型。  
  
-   [IProvideClassInfo2Impl](../atl/reference/iprovideclassinfo2impl-class.md) 加入[變成無法建立](../windows/noncreatable.md)屬性未指定目標物件。  
  
 最後，任何未定義使用內嵌的 IDL 的雙重介面就會以相對的取代 [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 類別。  如果雙重介面內嵌 IDL 中定義，則不會修改基底清單中的特定介面。  
  
 **Coclass** 屬性也會讓下列函式可透過插入程式碼，或在 \[大小寫的`GetObjectCLSID`，做為基底類別中的靜態方法`CComCoClass`：  
  
-   `UpdateRegistry`登錄類別工廠，目標類別。  
  
-   `GetObjectCLSID`這與註冊，也可用來取得目標類別的 CLSID。  
  
-   **GetObjectFriendlyName** 預設狀況下傳回格式字串"\<*目標類別名稱*\>  `Object`".  如果此函式已經存在，它不會加入。  要傳回更容易使用的名稱不是自動產生的目標類別中加入此函式。  
  
-   **GetProgID**，這與註冊，傳回與指定的字串  [progid](../windows/progid.md) 屬性。  
  
-   **GetVersionIndependentProgID** 具有相同的功能，為 **GetProgID**，它會傳回與指定的字串，但  [vi\_progid](../windows/vi-progid.md)。  
  
 下列變更發生關聯的 COM 對應時，會對目標類別：  
  
-   所有的目標類別衍生自的介面項目與所指定的所有項目加入 COM 對應 [COM 介面進入點](../mfc/com-interface-entry-points.md) 屬性，或所需 [的彙總](../windows/aggregates.md)屬性。  
  
-   [OBJECT\_ENTRY\_AUTO](../Topic/OBJECT_ENTRY_AUTO.md) 巨集就會插入的 COM 對應。  此巨集是類似於 [OBJECT\_ENTRY](http://msdn.microsoft.com/zh-tw/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd) 功能方面來看，但是不需要成為目標類別的 COM 對應的一部分。  
  
 在類別的.idl 檔中產生 coclass 名稱必須和類別相同的名稱。  範例中，並參考下列範例中，若要存取 coclass CMyClass，透過 MIDL 所產生標頭檔中，用戶端中的類別識別碼使用 CLSID\_CMyClass。  
  
## 範例  
 下列程式碼示範如何使用 **coclass** 屬性：  
  
```  
// cpp_attr_ref_coclass1.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[ object, uuid("00000000-0000-0000-0000-000000000001") ]  
__interface I {  
   HRESULT func();  
};  
  
[coclass, progid("MyCoClass.coclass.1"), vi_progid("MyCoClass.coclass"),   
appobject, uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")]  
class CMyClass : public I {};  
```  
  
 下列範例會示範如何覆寫預設實作會出現在所插入的程式碼的函式的 **coclass** 屬性。  請參閱 [\/fx 將加入](../build/reference/fx-merge-injected-code.md)如需檢視插入程式碼。  任何基底類別或介面，以供類別會在插入程式碼。此外，如果插入的程式碼中的預設包含類別，您明確指定該類別做為基底您 coclass 屬性提供者會使用您的程式碼中指定的表單。  
  
```  
// cpp_attr_ref_coclass2.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlwin.h>  
#include <atltypes.h>  
#include <atlctl.h>  
#include <atlhost.h>  
#include <atlplus.h>  
  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface bb {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class CMyClass : public bb {  
public:  
   // by adding the definition of UpdateRegistry to your code,   
   // the function will not be included in the injected code  
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {  
      // you can add to the default implementation  
      CRegistryVirtualMachine rvm;  
      HRESULT hr;  
      if (FAILED(hr = rvm.AddStandardReplacements()))  
         return hr;  
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());  
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),  
         GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);  
   }  
};  
```  
  
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
 [COM Attributes](../windows/com-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../windows/typedef-enum-union-and-struct-attributes.md)   
 [appobject](../windows/appobject.md)
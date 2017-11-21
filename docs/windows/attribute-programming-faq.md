---
title: "屬性程式設計常見問題集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- attributed programming
- attributes [C++], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c61ced7e0931f1dba46a7a6b760755f799d29b6b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="attribute-programming-faq"></a>屬性程式設計常見問題集
本主題將回答以下常見問題集：  
  
-   [HRESULT 是什麼？](#vcconattributeprogrammmingfaqanchor1)  
  
-   [何時具有指定屬性的參數名稱？](#vcconattributeprogrammmingfaqanchor2)  
  
-   [可以在屬性區塊中使用註解嗎？](#vcconattributeprogrammmingfaqanchor3)  
  
-   [屬性互動繼承的方式？](#vcconattributeprogrammmingfaqanchor4)  
  
-   [如何在未使用屬性的 ATL 專案中使用屬性？](#vcconattributeprogrammmingfaqanchor5)  
  
-   [如何使用屬性化專案中的.idl 檔案？](#vcconattributeprogrammmingfaqanchor6)  
  
-   [可以修改由屬性插入的程式碼嗎？](#vcconattributeprogrammmingfaqanchor7)  
  
-   [如何向前宣告屬性的介面？](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)  
  
-   [可以衍生自的類別，也會使用屬性的類別上使用屬性嗎？](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)  
  
##  <a name="vcconattributeprogrammmingfaqanchor1"></a>HRESULT 是什麼？  
 `HRESULT`是簡單的資料類型，通常用做為傳回值的屬性和 ATL 一般。 下表描述不同的值。 在標頭檔 winerror.h 包含多個值。  
  
|名稱|描述|值|  
|----------|-----------------|-----------|  
|S_OK|作業成功|0x00000000|  
|E_UNEXPECTED|未預期的失敗|0x8000FFFF|  
|E_NOTIMPL|未實作|0x80004001|  
|E_OUTOFMEMORY|無法配置所需的記憶體|0x8007000E|  
|E_INVALIDARG|一或多個引數不正確|0x80070057|  
|E_NOINTERFACE|不支援這類介面|0x80004002|  
|E_POINTER|無效的指標|0x80004003|  
|E_HANDLE|無效的控制代碼|0x80070006|  
|E_ABORT|已經中止操作|0x80004004|  
|E_FAIL|未指定的失敗|0x80004005|  
|E_ACCESSDENIED|一般拒絕存取錯誤|0x80070005|  
  
##  <a name="vcconattributeprogrammmingfaqanchor2"></a>何時具有指定屬性的參數名稱？  
 在大部分情況下，如果屬性有單一參數，該參數會命名為。 在您的程式碼插入屬性時，不需要此名稱。 例如，下列的使用方式[彙總](../windows/aggregatable.md)屬性：  
  
```  
[coclass, aggregatable(value=allowed)]  
class CMyClass  
{  
// The class declaration  
};  
```  
  
 是完全相同：  
  
```  
[coclass, aggregatable(allowed)]  
class CMyClass  
{  
// The class declaration  
};  
```  
  
 不過，下列屬性的單一、 未命名的參數：  
  
||||  
|-|-|-|  
|[call_as](../windows/call-as.md)|[case](../windows/case-cpp.md)|[cpp_quote](../windows/cpp-quote.md)|  
|[default](../windows/default-cpp.md)|[defaultvalue](../windows/defaultvalue.md)|[defaultvtable](../windows/defaultvtable.md)|  
|[emitidl](../windows/emitidl.md)|[entry](../windows/entry.md)|[first_is](../windows/first-is.md)|  
|[helpcontext](../windows/helpcontext.md)|[helpfile](../windows/helpfile.md)|[helpstring](../windows/helpstring.md)|  
|[helpstringcontext](../windows/helpstringcontext.md)|[helpstringdll](../windows/helpstringdll.md)|[id](../windows/id.md)|  
|[iid_is](../windows/iid-is.md)|[import](../windows/import.md)|[importlib](../windows/importlib.md)|  
|[include](../windows/include-cpp.md)|[includelib](../windows/includelib-cpp.md)|[last_is](../windows/last-is.md)|  
|[length_is](../windows/length-is.md)|[max_is](../windows/max-is.md)|[no_injected_text](../windows/no-injected-text.md)|  
|[pointer_default](../windows/pointer-default.md)|[pragma](../windows/pragma.md)|[restricted](../windows/restricted.md)|  
|[size_is](../windows/size-is.md)|[來源](../windows/source-cpp.md)|[switch_is](../windows/switch-is.md)|  
|[switch_type](../windows/switch-type.md)|[transmit_as](../windows/transmit-as.md)|[wire_marshal](../windows/wire-marshal.md)|  
  
##  <a name="vcconattributeprogrammmingfaqanchor3"></a>可以在屬性區塊中使用註解嗎？  
 您可以使用屬性區塊內的單一線條和多行註解。 不過，您無法使用保留的參數屬性括號內的註解的任一種樣式。  
  
 下列被可行的：  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1"), /* Multiple-line  
                                       comment */  
   threading("both") // Single-line comment  
]  
```  
  
 下列是不允許的：  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1" /* Multiple-line comment */ ),  
   threading("both" // Single-line comment)  
]  
```  
  
##  <a name="vcconattributeprogrammmingfaqanchor4"></a>屬性互動繼承的方式？  
 您可以從其他類別，可能會自行將歸類或不繼承屬性化和未歸屬的類別。 從屬性化的類別衍生的結果是相同的屬性提供者已轉換其程式碼之後，衍生自該類別。 屬性不會傳送給衍生透過 c + + 繼承的類別。 屬性提供者只會轉換來及其屬性的程式碼。  
  
##  <a name="vcconattributeprogrammmingfaqanchor5"></a>如何在未使用屬性的 ATL 專案中使用屬性？  
 您可能需要有.idl 檔案，未使用屬性的 ATL 專案，而且您可能要啟動 新增屬性化的物件。 在此情況下，使用 加入類別精靈提供的程式碼。  
  
##  <a name="vcconattributeprogrammmingfaqanchor6"></a>如何使用屬性化專案中的.idl 檔案？  
 您可能想要使用 ATL 屬性化專案中的.idl 檔案。 在此情況下，您會使用[importidl](../windows/importidl.md)屬性，請編譯.h 檔案的.idl 檔案 (請參閱[MIDL 屬性頁](../ide/midl-property-pages.md)專案的 [屬性頁] 對話方塊中)，然後在您的專案中包含的.h 檔案.  
  
##  <a name="vcconattributeprogrammmingfaqanchor7"></a>可以修改由屬性插入的程式碼嗎？  
 某些屬性會將程式碼插入您的專案。 您可以查看插入程式碼使用[/Fx](../build/reference/fx-merge-injected-code.md)編譯器選項。 它也可插入檔案中程式碼複製並貼到您的原始程式碼。 這可讓您修改屬性的行為。 不過，您可能必須修改您程式碼的其他部分。  
  
 下列範例會將插入的程式碼複製到原始程式碼檔案中的結果：  
  
```  
// attr_injected.cpp  
// compile with: comsupp.lib  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
  
[ module(name="MyLibrary") ];  
  
// ITestTest  
[   
   object,  
   uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"),  
   dual,  
   helpstring("ITestTest Interface"),  
   pointer_default(unique)  
]  
  
__interface ITestTest : IDispatch {  
   [id(1), helpstring("method DoTest")]   
   HRESULT DoTest([in] BSTR str);  
};  
  
// _ITestTestEvents  
[  
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"),  
   dispinterface,  
   helpstring("_ITestTestEvents Interface")  
]  
  
__interface _ITestTestEvents {  
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);  
};  
  
// CTestTest  
[  
   coclass,  
   threading(apartment),  
   vi_progid("TestATL1.TestTest"),  
   progid("TestATL1.TestTest.1"),  
   version(1.0),  
   uuid("D9632007-14FA-4679-9E1C-28C9A949E784"),  
   // this line would be commented out from original file  
   // event_source("com"),  
   // this line would be added to support injected code  
   source(_ITestTestEvents),  
   helpstring("TestTest Class")  
]  
  
class ATL_NO_VTABLE CTestTest : public ITestTest,  
// the following base classes support added injected code  
public IConnectionPointContainerImpl<CTestTest>,  
public IConnectionPointImpl<CTestTest, &__uuidof(::_ITestTestEvents), CComDynamicUnkArray>  
{  
public:  
   CTestTest() {  
   }  
   // this line would be commented out from original file  
   // __event __interface _ITestTestEvents;  
   DECLARE_PROTECT_FINAL_CONSTRUCT()  
   HRESULT FinalConstruct() {  
      return S_OK;  
   }  
  
void FinalRelease() {}  
  
public:  
   CComBSTR m_value;  
   STDMETHOD(DoTest)(BSTR str) {  
      VARIANT_BOOL bCancel = FALSE;  
      BeforeChange(str,&bCancel);  
      if (bCancel) {  
          return Error("Error : Someone don't want us to change the value");  
      }  
  
     m_value =str;  
     return S_OK;  
    }  
// the following was copied in from the injected code.  
HRESULT BeforeChange(::BSTR i1,::VARIANT_BOOL* i2) {  
   HRESULT hr = S_OK;  
   IConnectionPointImpl<CTestTest, &__uuidof(_ITestTestEvents), CComDynamicUnkArray>* p = this;  
   VARIANT rgvars[2];  
   Lock();  
   IUnknown** pp = p->m_vec.begin();  
   Unlock();  
   while (pp < p->m_vec.end()) {  
      if (*pp != NULL) {  
         IDispatch* pDispatch = (IDispatch*) *pp;  
         ::VariantInit(&rgvars[1]);  
         rgvars[1].vt = VT_BSTR;  
         V_BSTR(&rgvars[1])= (BSTR) i1;  
         ::VariantInit(&rgvars[0]);  
         rgvars[0].vt = (VT_BOOL | VT_BYREF);  
         V_BOOLREF(&rgvars[0])= (VARIANT_BOOL*) i2;  
         DISPPARAMS disp = { rgvars, NULL, 2, 0 };  
         VARIANT ret_val;  
         hr = __ComInvokeEventHandler(pDispatch, 1, 1, &disp, &ret_val);  
         if (FAILED(hr))  
            break;  
      }  
      pp++;  
   }  
   return hr;  
}  
  
BEGIN_CONNECTION_POINT_MAP(CTestTest)  
CONNECTION_POINT_ENTRY(__uuidof(::_ITestTestEvents))  
END_CONNECTION_POINT_MAP()  
// end added code section  
  
// _ITestCtrlEvents Methods  
public:  
};  
  
int main() {}  
```  
  
##  <a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a>如何向前宣告屬性的介面？  
 如果您要讓向前宣告的屬性化的介面，您必須套用相同的屬性套用至實際的介面宣告的向前宣告。 您還必須套用[匯出](../windows/export.md)您向前宣告此屬性。  
  
##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a>可以衍生自的類別，也會使用屬性的類別上使用屬性嗎？  
 否，不支援使用衍生自的類別，也會使用屬性的類別上的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../windows/attributed-programming-concepts.md)
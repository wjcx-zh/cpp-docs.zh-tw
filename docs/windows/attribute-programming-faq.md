---
title: "Attribute Programming FAQ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributed programming"
  - "attributes [C++], frequently asked questions"
  - "FAQs (frequently asked questions), attributed programming [C++]"
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Attribute Programming FAQ
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題回答下列常見的問題：  
  
-   [什麼是 HRESULT？](#vcconattributeprogrammmingfaqanchor1)  
  
-   [何時有指定屬性的參數名稱?](#vcconattributeprogrammmingfaqanchor2)  
  
-   [可以在屬性區塊中使用註解?](#vcconattributeprogrammmingfaqanchor3)  
  
-   [屬性互動繼承的方式？](#vcconattributeprogrammmingfaqanchor4)  
  
-   [我要如何在非屬性化的 ATL 專案中使用屬性呢？](#vcconattributeprogrammmingfaqanchor5)  
  
-   [我要如何使用屬性化專案中的一個.idl 檔案?](#vcconattributeprogrammmingfaqanchor6)  
  
-   [可以修改由屬性插入的程式碼嗎？](#vcconattributeprogrammmingfaqanchor7)  
  
-   [我如何向前宣告屬性的介面？](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)  
  
-   [可以使用屬性類別衍生自也要使用屬性的類別上嗎？](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)  
  
##  <a name="vcconattributeprogrammmingfaqanchor1"></a> 什麼是 HRESULT？  
 `HRESULT`是簡單的資料型別通常做為傳回值的屬性和 ATL 一般。  下表描述不同的值。  多個值都包含在標頭檔 winerror.h。  
  
|名稱|描述|值|  
|--------|--------|-------|  
|S\_OK|作業成功|0x00000000|  
|E\_UNEXPECTED|未預期的錯誤|0x8000FFFF|  
|E\_NOTIMPL|未實作|0x80004001|  
|E\_OUTOFMEMORY|無法配置所需的記憶體|0x8007000E|  
|E\_INVALIDARG|一或多個引數不正確|0x80070057|  
|E\_NOINTERFACE|這種不支援的介面|0x80004002|  
|E\_POINTER|無效的指標|0x80004003|  
|E\_HANDLE|無效的控制代碼|0x80070006|  
|E\_ABORT|操作中止|0x80004004|  
|E\_FAIL|未指定的失敗|0x80004005|  
|E\_ACCESSDENIED|一般性存取被拒的錯誤|「 0x80070005|  
  
##  <a name="vcconattributeprogrammmingfaqanchor2"></a> 何時有指定屬性的參數名稱?  
 在大部分的情況下，如果屬性有一個參數，該參數命名。  插入程式碼中的屬性時，就不需要此名稱。  例如，下列的使用方式[可集成](../windows/aggregatable.md)屬性：  
  
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
|[call\_as](../windows/call-as.md)|[case](../windows/case-cpp.md)|[cpp\_quote](../windows/cpp-quote.md)|  
|[default](../windows/default-cpp.md)|[預設值&#93;](../windows/defaultvalue.md)|[defaultvtable](../windows/defaultvtable.md)|  
|[emitidl](../windows/emitidl.md)|[項目](../windows/entry.md)|[first\_is](../windows/first-is.md)|  
|[helpcontext](../windows/helpcontext.md)|[說明檔案](../windows/helpfile.md)|[helpstring](../windows/helpstring.md)|  
|[helpstringcontext](../windows/helpstringcontext.md)|[helpstringdll](../windows/helpstringdll.md)|[id](../windows/id.md)|  
|[iid\_is](../windows/iid-is.md)|[import](../windows/import.md)|[importlib](../windows/importlib.md)|  
|[包含](../windows/include-cpp.md)|[includelib](../windows/includelib-cpp.md)|[last\_is](../windows/last-is.md)|  
|[length\_is](../windows/length-is.md)|[max\_is](../windows/max-is.md)|[no\_injected\_text](../windows/no-injected-text.md)|  
|[pointer\_default](../windows/pointer-default.md)|[pragma](../windows/pragma.md)|[restricted](../windows/restricted.md)|  
|[size\_is](../windows/size-is.md)|[source](../windows/source-cpp.md)|[switch\_is](../windows/switch-is.md)|  
|[switch\_type](../windows/switch-type.md)|[transmit\_as](../windows/transmit-as.md)|[wire\_marshal](../windows/wire-marshal.md)|  
  
##  <a name="vcconattributeprogrammmingfaqanchor3"></a> 可以在屬性區塊中使用註解?  
 您可以使用屬性區塊內的單行和多行註解。  不過，您無法使用保留給屬性的參數在括號內的註解的兩種樣式。  
  
 下列被允許的：  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1"), /* Multiple-line  
                                       comment */  
   threading("both") // Single-line comment  
]  
```  
  
 不允許下列:  
  
```  
[ coclass,  
   progid("MyClass.CMyClass.1" /* Multiple-line comment */ ),  
   threading("both" // Single-line comment)  
]  
```  
  
##  <a name="vcconattributeprogrammmingfaqanchor4"></a> 屬性互動繼承的方式？  
 您可以繼承其他類別，可能本身屬性或非屬性化和非使用屬性類別。  從屬性化的類別衍生的結果是相同屬性提供者已轉換的程式碼之後，衍生自該類別。  屬性不會傳輸到衍生透過 C\+\+ 繼承的類別。  屬性提供者只會轉換其屬性的 vicinity 中的程式碼。  
  
##  <a name="vcconattributeprogrammmingfaqanchor5"></a> 我要如何在非屬性化的 ATL 專案中使用屬性呢？  
 您可能必須非屬性化的 ATL 專案，都有一個.idl 檔案，請和您可能想要開始加入屬性化的物件。  如此一來，您也可使用 \[加入類別精靈提供的程式碼。  
  
##  <a name="vcconattributeprogrammmingfaqanchor6"></a> 我要如何使用屬性化專案中的一個.idl 檔案?  
 您可能想要使用屬性化的 ATL 專案的.idl 檔。  如此一來，您可以使用 [importidl](../windows/importidl.md) 屬性、 編譯.idl 檔案到.h 檔案 \(請參閱 [Midl 屬性](../ide/midl-property-pages.md)專案的 \[屬性頁\] 對話方塊中\)，然後將.h 檔案包含在專案中。  
  
##  <a name="vcconattributeprogrammmingfaqanchor7"></a> 可以修改由屬性插入的程式碼嗎？  
 有些屬性會將程式碼注入您的專案。  您可以看到插入的程式碼，藉由使用 [\/fx 將加入](../build/reference/fx-merge-injected-code.md)編譯器選項。  您也可插入的檔案從程式碼複製並貼到您的程式碼。  這可讓您修改屬性的行為。  不過，您可能必須修改您程式碼的其他部分。  
  
 下列範例會複製原始程式檔中插入程式碼的結果：  
  
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
  
##  <a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> 我如何向前宣告屬性的介面？  
 如果您要做為屬性化的介面的向前宣告，您必須在向前宣告，則套用到實際的介面宣告中套用相同的屬性。  您也必須套用[export](../windows/export.md)屬性設定為您的向前宣告。  
  
##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> 可以使用屬性類別衍生自也要使用屬性的類別上嗎？  
 否，不支援使用屬性，也會使用屬性的類別衍生的類別。  
  
## 請參閱  
 [Concepts](../windows/attributed-programming-concepts.md)
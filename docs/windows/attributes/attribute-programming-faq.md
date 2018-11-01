---
title: 屬性程式設計常見問題集
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: b273ad71c3c6eaed69fc715401219200f26f87eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434979"
---
# <a name="attribute-programming-faq"></a>屬性程式設計常見問題集

本主題將回答以下常見問題集：

- [HRESULT 是什麼？](#vcconattributeprogrammmingfaqanchor1)

- [何時已指定屬性的參數名稱？](#vcconattributeprogrammmingfaqanchor2)

- [可以在屬性區塊中使用註解嗎？](#vcconattributeprogrammmingfaqanchor3)

- [屬性互動繼承的方式？](#vcconattributeprogrammmingfaqanchor4)

- [如何使用屬性化 ATL 專案中？](#vcconattributeprogrammmingfaqanchor5)

- [如何使用屬性化專案中的.idl 檔案？](#vcconattributeprogrammmingfaqanchor6)

- [我是否可以修改屬性所插入的程式碼？](#vcconattributeprogrammmingfaqanchor7)

- [如何向前宣告屬性的介面？](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [可以使用屬性衍生自的類別，也會使用屬性的類別上嗎？](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

##  <a name="vcconattributeprogrammmingfaqanchor1"></a> HRESULT 是什麼？

HRESULT 為通常做為傳回值的屬性和 ATL 一般的簡單資料類型。 下表描述各種不同的值。 標頭檔 winerror.h 中包含多個值。

|名稱|描述|值|
|----------|-----------------|-----------|
|S_OK|作業成功|0x00000000|
|E_UNEXPECTED|未預期的失敗|0x8000FFFF|
|E_NOTIMPL|未實作|0x80004001|
|E_OUTOFMEMORY|無法配置所需的記憶體|0x8007000E|
|E_INVALIDARG|一或多個引數不正確|0x80070057|
|E_NOINTERFACE|不支援的這類介面|0x80004002|
|E_POINTER|無效的指標|0x80004003|
|E_HANDLE|無效的控制代碼|0x80070006|
|E_ABORT|作業已中止|0x80004004|
|E_FAIL|未指定的失敗|0x80004005|
|E_ACCESSDENIED|一般拒絕存取錯誤|0x80070005|

##  <a name="vcconattributeprogrammmingfaqanchor2"></a> 何時已指定屬性的參數名稱？

在大部分情況下，如果屬性具有單一參數，該參數會命名為。 在您的程式碼中插入屬性時，不需要此名稱。 例如，下列的使用方式[彙總](aggregatable.md)屬性：

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

是完全相同：

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

不過，下列屬性的單一、 未命名的參數：

||||
|-|-|-|
|[call_as](call-as.md)|[case](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[default](default-cpp.md)|[defaultvalue](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[entry](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[helpfile](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[id](id.md)|
|[iid_is](iid-is.md)|[import](import.md)|[importlib](importlib.md)|
|[include](include-cpp.md)|[includelib](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[restricted](restricted.md)|
|[size_is](size-is.md)|[source](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

##  <a name="vcconattributeprogrammmingfaqanchor3"></a> 可以在屬性區塊中使用註解嗎？

您可以使用屬性區塊中的單行和多行註解。 不過，您無法使用任一種存留的參數屬性以括弧括住的註解。

以下被允許的：

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

不允許下列：

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

##  <a name="vcconattributeprogrammmingfaqanchor4"></a> 屬性互動繼承的方式？

您可以從其他類別，可能會自行將歸類或不繼承屬性化和未歸屬類別。 從屬性化的類別衍生的結果是相同屬性提供者已轉換其程式碼後，從該類別衍生。 若要衍生的類別，透過 c + + 繼承時，就不會傳輸屬性。 屬性提供者只會將轉換附近有其屬性的程式碼。

##  <a name="vcconattributeprogrammmingfaqanchor5"></a> 如何使用屬性化 ATL 專案中？

您可能有.idl 檔案，非屬性化的 ATL 專案，您可能想要啟動 新增屬性化的物件。 在此案例中，使用**加入類別精靈**提供的程式碼。

##  <a name="vcconattributeprogrammmingfaqanchor6"></a> 如何使用屬性化專案中的.idl 檔案？

您可能想要使用屬性化 ATL 專案中的.idl 檔案。 在此案例中，您會使用[importidl](importidl.md)屬性的編譯.h 檔案的.idl 檔案 (請參閱[MIDL 屬性頁](../../ide/midl-property-pages.md)中的專案**屬性頁**對話方塊)，和然後在專案中包含的.h 檔案。

##  <a name="vcconattributeprogrammmingfaqanchor7"></a> 我是否可以修改屬性所插入的程式碼？

某些屬性會將程式碼插入您的專案。 您可以使用，以查看插入程式碼[/Fx](../../build/reference/fx-merge-injected-code.md)編譯器選項。 它也可插入的檔案複製程式碼，並將它貼到您的程式碼。 這可讓您修改屬性的行為。 不過，您可能要修改您的程式碼以及的其他部分。

下列範例會將插入的程式碼複製到原始程式碼檔案的結果：

```cpp
// attr_injected.cpp
// compile with: comsupp.lib
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(name="MyLibrary") ];

// ITestTest
[
   object, uuid("DADECE00-0FD2-46F1-BFD3-6A0579CA1BC4"), dual, helpstring("ITestTest Interface"), pointer_default(unique)
]

__interface ITestTest : IDispatch {
   [id(1), helpstring("method DoTest")]
   HRESULT DoTest([in] BSTR str);
};

// _ITestTestEvents
[
   uuid("12753B9F-DEF4-49b0-9D52-A79C371F2909"), dispinterface, helpstring("_ITestTestEvents Interface")
]

__interface _ITestTestEvents {
   [id(1), helpstring("method BeforeChange")] HRESULT BeforeChange([in] BSTR str, [in,out] VARIANT_BOOL* bCancel);
};

// CTestTest
[
   coclass, threading(apartment), vi_progid("TestATL1.TestTest"), progid("TestATL1.TestTest.1"), version(1.0), uuid("D9632007-14FA-4679-9E1C-28C9A949E784"), // this line would be commented out from original file
   // event_source("com"), // this line would be added to support injected code
   source(_ITestTestEvents), helpstring("TestTest Class")
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

##  <a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> 如何向前宣告屬性的介面？

如果您要讓屬性的介面之向前宣告，您必須套用相同的屬性，以向前宣告套用至實際的介面宣告。 您也必須套用[匯出](export.md)屬性設定為您的向前宣告。

##  <a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> 可以使用屬性衍生自的類別，也會使用屬性的類別上嗎？

否，不支援使用衍生自的類別，也會使用屬性的類別上的屬性。

## <a name="see-also"></a>另請參閱

[適用於 COM 與 .NET 的 C++ 屬性](cpp-attributes-com-net.md)
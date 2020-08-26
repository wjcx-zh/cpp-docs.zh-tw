---
title: 屬性程式設計常見問題集
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 70fbcc47884214fb998eb63ebfe50e445dbe95b8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843140"
---
# <a name="attribute-programming-faq"></a>屬性程式設計常見問題集

本主題將回答下列常見問題：

- [什麼是 HRESULT？](#vcconattributeprogrammmingfaqanchor1)

- [何時必須指定屬性的參數名稱？](#vcconattributeprogrammmingfaqanchor2)

- [我可以在屬性區塊中使用批註嗎？](#vcconattributeprogrammmingfaqanchor3)

- [屬性與繼承的互動方式為何？](#vcconattributeprogrammmingfaqanchor4)

- [如何使用非屬性化 ATL 專案中的屬性？](#vcconattributeprogrammmingfaqanchor5)

- [如何使用屬性化專案中的 .idl 檔案？](#vcconattributeprogrammmingfaqanchor6)

- [我可以修改由屬性插入的程式碼嗎？](#vcconattributeprogrammmingfaqanchor7)

- [如何轉送宣告屬性化介面？](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [我可以在衍生自類別的類別上使用屬性，而該類別也使用屬性嗎？](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a> 什麼是 HRESULT？

HRESULT 是簡單的資料類型，通常用來做為屬性和 ATL 的傳回值。 下表說明各種不同的值。 Winerror.h 標頭檔中包含更多的值。

|名稱|描述|值|
|----------|-----------------|-----------|
|S_OK|作業已順利完成|0x00000000|
|E_UNEXPECTED|未預期的失敗|0x8000FFFF|
|E_NOTIMPL|未實作|0x80004001|
|E_OUTOFMEMORY|無法配置所需的記憶體|0x8007000E|
|E_INVALIDARG|一或多個引數無效|0x80070057|
|E_NOINTERFACE|不支援這類介面|0x80004002|
|E_POINTER|指標無效|且顯示0x80004003|
|E_HANDLE|不正確控制碼|0x80070006|
|E_ABORT|作業已中止|0x80004004|
|E_FAIL|未指定的失敗|0x80004005|
|E_ACCESSDENIED|一般拒絕存取錯誤|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a> 何時必須指定屬性的參數名稱？

在大部分情況下，如果屬性具有單一參數，則該參數會命名為。 在您的程式碼中插入屬性時，不需要此名稱。 例如，下列 [匯總屬性的](aggregatable.md) 使用方式：

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

完全相同：

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

但是，下列屬性具有單一、未命名的參數：

:::row:::
   :::column span="":::
      [`call_as`](call-as.md)\
      [`case`](case-cpp.md)\
      [`cpp_quote`](cpp-quote.md)\
      [`default`](default-cpp.md)\
      [`defaultvalue`](defaultvalue.md)\
      [`defaultvtable`](defaultvtable.md)\
      [`emitidl`](emitidl.md)\
      [`entry`](entry.md)\
      [`first_is`](first-is.md)
   :::column-end:::
   :::column span="":::
      [`helpcontext`](helpcontext.md)\
      [`helpfile`](helpfile.md)\
      [`helpstring`](helpstring.md)\
      [`helpstringcontext`](helpstringcontext.md)\
      [`helpstringdll`](helpstringdll.md)\
      [`id`](id.md)\
      [`iid_is`](iid-is.md)\
      [`import`](import.md)
   :::column-end:::
   :::column span="":::
      [`importlib`](importlib.md)\
      [`include`](include-cpp.md)\
      [`includelib`](includelib-cpp.md)\
      [`last_is`](last-is.md)\
      [`length_is`](length-is.md)\
      [`max_is`](max-is.md)\
      [`no_injected_text`](no-injected-text.md)\
      [`pointer_default`](pointer-default.md)
   :::column-end:::
   :::column span="":::
      [`pragma`](pragma.md)\
      [`restricted`](restricted.md)\
      [`size_is`](size-is.md)\
      [`source`](source-cpp.md)\
      [`switch_is`](switch-is.md)\
      [`switch_type`](switch-type.md)\
      [`transmit_as`](transmit-as.md)\
      [`wire_marshal`](wire-marshal.md)
   :::column-end:::
:::row-end:::

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a> 我可以在屬性區塊中使用批註嗎？

您可以在屬性區塊中使用單行和多行批註。 不過，您無法在保留屬性參數的括弧內使用任一種類型的批註。

允許下列各項：

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

不允許的情況如下：

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a> 屬性與繼承的互動方式為何？

您可以從其他類別繼承屬性化和未歸屬類別，而這些類別本身可能會有屬性。 衍生自屬性化類別的結果與屬性提供者轉換其程式碼之後，衍生自該類別的結果相同。 屬性不會透過 c + + 繼承傳送至衍生的類別。 屬性提供者只會在其屬性的鄰近範圍中轉換程式碼。

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a> 如何使用非屬性化 ATL 專案中的屬性？

您可能會有一個非屬性化 ATL 專案，其具有 .idl 檔案，而且您可能會想要開始加入屬性化物件。 在此情況下，請使用 [ **加入類別] 嚮導** 來提供程式碼。

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a> 如何使用屬性化專案中的 .idl 檔案？

您可能會有想要在 ATL 屬性化專案中使用的 .idl 檔案。 在這種情況下，您會使用[importidl](importidl.md)屬性、將 .idl 檔編譯為 .h 檔 (在專案的 [**屬性頁**] 對話方塊中查看[MIDL 屬性頁](../../build/reference/midl-property-pages.md)) ，然後將 .h 檔案包含在您的專案中。

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a> 我可以修改由屬性插入的程式碼嗎？

某些屬性會將程式碼插入您的專案中。 您可以使用 [/fx](../../build/reference/fx-merge-injected-code.md) 編譯器選項來查看插入的程式碼。 您也可以從插入的檔案複製程式碼，並將它貼到您的原始程式碼中。 這可讓您修改屬性的行為。 不過，您可能也必須修改程式碼的其他部分。

下列範例是將插入程式碼複製到原始程式碼檔的結果：

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

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a> 如何轉送宣告屬性化介面？

如果您要對屬性化介面進行向前宣告，則必須將相同的屬性套用至您套用至實際介面宣告的正向宣告。 您也必須將 [export](export.md) 屬性套用至向前宣告。

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a> 我可以在衍生自類別的類別上使用屬性，而該類別也使用屬性嗎？

否，不支援在衍生自類別且也使用屬性的類別上使用屬性。

## <a name="see-also"></a>另請參閱

[適用於 COM 和 .NET 的 C++ 屬性](cpp-attributes-com-net.md)

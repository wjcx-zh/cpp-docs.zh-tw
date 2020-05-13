---
title: 屬性程式設計常見問題集
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributed programming
- attributes [C++/CLI], frequently asked questions
- FAQs (frequently asked questions), attributed programming [C++]
ms.assetid: a1b8349f-7f51-43c4-95ea-4edb6e5f243f
ms.openlocfilehash: 6c1762994d2cb109e86397bb0a5db1258cf33be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376068"
---
# <a name="attribute-programming-faq"></a>屬性程式設計常見問題集

本主題回答以下常見問題:

- [什麼是 HRESULT?](#vcconattributeprogrammmingfaqanchor1)

- [何時必須指定屬性的參數名稱?](#vcconattributeprogrammmingfaqanchor2)

- [我可以在屬性塊中使用註釋嗎?](#vcconattributeprogrammmingfaqanchor3)

- [屬性如何與繼承交互?](#vcconattributeprogrammmingfaqanchor4)

- [如何在非歸因 ATL 專案中使用屬性?](#vcconattributeprogrammmingfaqanchor5)

- [如何在屬性化專案中使用 .idl 檔?](#vcconattributeprogrammmingfaqanchor6)

- [我可以修改由屬性注入的代碼嗎?](#vcconattributeprogrammmingfaqanchor7)

- [如何轉發聲明屬性化介面?](#vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface)

- [是否可以對派生自同樣使用屬性的類的屬性使用屬性?](#vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor)

## <a name="what-is-an-hresult"></a><a name="vcconattributeprogrammmingfaqanchor1"></a>什麼是 HRESULT?

HRESULT 是一種簡單的資料類型,通常由屬性和 ATL 用作返回值。 下表描述了各種值。 頁眉檔 winerror.h 中包含更多值。

|名稱|描述|值|
|----------|-----------------|-----------|
|S_OK|作業已順利完成|0x00000000|
|E_UNEXPECTED|意外失敗|0x8000FFFF|
|E_NOTIMPL|未實作|0x80004001|
|E_OUTOFMEMORY|配置需要記憶體失敗|0x8007000E|
|E_INVALIDARG|一個或多個參數無效|0x80070057|
|E_NOINTERFACE|不支援此類介面|0x80004002|
|E_POINTER|無效指標|0x80004003|
|E_HANDLE|句柄無效|0x80070006|
|E_ABORT|操作已中止|0x80004004|
|E_FAIL|未指定失敗|0x80004005|
|E_ACCESSDENIED|一般存取被拒絕錯誤|0x80070005|

## <a name="when-do-i-have-to-specify-the-parameter-name-for-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor2"></a>何時必須指定屬性的參數名稱?

在大多數情況下,如果屬性具有單個參數,則命名該參數。 在代碼中插入該屬性時,不需要此名稱。 例如,[彙總屬性](aggregatable.md)的以下用法:

```cpp
[coclass, aggregatable(value=allowed)]
class CMyClass
{
// The class declaration
};
```

與以下情況完全相同:

```cpp
[coclass, aggregatable(allowed)]
class CMyClass
{
// The class declaration
};
```

但是,以下屬性具有單個未命名的參數:

||||
|-|-|-|
|[call_as](call-as.md)|[情況 下](case-cpp.md)|[cpp_quote](cpp-quote.md)|
|[default](default-cpp.md)|[預設值](defaultvalue.md)|[defaultvtable](defaultvtable.md)|
|[emitidl](emitidl.md)|[進入](entry.md)|[first_is](first-is.md)|
|[helpcontext](helpcontext.md)|[說明檔案](helpfile.md)|[helpstring](helpstring.md)|
|[helpstringcontext](helpstringcontext.md)|[helpstringdll](helpstringdll.md)|[id](id.md)|
|[iid_is](iid-is.md)|[進口](import.md)|[importlib](importlib.md)|
|[包括](include-cpp.md)|[包括利布](includelib-cpp.md)|[last_is](last-is.md)|
|[length_is](length-is.md)|[max_is](max-is.md)|[no_injected_text](no-injected-text.md)|
|[pointer_default](pointer-default.md)|[pragma](pragma.md)|[限制](restricted.md)|
|[size_is](size-is.md)|[源](source-cpp.md)|[switch_is](switch-is.md)|
|[switch_type](switch-type.md)|[transmit_as](transmit-as.md)|[wire_marshal](wire-marshal.md)|

## <a name="can-i-use-comments-in-an-attribute-block"></a><a name="vcconattributeprogrammmingfaqanchor3"></a>我可以在屬性塊中使用註釋嗎?

您可以在屬性塊中使用單行和多行註釋。 但是,不能在括弧內使用任一樣式的註釋,將參數保留到屬性。

允許以下操作:

```cpp
[ coclass, progid("MyClass.CMyClass.1"), /* Multiple-line
                                       comment */
   threading("both") // Single-line comment
]
```

不允許使用以下內容:

```cpp
[ coclass, progid("MyClass.CMyClass.1" /* Multiple-line comment */ ), threading("both" // Single-line comment)
]
```

## <a name="how-do-attributes-interact-with-inheritance"></a><a name="vcconattributeprogrammmingfaqanchor4"></a>屬性如何與繼承交互?

可以從其他類繼承屬性類和未歸因類,這些類本身可能歸因與否。 從屬性類派生的結果與屬性提供程式轉換其代碼後從該類派生的結果相同。 屬性不會通過C++繼承傳輸到派生類。 屬性提供程式僅在其屬性附近轉換代碼。

## <a name="how-can-i-use-attributes-in-a-nonattributed-atl-project"></a><a name="vcconattributeprogrammmingfaqanchor5"></a>如何在非歸因 ATL 專案中使用屬性?

您可能有一個非歸因 ATL 專案,該專案具有 .idl 檔,您可能需要開始添加屬性化物件。 在這種情況下,請使用**添加類嚮導**提供代碼。

## <a name="how-can-i-use-an-idl-file-in-an-attributed-project"></a><a name="vcconattributeprogrammmingfaqanchor6"></a>如何在屬性化專案中使用 .idl 檔?

您可能有一個要在 ATL 屬性化專案中使用的 .idl 檔。 在這種情況下,您將使用[importidl](importidl.md)屬性,將 .idl 檔編譯為 .h 檔(請參閱項目**屬性頁**對話框中的[MIDL 屬性頁](../../build/reference/midl-property-pages.md)),然後在專案中包括 .h 檔。

## <a name="can-i-modify-code-that-is-injected-by-an-attribute"></a><a name="vcconattributeprogrammmingfaqanchor7"></a>我可以修改由屬性注入的代碼嗎?

某些屬性將代碼注入到專案中。 您可以使用[/Fx](../../build/reference/fx-merge-injected-code.md)編譯器選項查看注入的代碼。 還可以從注入的檔案複製代碼並將其貼上到原始碼中。 這允許您修改屬性的行為。 但是,您可能還必須修改代碼的其他部分。

以下範例是將注入的代碼複製到原始碼檔案中的結果:

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

## <a name="how-can-i-forward-declare-an-attributed-interface"></a><a name="vcconattributeprogrammmingfaqhowcaniforwarddeclareanattributedinterface"></a>如何轉發聲明屬性化介面?

如果要對屬性化介面進行正向聲明,則必須對應用於實際介面聲明的正向聲明應用相同的屬性。 還必須將[匯出](export.md)屬性應用於前進聲明。

## <a name="can-i-use-attributes-on-a-class-derived-from-a-class-that-also-uses-attributes"></a><a name="vcconcaniuseattributesonclassderivedfromclassthatalsousesattributesanchor"></a>是否可以對派生自同樣使用屬性的類的屬性使用屬性?

否,不支援使用從同樣使用屬性的類派生的類的屬性。

## <a name="see-also"></a>另請參閱

[適用於 COM 和 .NET 的 C++ 屬性](cpp-attributes-com-net.md)

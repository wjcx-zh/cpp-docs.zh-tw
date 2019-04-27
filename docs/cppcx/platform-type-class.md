---
title: Platform::Type 類別
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: 456dbff652c8f1b800308ff757930b425616a83f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182999"
---
# <a name="platformtype-class"></a>Platform::Type 類別

包含與類型 (特別是此項)、字串名稱和 typecode 相關的執行階段資訊。 藉由呼叫取得[object:: gettype](../cppcx/platform-object-class.md#gettype)上的任何物件或使用[typeid](../extensions/typeid-cpp-component-extensions.md)運算子，在類別或結構的名稱。

## <a name="syntax"></a>語法

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>備註

在必須使用 `Type` 或 `if` 陳述式 (可根據物件的執行階段類型加以分支處理) 進行直接處理的應用程式中， `switch` 類別非常有用。 描述類型的類別型別程式碼會擷取藉由使用[type:: gettypecode](#gettypecode)成員函式。

## <a name="public-methods"></a>公用方法

|||
|-|-|
|[Type::GetTypeCode 方法](#gettypecode)|傳回物件的 [Platform::TypeCode 列舉](../cppcx/platform-typecode-enumeration.md) 值。|
|[Type::ToString 方法](#tostring)|傳回其中繼資料中所指定型別的名稱。|

## <a name="public-properties"></a>公用屬性

|||
|-|-|
|[Type::FullName](#fullname)|傳回表示類型之完整名稱的 [Platform::String 類別](../cppcx/platform-string-class.md)^，並使用 . （點） 做為分隔符號，不:: （雙冒號） — 比方說， `MyNamespace.MyClass`。|

## <a name="conversion-operators"></a>轉換運算子

|||
|-|-|
|[運算子 Type^](../cppcx/operator-type-hat.md)|可以從 `Windows::UI::Xaml::Interop::TypeName` 轉換為 `Platform::Type`。|
|[運算子 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|可以從 `Platform::Type` 轉換為 `Windows::UI::Xaml::Interop::TypeName`。|

### <a name="requirements"></a>需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="fullname"></a> Type::FullName 屬性

擷取目前的類型，在表單中的完整名稱`Namespace.Type`。

### <a name="syntax"></a>語法

```cpp
String^ FullName();
```

### <a name="return-value"></a>傳回值

型別的名稱。
### <a name="example"></a>範例

```

//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="gettypecode"></a> Type::GetTypeCode 方法

擷取內建類型數值類型類別目錄。

### <a name="syntax"></a>語法

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>傳回值

其中一個 Platform::TypeCode 列舉值。

### <a name="remarks"></a>備註

GetTypeCode () 成員方法相當於 `typeid` 屬性。

## <a name="tostring"></a> Type::ToString 方法

擷取型別的名稱。

### <a name="syntax"></a>語法

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>傳回值

它的中繼資料中所指定類型的名稱。

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)

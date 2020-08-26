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
ms.openlocfilehash: f94e1b37cf198f92d49efc793753892c1b138d69
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846559"
---
# <a name="platformtype-class"></a>Platform::Type 類別

包含與類型 (特別是此項)、字串名稱和 typecode 相關的執行階段資訊。 藉由對任何物件呼叫 [object：： GetType](../cppcx/platform-object-class.md#gettype) ，或針對類別或結構名稱使用 [typeid](../extensions/typeid-cpp-component-extensions.md) 運算子取得。

## <a name="syntax"></a>語法

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>備註

`Type`類別在必須使用 **`if`** 或 **`switch`** 語句（根據物件的執行時間類型進行分支）的應用程式中很有用。 使用 [type：： GetTypeCode](#gettypecode) 成員函式，可以抓取描述型別分類的型別程式碼。

## <a name="public-methods"></a>公用方法

| 名稱 | 描述 |
|--|--|
| [Type：： GetTypeCode 方法](#gettypecode) | 傳回物件的 [Platform::TypeCode 列舉](../cppcx/platform-typecode-enumeration.md) 值。 |
| [Type：： ToString 方法](#tostring) | 傳回其中繼資料中指定之類型的名稱。 |

## <a name="public-properties"></a>公用屬性

| 名稱 | 描述 |
|--|--|
| [Type：： FullName](#fullname) | 傳回表示類型之完整名稱的 [Platform::String 類別](../cppcx/platform-string-class.md)^，並使用 .  (點) 作為分隔符號，而不是：： (雙冒號) ，例如 `MyNamespace.MyClass` 。 |

## <a name="conversion-operators"></a>轉換運算子

| 名稱 | 描述 |
|--|--|
| [運算子類型 ^](../cppcx/operator-type-hat.md) | 可以從 `Windows::UI::Xaml::Interop::TypeName` 轉換為 `Platform::Type`。 |
| [運算子 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md) | 可以從 `Platform::Type` 轉換為 `Windows::UI::Xaml::Interop::TypeName`。 |

### <a name="requirements"></a>規格需求

**最低支援用戶端：** Windows 8

**最低支援伺服器：** Windows Server 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="typefullname-property"></a><a name="fullname"></a> Type：： FullName 屬性

以表單形式抓取目前類型的完整名稱 `Namespace.Type` 。

### <a name="syntax"></a>語法

```cpp
String^ FullName();
```

### <a name="return-value"></a>傳回值

型別的名稱。

### <a name="example"></a>範例

```cpp
//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="typegettypecode-method"></a><a name="gettypecode"></a> Type::GetTypeCode 方法

擷取內建類型數值類型類別目錄。

### <a name="syntax"></a>語法

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>傳回值

其中一個 Platform::TypeCode 列舉值。

### <a name="remarks"></a>備註

GetTypeCode ( # A1 成員方法的對等專案是 **`typeid`** 屬性。

## <a name="typetostring-method"></a><a name="tostring"></a> Type：： ToString 方法

捕獲型別的名稱。

### <a name="syntax"></a>語法

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>傳回值

在其中繼資料中指定之類型的名稱。

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)

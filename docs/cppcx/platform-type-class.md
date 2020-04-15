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
ms.openlocfilehash: 7463a2518e6ec5cc84f59db05cfaf60e43eb9fde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322086"
---
# <a name="platformtype-class"></a>Platform::Type 類別

包含與類型 (特別是此項)、字串名稱和 typecode 相關的執行階段資訊。 通過調用[Object::getType](../cppcx/platform-object-class.md#gettype)在任何物件上或使用類或結構名稱上的[typeid](../extensions/typeid-cpp-component-extensions.md)運算符獲得。

## <a name="syntax"></a>語法

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>備註

在必須使用 `Type` 或 `if` 陳述式 (可根據物件的執行階段類型加以分支處理) 進行直接處理的應用程式中， `switch` 類別非常有用。 使用[Type::GetTypeCode](#gettypecode)成員函數檢索描述類型類別的類型代碼。

## <a name="public-methods"></a>公用方法

|||
|-|-|
|[類型:取得類型代碼方法](#gettypecode)|傳回物件的 [Platform::TypeCode 列舉](../cppcx/platform-typecode-enumeration.md) 值。|
|[類型::到字串方法](#tostring)|返回其元數據中指定的類型的名稱。|

## <a name="public-properties"></a>公用屬性

|||
|-|-|
|[類型:全名](#fullname)|傳回表示類型之完整名稱的 [Platform::String 類別](../cppcx/platform-string-class.md)^，並使用 . (點)作為分隔符,而不是 :: (雙冒號)`MyNamespace.MyClass`* 例如 。|

## <a name="conversion-operators"></a>轉換運算子

|||
|-|-|
|[運算子型別*](../cppcx/operator-type-hat.md)|可以從 `Windows::UI::Xaml::Interop::TypeName` 轉換為 `Platform::Type`。|
|[運算子 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)|可以從 `Platform::Type` 轉換為 `Windows::UI::Xaml::Interop::TypeName`。|

### <a name="requirements"></a>需求

**受支援的最小用戶端:** 視窗 8

**受支援的伺服器最少:** 視窗伺服器 2012

**命名空間：** Platform

**中繼資料：** platform.winmd

## <a name="typefullname-property"></a><a name="fullname"></a>類型::全名屬性

檢索表單`Namespace.Type`中目前類型的完全限定名稱。

### <a name="syntax"></a>語法

```cpp
String^ FullName();
```

### <a name="return-value"></a>傳回值

類型的名稱。

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

GetTypeCode () 成員方法相當於 `typeid` 屬性。

## <a name="typetostring-method"></a><a name="tostring"></a>類型::到字串方法

檢索類型的名稱。

### <a name="syntax"></a>語法

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>傳回值

在其中繼資料中指定的類型的名稱。

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)

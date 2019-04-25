---
title: 運算子 Type^
ms.date: 12/30/2016
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
ms.openlocfilehash: 180efcac76b7f51291a47ee68508e7444a6c069c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161806"
---
# <a name="operator-type"></a>運算子 Type^

可以從 [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) 轉換為 `Platform::Type`。

## <a name="syntax"></a>語法

```cpp
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName);
```

### <a name="return-value"></a>傳回值

指定 `Platform::Type` Windows::UI::Xaml::Interop::TypeName [時，則傳回](/uwp/api/windows.ui.xaml.interop.typename)。

### <a name="remarks"></a>備註

`TypeName` 是用來表示類型資訊的非語言相關 Windows 執行階段結構。 [Platform::Type](../cppcx/platform-type-class.md) 則是 C++ 專屬，並且無法跨應用程式二進位介面 (ABI) 傳遞。 以下是 `TypeName`其中一種在 [Navigate](/uwp/api/windows.ui.xaml.controls.frame.navigate) 函式內的用法：

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>範例

下一個範例顯示如何在 `TypeName` 和 `Type`之間轉換。

```

// Convert from Type to TypeName
TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>.NET Framework 同等

.NET framework 程式會將`TypeName`為 <xref:System.Type>

### <a name="requirements"></a>需求

## <a name="see-also"></a>另請參閱

[運算子 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type 類別](../cppcx/platform-type-class.md)

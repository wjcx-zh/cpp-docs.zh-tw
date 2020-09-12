---
title: 將類型和成員設為已被取代 (C++/CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 6d61b00690cc087c3baced6d96d0b6c8d73b5850
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040323"
---
# <a name="deprecating-types-and-members-ccx"></a>將類型和成員設為已被取代 (C++/CX)

在 c + +/CX 中，支援使用已被取代的屬性 [取代](/uwp/api/windows.foundation.metadata.deprecatedattribute) 生產者和取用者的 Windows 執行階段類型和成員。 如果您使用的 API 已套用這個屬性，您會收到一個編譯時期警告訊息，表示 API 已被取代，此外建議替代的 API 以供使用。 在您的公用類型和方法，可以套用這個屬性並提供自訂訊息。

> [!CAUTION]
> 已被 [取代](/uwp/api/windows.foundation.metadata.deprecatedattribute) 的屬性只能搭配 Windows 執行階段類型使用。 如果是 Standard C++ 類別和成員，請使用 [__declspec(deprecated)](../cpp/deprecated-cpp.md)。

### <a name="example"></a>範例

下列範例示範如何 (例如在 Windows 執行階段元件中) 將您的公用 API 設為已被取代。 第二個參數，其類型為 [Windows:Foundation::Metadata::DeprecationType](/uwp/api/windows.foundation.metadata.deprecationtype) ，指定 API 正要被取代或移除。 目前只支援 DeprecationType::Deprecated 值。 屬性中的第三個參數指定要套用屬性的 [Windows::Foundation::Metadata::Platform](/uwp/api/windows.foundation.metadata.platformattribute) 。

```

namespace wfm = Windows::Foundation::Metadata;

public ref class Bicycle sealed
{

public:
    property double Speed;

    [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)]
    double ComputeAngularVelocity();
};
```

## <a name="supported-targets"></a>支援的目標

下表列出可套用 Deprecated 屬性的建構：

:::row:::
   :::column span="":::
      類別
      授權
      列舉
      列舉欄位 \
      事件類
      interface
   :::column-end:::
   :::column span="":::
      法
      參數化的函式 \
      屬性\
      結構
      結構欄位 \
      XAML 控制項
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>另請參閱

[型別系統](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空間參考](../cppcx/namespaces-reference-c-cx.md)

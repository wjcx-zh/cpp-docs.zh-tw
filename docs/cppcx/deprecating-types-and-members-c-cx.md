---
title: 即將過時的型別和成員 (C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b2f8ab1c52297a95c89f8ee00053d24baebe39d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205476"
---
# <a name="deprecating-types-and-members-ccx"></a>將類型和成員設為已被取代 (C++/CX)
在 C + + /CX 中，Windows 執行階段型別和成員的生產者和取用者使用[Deprecated](/uwp/api/windows.foundation.metadata.deprecatedattribute)支援屬性。 如果您使用的 API 已套用這個屬性，您會收到一個編譯時期警告訊息，表示 API 已被取代，此外建議替代的 API 以供使用。 在您的公用類型和方法，可以套用這個屬性並提供自訂訊息。  
  
> [!CAUTION]
>  [Deprecated](/uwp/api/windows.foundation.metadata.deprecatedattribute)是只能與 Windows 執行階段類型的屬性。 標準 c + + 類別和成員，請使用[__declspec （deprecated)](../cpp/deprecated-cpp.md)。  
  
### <a name="example"></a>範例  
 下列範例示範如何 (例如在 Windows 執行階段元件中) 將您的公用 API 設為已被取代。 第二個參數，型別[Windows: Foundation:: metadata:: deprecationtype](/uwp/api/windows.foundation.metadata.deprecationtype)指定 API 正要被取代或移除。 目前只支援 DeprecationType::Deprecated 值。 在屬性中的第三個參數會指定[Windows::Foundation::Metadata::Platform](/uwp/api/windows.foundation.metadata.platformattribute)來套用屬性。  
  
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
  
||  
|-|  
|XAML 控制項|  
|Delegate - 委派|  
|Event - 事件|  
|列舉欄位|  
|enum|  
|struct|  
|方法|  
|Class - 類別|  
|interface|  
|屬性|  
|結構欄位|  
|參數化建構函式|  
  
## <a name="see-also"></a>另請參閱  
 [型別系統](../cppcx/type-system-c-cx.md)   
 [Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)
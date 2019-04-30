---
title: Platform::Metadata::RuntimeClassName
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::RuntimeClassName
helpviewer_keywords:
- RuntimeClassName
- Platform::Metadata::RuntimeClassName
ms.assetid: fdef8f85-ab94-4edd-ba50-ee0da9358ff6
ms.openlocfilehash: d3de753c3a8897058333e02ce4294a0780d5b818
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387574"
---
# <a name="platformmetadataruntimeclassname"></a>Platform::Metadata::RuntimeClassName

套用至類別定義時，確保私用類別從 GetRuntimeClassName 函數傳回有效的名稱。

## <a name="syntax"></a>語法

```cpp
[Platform::Metadata::RuntimeClassName] name
```

#### <a name="parameters"></a>參數

*name*<br/>
Windows 執行階段中可見的現有公用類型名稱。

### <a name="remarks"></a>備註

使用這個屬性可在私用 ref 類別上指定自訂執行階段類型名稱，及 (或) 在現有名稱不符合需求時使用。 指定為類別實作的公用介面名稱。

### <a name="example"></a>範例

下列範例顯示如何使用這個屬性。 在這個範例中，HellowWorldImpl 的執行階段類型名稱為 Test::Native::MyComponent::IHelloWorld

```cpp
namespace Test
{
    namespace Native
    {
        namespace MyComponent
        {
            public interface class IHelloWorld
            {
                Platform::String^ SayHello();
            };

            private ref class HelloWorldImpl sealed :[Platform::Metadata::RuntimeClassName] IHelloWorld
            {
            public:
                HelloWorldImpl();
                virtual Platform::String^ SayHello();
            };

            Platform::String^ HelloWorldImpl::SayHello()
            {
                return L"Hello World!";
            }
        }
    }
}
```

## <a name="see-also"></a>另請參閱

[Platform::Metadata 命名空間](../cppcx/platform-metadata-namespace.md)

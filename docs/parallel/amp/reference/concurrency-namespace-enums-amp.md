---
title: Concurrency 命名空間列舉 (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: a4feb2f98fc288fa79c0f9d81e4ed882027eddf8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855719"
---
# <a name="concurrency-namespace-enums-amp"></a>Concurrency 命名空間列舉 (AMP)

|||
|-|-|
|[access_type 列舉](#access_type)|[queuing_mode 列舉](#queuing_mode)|

## <a name="access_type"></a>access_type 列舉

列舉類型，用來表示資料的各種存取類型。

```cpp
enum access_type;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`access_type_auto`|自動選擇快速鍵的最佳 `access_type`。|
|`access_type_none`|專用. 只有在加速器上才可存取配置，而不是在 CPU 上。|
|`access_type_read`|共用. 配置可在加速器上存取，並可在 CPU 上讀取。|
|`access_type_read_write`|共用. 配置可在加速器上存取，而且可以在 CPU 上寫入。|
|`access_type_write`|共用. 配置可在加速器上存取，而且可以在 CPU 上讀取和寫入。|

## <a name="queuing_mode"></a>queuing_mode 列舉

指定加速器支援的佇列模式。

```cpp
enum queuing_mode;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`queuing_mode_immediate`|佇列模式，指定任何命令（例如 parallel_for_each 函式[（C++ AMP））](concurrency-namespace-functions-amp.md#parallel_for_each)一旦傳回給呼叫端，就會傳送至對應的加速器裝置。|
|`queuing_mode_automatic`|佇列模式，指定命令會在對應至[accelerator_view](accelerator-view-class.md)物件的命令佇列上排入佇列。 呼叫[accelerator_view：： flush](accelerator-view-class.md#flush)時，會將命令傳送至裝置。|

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

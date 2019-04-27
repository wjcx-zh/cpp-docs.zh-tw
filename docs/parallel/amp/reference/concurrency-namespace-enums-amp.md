---
title: Concurrency 命名空間列舉 (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: adfc1743d887f2a670111eff31cf4653d2df1bee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180449"
---
# <a name="concurrency-namespace-enums-amp"></a>Concurrency 命名空間列舉 (AMP)

|||
|-|-|
|[access_type 列舉](#access_type)|[queuing_mode 列舉](#queuing_mode)|

##  <a name="access_type"></a>  access_type 列舉

用來表示資料的存取權的各種類型的列舉型別。

```
enum access_type;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`access_type_auto`|自動選擇最適合`access_type`加速器。|
|`access_type_none`|專用。 只有可存取在加速器上，而不是在 CPU 配置。|
|`access_type_read`|共用。 配置在加速器上存取，並在 CPU 上讀取。|
|`access_type_read_write`|共用。 配置在加速器上存取，並在 CPU 上為可寫入。|
|`access_type_write`|共用。 配置在加速器上存取，並可讀取且可寫入，而在 CPU 上。|

##  <a name="queuing_mode"></a>  queuing_mode 列舉

指定在加速器支援的佇列模式。

```
enum queuing_mode;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`queuing_mode_immediate`|佇列模式會指定任何命令，例如[parallel_for_each 函式 (C++ P)](concurrency-namespace-functions-amp.md#parallel_for_each)，因為它們會傳回給呼叫者傳送至對應的加速器裝置。|
|`queuing_mode_automatic`|指定命令會排入對應至命令佇列的佇列模式[accelerator_view](accelerator-view-class.md)物件。 命令傳送至裝置時[accelerator_view:: flush](accelerator-view-class.md#flush)呼叫。|

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

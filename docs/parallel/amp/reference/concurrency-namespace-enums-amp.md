---
title: Concurrency 命名空間列舉 (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
ms.openlocfilehash: 2467db27ad36dfcda31dfb5bb45067ada5470d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376324"
---
# <a name="concurrency-namespace-enums-amp"></a>Concurrency 命名空間列舉 (AMP)

|||
|-|-|
|[access_type 列舉](#access_type)|[queuing_mode枚舉](#queuing_mode)|

## <a name="access_type-enumeration"></a><a name="access_type"></a>access_type枚舉

用於表示對數據的各種類型的訪問的枚舉類型。

```cpp
enum access_type;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`access_type_auto`|自動選擇最適合`access_type`加速器的加速器。|
|`access_type_none`|專用。 分配只能在加速器上訪問,而不能在 CPU 上訪問。|
|`access_type_read`|共用。 分配在加速器上是可訪問的,並且在 CPU 上是可讀的。|
|`access_type_read_write`|共用。 分配可在加速器上訪問,可在 CPU 上寫入。|
|`access_type_write`|共用。 分配在加速器上是可存取的,在 CPU 上既可讀又可寫。|

## <a name="queuing_mode-enumeration"></a><a name="queuing_mode"></a>queuing_mode枚舉

指定加速器上支援的排隊模式。

```cpp
enum queuing_mode;
```

### <a name="values"></a>值

|名稱|描述|
|----------|-----------------|
|`queuing_mode_immediate`|一種排隊模式,用於指定任何命令(例如[,parallel_for_each函數 (C++ AMP))](concurrency-namespace-functions-amp.md#parallel_for_each)在返回調用方後立即發送到相應的加速器設備。|
|`queuing_mode_automatic`|一種排隊模式,用於指定在對應於[accelerator_view](accelerator-view-class.md)物件的命令佇列上排隊的命令。 當調用[accelerator_view:刷新](accelerator-view-class.md#flush)時,命令將發送到設備。|

## <a name="see-also"></a>另請參閱

[併發命名空間(C++ AMP)](concurrency-namespace-cpp-amp.md)

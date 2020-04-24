---
title: Platform::Collections 命名空間
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
ms.openlocfilehash: ab6b78f1b88c586a11276d36387fb42ea6ee667f
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032417"
---
# <a name="platformcollections-namespace"></a>Platform::Collections 命名空間

平臺::集合命名空間包含`Map``MapView`、`Vector``VectorView`和 類。 這些類別是 [Windows::Foundation::Collections](/uwp/api/windows.foundation.collections) 命名空間中定義的相對應介面的具象實作。 實體集合類型無法橫跨 ABI 移植 (例如，當 Javascript 或 C# 程式呼叫 C++ 元件時)，但是可以隱含地轉換成對應的介面類型。 例如，如果您實作公用方法來填入和傳回集合，請使用 [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) 在內部實作集合，並使用 [Windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1) 作為傳回類型。 有關詳細資訊,請參閱C++ 中的[「集合](../cppcx/collections-c-cx.md)」和[「創建 Windows 執行時元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)」。

您可以從 [std::vector](../standard-library/vector-class.md) 建構 Platform::Collections::Vector，也可以從 [std::map](../cppcx/platform-collections-map-class.md) 建構 [Platform::Collections::Map](../standard-library/map-class.md)。

此外,平臺:集合命名空間支援回插入和輸入反覆運算器以及`Vector`反覆運算`VectorView`器。

您必須包括`#include`( ) 集合.h 標頭才能在平臺::集合命名空間中使用類型。

## <a name="syntax"></a>語法

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>成員

這個命名空間包含下列成員。

|名稱|描述|
|----------|-----------------|
|[Platform::Collections::BackInsertIterator 類別](../cppcx/platform-collections-backinsertiterator-class.md)|代表將元素插入集合結尾的迭代器。|
|[Platform::Collections::InputIterator 類別](../cppcx/platform-collections-inputiterator-class.md)|代表將元素插入集合開頭的迭代器。|
|[Platform::Collections::Map 類別](../cppcx/platform-collections-map-class.md)|代表依索引鍵存取的可修改的機碼值組集合。 類似於 [std::map](../standard-library/map-class.md)。|
|[Platform::Collections::MapView 類別](../cppcx/platform-collections-mapview-class.md)|代表依索引鍵存取的唯讀機碼值組集合。|
|[Platform::Collections::Vector 類別](../cppcx/platform-collections-vector-class.md)|代表可修改的元素序列。 類似於 [std::vector](../standard-library/vector-class.md)。|
|[Platform::Collections::VectorIterator 類別](../cppcx/platform-collections-vectoriterator-class.md)|表示周遊 `Vector` 集合的迭代器。|
|[Platform::Collections::VectorView 類別](../cppcx/platform-collections-vectorview-class.md)|代表唯讀元素序列。|
|[Platform::Collections::VectorViewIterator 類別](../cppcx/platform-collections-vectorviewiterator-class.md)|表示周遊 `VectorView` 集合的迭代器。|

## <a name="inheritance-hierarchy"></a>繼承階層

[平台命名空間](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>需求

**中繼資料：** platform.winmd

**命名空間：** Platform::Collections

**編譯器選項：** /ZW

## <a name="see-also"></a>另請參閱

[平台命名空間](../cppcx/platform-namespace-c-cx.md)

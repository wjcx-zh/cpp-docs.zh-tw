---
title: Concurrency 命名空間常數 (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::HLSL_MAX_NUM_BUFFERS
- amp/Concurrency::MODULENAME_MAX_LENGTH
ms.assetid: 13a8e8cd-2eec-4e60-a91d-5d271072747b
ms.openlocfilehash: 512c0e30048584ae97a5da14fd5b3304f6888390
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841216"
---
# <a name="concurrency-namespace-constants-amp"></a>Concurrency 命名空間常數 (AMP)

[HLSL_MAX_NUM_BUFFERS](#hlsl_max_num_buffers)\
[MODULENAME_MAX_LENGTH](#modulename_max_length)

## <a name="hlsl_max_num_buffers-constant"></a><a name="hlsl_max_num_buffers"></a> HLSL_MAX_NUM_BUFFERS 常數

DirectX 允許的最大緩衝區數目。

```cpp
static const UINT HLSL_MAX_NUM_BUFFERS = 64 + 128;
```

## <a name="modulename_max_length-constant"></a><a name="modulename_max_length"></a> MODULENAME_MAX_LENGTH 常數

儲存模組名稱的最大長度。 在編譯器和執行時間上，此值必須相同。

```cpp
static const UINT MODULENAME_MAX_LENGTH = 1024;
```

## <a name="see-also"></a>另請參閱

[並行命名空間 (C++ AMP) ](concurrency-namespace-cpp-amp.md)

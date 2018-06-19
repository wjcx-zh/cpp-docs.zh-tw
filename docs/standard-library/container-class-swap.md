---
title: 容器類別::swap | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0ac2b3322f7f034c09c86f2307da2e3f3995c0d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842322"
---
# <a name="container-classswap"></a>容器類別::swap

> [!NOTE]
> 本主題位於 Visual C++ 文件內，可做為 C++ 標準程式庫中所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

會交換 **\*this** 和其引數之間受控制的序列。

## <a name="syntax"></a>語法

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>備註

若為 **\*this.get\_allocator ==** _right_**.get_allocator**，則會在固定的時間進行交換。 否則，它會執行多個元素指派，和與兩個受控制序列中元素數目成正比的建構函式呼叫。

## <a name="see-also"></a>另請參閱

[範例容器類別](../standard-library/sample-container-class.md)<br/>

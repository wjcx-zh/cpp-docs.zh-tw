---
title: 容器類別::reference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- reference method
ms.assetid: ab85a9fb-c628-4761-9a5f-a0231fad7690
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13883e1426be22c8cf3d329be33258c69511900d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966008"
---
# <a name="container-classreference"></a>容器類別::reference

> [!NOTE]
> 本主題位於 Visual C++ 文件內，可做為 C++ 標準程式庫中所用容器的無作用範例。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../standard-library/stl-containers.md)。

描述物件，其可作為受控制序列之元素的參考。

## <a name="syntax"></a>語法

```

typedef T2 reference;
```

## <a name="remarks"></a>備註

其描述為未指定類型的同義字`T2`(通常`Alloc::reference`)。 型別的物件`reference`型別的物件可以轉型[const_reference](../standard-library/container-class-const-reference.md)。

## <a name="see-also"></a>另請參閱

[範例容器類別](../standard-library/sample-container-class.md)<br/>

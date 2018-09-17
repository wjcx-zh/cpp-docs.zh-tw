---
title: 使用 NMAKE 巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0b68a5f3128b5d3780895f8080411819ed9b538
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712582"
---
# <a name="using-an-nmake-macro"></a>使用 NMAKE 巨集

若要使用巨集，請先加上貨幣符號 （$），如下所示的括號括住其名稱的物件。

## <a name="syntax"></a>語法

```
$(macroname)
```

## <a name="remarks"></a>備註

允許不含空格。 括號是選擇性如果*macroname*是單一字元。 定義字串取代 $(*macroname*); 未定義的巨集取代 null 字串。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

[巨集替換](../build/macro-substitution.md)

## <a name="see-also"></a>另請參閱

[巨集和 NMAKE](../build/macros-and-nmake.md)
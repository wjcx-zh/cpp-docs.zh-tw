---
title: 使用 NMAKE 巨集
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
ms.openlocfilehash: fb3b154ba8b30bbfc9a6c7c6b37720e5c60d6327
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317246"
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

[巨集替換](macro-substitution.md)

## <a name="see-also"></a>另請參閱

[巨集和 NMAKE](macros-and-nmake.md)

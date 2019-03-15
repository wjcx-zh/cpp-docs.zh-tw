---
title: 相依的搜尋路徑
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
ms.openlocfilehash: bc2c430c43f408065234c9df50977003eafd3cb1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824791"
---
# <a name="search-paths-for-dependents"></a>相依的搜尋路徑

每一個相依具有選擇性的搜尋路徑，指定方式如下：

## <a name="syntax"></a>語法

```
{directory[;directory...]}dependent
```

## <a name="remarks"></a>備註

NMAKE 中找尋相依的第一次在目前的目錄中，然後在目錄中指定的順序。 巨集可以指定部分或全部的搜尋路徑。 將目錄名稱括在大括號 （{}）;使用分號 （;） 分隔多個目錄。 不允許任何空格或定位字元。

## <a name="see-also"></a>另請參閱

[相依性](dependents.md)

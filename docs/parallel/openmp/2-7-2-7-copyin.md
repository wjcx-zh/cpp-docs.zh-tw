---
title: 2.7.2.7 copyin
ms.date: 11/04/2016
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
ms.openlocfilehash: 20db32530ee60967245497cdfb12a0fce103f7b7
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519525"
---
# <a name="2727-copyin"></a>2.7.2.7 copyin

**Copyin**子句提供一個機制來指派相同的值，以**threadprivate**小組執行平行的區域中的每個執行緒的變數。 每個變數中指定**copyin**複製子句，在小組的主要執行緒中變數的值，如同是由指派執行緒私用複本，在平行區域的開頭。 語法**copyin**子句如下所示：

```

copyin(
variable-list
)
```

若要限制**copyin**子句如下所示：

- 中指定的變數**copyin**子句必須具有可存取且明確的複製指派運算子。

- 中指定的變數**copyin**子句必須**threadprivate**變數。
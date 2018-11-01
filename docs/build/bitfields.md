---
title: 位元欄位
ms.date: 11/04/2016
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
ms.openlocfilehash: 3ff0092bbd31b8b1cd98fa56fb802c7ce28cb472
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652825"
---
# <a name="bitfields"></a>位元欄位

結構的位元欄位限制為 64 位元，而且可以是類型的帶正負號 int、 不帶正負號的 int、 int64、 或不帶正負號的 int64。 跨越界限類型的位元欄位會略過對齊的下一步 類型的對齊方式的位元欄位的位元。 例如，整數的位元欄位可能不會跨 32 位元界限。

## <a name="see-also"></a>另請參閱

[類型和儲存區](../build/types-and-storage.md)
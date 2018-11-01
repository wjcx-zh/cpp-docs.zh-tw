---
title: 連結器工具錯誤 LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: ce5332c2812740ef0b8c7d8e9c64a095d20a4e2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641451"
---
# <a name="linker-tools-error-lnk2017"></a>連結器工具錯誤 LNK2017

'symbol' 重新配置至 'segment' 沒有 /largeaddressaware: no 無效

您嘗試建置 32 位元位址的 64 位元映像。 若要這樣做，您必須：

- 使用固定的載入位址。

- 限制為 3 GB 的映像。

- 指定[/largeaddressaware: no](../../build/reference/largeaddressaware-handle-large-addresses.md)。
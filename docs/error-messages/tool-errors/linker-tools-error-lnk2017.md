---
title: 連結器工具錯誤 LNK2017 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2017
dev_langs:
- C++
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80af2bb6475fc37b7feba5b29bfe9c1292740286
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022446"
---
# <a name="linker-tools-error-lnk2017"></a>連結器工具錯誤 LNK2017

'symbol' 重新配置至 'segment' 沒有 /largeaddressaware: no 無效

您嘗試建置 32 位元位址的 64 位元映像。 若要這樣做，您必須：

- 使用固定的載入位址。

- 限制為 3 GB 的映像。

- 指定[/largeaddressaware: no](../../build/reference/largeaddressaware-handle-large-addresses.md)。
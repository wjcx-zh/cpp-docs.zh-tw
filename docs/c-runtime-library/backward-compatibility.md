---
title: 回溯相容性
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
ms.openlocfilehash: f672f0601a9d20a726f90963265d08ec212dedce
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744467"
---
# <a name="backward-compatibility"></a>回溯相容性

針對產品版本之間的相容性，程式庫 OLDNAMES.LIB 會將舊名稱對應到新名稱。 例如，`open` 會對應到 `_open`。 只有當您使用下列命令列選項組合來編譯時，才必須明確地與 OLDNAMES.LIB 連結：

- `/Zl` (省略來自物件檔案的預設程式庫名稱) 與 `/Ze` (預設值 — 使用 Microsoft 延伸模組)

- `/link` (連結器控制)、`/NOD` (無預設程式庫搜尋) 與 `/Ze`

如需編譯器命令列選項的詳細資訊，請參閱[編譯器參考](../build/reference/compiler-options.md)。

## <a name="see-also"></a>另請參閱

[相容性](../c-runtime-library/compatibility.md)

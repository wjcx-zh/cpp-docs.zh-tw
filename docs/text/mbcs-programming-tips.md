---
title: MBCS 程式設計提示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- programming [C++], MBCS
- character sets [C++], multibyte
- MBCS [C++], programming
- multibyte characters [C++]
ms.assetid: d8ad36b8-917f-474e-8adb-69462adecd17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a88fffbfc42dd6e7386ec43e55f2013f2548b6f5
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204466"
---
# <a name="mbcs-programming-tips"></a>MBCS 程式設計提示

在新的開發，您應該為終端使用者可能看到的所有字串使用 Unicode 字元編碼。 MBCS 是舊版的技術，已由 Unicode 取代。 本節為必須維護使用 MBCS 且不適合轉換為 Unicode 之現有程式的開發人員提供提示。 建議也適用於 MFC 應用程式和撰寫不以 MFC 應用程式。 主題包括：

- [一般 MBCS 程式設計的建議](../text/general-mbcs-programming-advice.md)

- [增量和遞減指標](../text/incrementing-and-decrementing-pointers.md)

- [位元組索引](../text/byte-indices.md)

- [字串中的最後一個字元](../text/last-character-in-a-string.md)

- [字元指派](../text/character-assignment.md)

- [字元比較](../text/character-comparison.md)

- [緩衝區溢位](../text/buffer-overflow.md)

## <a name="see-also"></a>另請參閱

[多位元組字元集 (MBCS) 的支援](../text/support-for-multibyte-character-sets-mbcss.md)
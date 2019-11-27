---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 17edea122afc03a8c3a2fdc86ee6c06c2ccf3c85
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398480"
---
# <a name="dosseg-32-bit-masm"></a>..DOSSEG （32-位 MASM）

根據 MS-DOS 區段慣例來排序區段： CODE first，然後是不在 DGROUP 中的區段，然後是 DGROUP 中的區段。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> **.DOSSEG**

## <a name="remarks"></a>備註

DGROUP 中的區段會遵循此順序：不在 BSS 或堆疊中的區段、BSS 區段，最後是堆疊區段。 主要用於確保 MASM 獨立程式中的 CodeView 支援。 與[.dosseg](../../assembler/masm/dosseg.md)相同。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)

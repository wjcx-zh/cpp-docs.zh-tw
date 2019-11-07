---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 8f0388c3df9804c0cdb105162a962a44fe207345
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703307"
---
# <a name="dosseg-32-bit-masm"></a>..DOSSEG （32-位 MASM）

根據 MS-DOS 區段慣例來排序區段： CODE first，然後是不在 DGROUP 中的區段，然後是 DGROUP 中的區段。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> .DOSSEG

## <a name="remarks"></a>備註

DGROUP 中的區段會遵循此順序：不在 BSS 或堆疊中的區段、BSS 區段，最後是堆疊區段。 主要用於確保 MASM 獨立程式中的 CodeView 支援。 與[.dosseg](../../assembler/masm/dosseg.md)相同。

## <a name="see-also"></a>請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>
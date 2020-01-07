---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: e27b0ae185542c11ee29119575d5c8225501f71e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313843"
---
# <a name="dosseg-32-bit-masm"></a>..DOSSEG （32-位 MASM）

根據 MS-DOS 區段慣例來排序區段： CODE first，然後是不在 DGROUP 中的區段，然後是 DGROUP 中的區段。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> **.DOSSEG**

## <a name="remarks"></a>備註

DGROUP 中的區段會遵循此順序：不在 BSS 或堆疊中的區段、BSS 區段，最後是堆疊區段。 主要用於確保 MASM 獨立程式中的 CodeView 支援。 與[.dosseg](dosseg.md)相同。

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)

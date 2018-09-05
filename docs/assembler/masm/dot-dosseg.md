---
title: .DOSSEG | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33ee0b0b049ece65786c4d4857c2e082a067fee4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693228"
---
# <a name="dosseg"></a>.DOSSEG

排序依據的 MS-DOS 區段慣例的區段： 程式碼第一次，然後區段不在 DGROUP，和在 DGROUP 然後區段。

## <a name="syntax"></a>語法

> .DOSSEG

## <a name="remarks"></a>備註

在 DGROUP 區段依照下列順序： 不在 BSS 或堆疊中的區段 BSS 區段，然後最後堆疊區段。 主要用於確保在 MASM 獨立程式中的 CodeView 支援。 與相同[DOSSEG](../../assembler/masm/dosseg.md)。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>
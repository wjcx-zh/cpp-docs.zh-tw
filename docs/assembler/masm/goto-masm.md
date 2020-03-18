---
title: GOTO (MASM)
ms.date: 12/16/2019
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 18f286d8634202b57dea788aa6984755a5afb197
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440803"
---
# <a name="goto"></a>GOTO

將元件傳輸到標記為 **：** _macrolabel_的行。

## <a name="syntax"></a>語法

> **GOTO** *macrolabel*

## <a name="remarks"></a>備註

只有在[宏](macro.md)、 [FOR](for-masm.md)、 [FORC](forc.md)、 [REPEAT](repeat.md)和[WHILE](while-masm.md)區塊中才允許**GOTO** 。 *Macrolabel*目標必須是行上的唯一指示詞，且前面必須加上前置冒號。

## <a name="see-also"></a>另請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)

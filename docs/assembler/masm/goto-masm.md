---
title: GOTO (MASM)
ms.date: 08/30/2018
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: a03cbda5a8ff64f6c167766f416e7744a5382ad5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654660"
---
# <a name="goto-masm"></a>GOTO (MASM)

將組件傳送至標記的一行 **:**_macrolabel_。

## <a name="syntax"></a>語法

> **GOTO** *macrolabel*

## <a name="remarks"></a>備註

**GOTO**允許只在[巨集](macro.md)， [FOR](for-masm.md)， [FORC](forc.md)，[重複](repeat.md)，和[時](while-masm.md)區塊。 *Macrolabel*目標必須是該行的唯一指示詞，而且必須加上前置的冒號。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>
